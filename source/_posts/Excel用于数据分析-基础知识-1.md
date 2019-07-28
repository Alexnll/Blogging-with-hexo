---
title: Excel用于数据分析 - 基础知识(1)
date: 2019-07-28 23:33:15
tags:
    - Excel
    - data analysis 
---

### 摘要
本文总结了学习将Excel用于数据分析的大致路线，以及基础Excel学习中的一些细节内容。

<!-- more -->
### 正文
#### 1. Excel学习路线
在学习将Excel用于数据分析时，可遵循下列步骤进行<sup>[1]</sup>：
1. 熟悉Excel基础功能
2. 熟悉常用的Excel函数
3. 使用Excel进行绘图
4. 数据透视表的使用
5. VBA与宏的使用
6. Powerquery，PowerPivot，PowerBi等
7. 进一步深入学习与实际运用....

在学习时，可结合实际的数据集进行实际的数据处理与分析。本人在学习时，使用了美国房价<sup>[2]</sup>以及movielens电影评分<sup>[3]</sup>两个数据集。

#### 2.常用Excel函数的使用
1. IF: 逻辑判断，根据不同条件改变答案
   公式：=IF(条件表达式, 为真时，为假时)
   可通过IF嵌套，以判断复数条件：IF(logical 1, A, IF(logical 2, B, C))
&nbsp;

2. AND，OR：返回逻辑值
   =AND/OR(logical1, logical2 ...)，所有参数都为真时返回TRUE(AND/OR)，都为假时返回FALSE(AND/OR),除此之外返回真(OR)/假(AND)。
&nbsp;

3. COUNT/COUNTIF: 计数函数
   =COUNT(Range),统计某个单元格区域内的单元格总数
    =COUNTIF(Range, Criteria)，统计某个单元格区域中符合制定条件的单元格数目。多个条件时可使用COUNTIFS。
&nbsp;
4. SUM/SUMIF: 求和函数
   SUM用于对行和列求和：SUM(起始单元格：终止单元格)
   =SUM(Range)，对单元格区域进行求和
   =SUMIF(Range, Criteria, Sum_Range)，Range表示条件判断的区域，Criteria表示条件判断或表达式，Sum_Range表示求和的区域。同样，多个条件时可使用SUMIFS。
&nbsp;

5. LOOKUP/VLOOKUP：查找引用函数（5, 6, 7同）
    =VLOOKUP(lookup_value, table_array, col_index_num, range_lookup)，该函数的四个参数分别表示：需要查找的数值，查找的单元格区域，在单元格区域内待返回的匹配值的列的序号，是否为模糊匹配(TRUE或省略则为模糊匹配，FALSE则表示精确匹配，若找不到则返回错误值#N/A)。
    VLOOKUP函数可用于将不同的关联表格合并。注意，该函数只能查找到符合条件的第一个值。
    LOOKUP的使用待研究...
&nbsp;

6. FIND
    =FIND(find_text, within_text, start_num)，其参数分别表示要查找的文本，本文所在的单元格，从第几个字符开始查找。
    FIND经常可用于跟其他函数(特别是LEFT, RIGHT, MID等)进行嵌套。
&nbsp;

7. INDEX：用于返回表或区域中的值或是对值进行引用
    INDEX包括两种使用方式：
    - 数组形式：INDEX(array，row_num，column_num)
    - 引用形式：INDEX(reference，row_num，column_num，area_num)
    待研究。
&nbsp;

8. MATCH：用于在指定区域内按指定方式查询与制定内容所匹配的单元格**位置**，同LOOKUP系列所区分。
    =MATCH(lookup_value, lookuparray, match-type，其中lookup_value表示查询的制定内容，lookuparray表示查询的指定区域，match-type表示查询的制定方式，用-1,0，1表示。
    match-type如下：
    - 1或省略：查询小于或等于指定内容的最大值，且指定区域必须按升序排列；
    - 0：查询等于指定内容的第一个数值；
    - -1：查询大于或等于指定内容的最小值，且指定区域必须按降序排列。
&nbsp;

9. DATE：按年，月，日生成特定格式的日期
    =DATE(year, month, day)
&nbsp;

10.  DAYS：计算两个日期间相隔天数
    =DAYS(开始日期, 结束日期)，返回相隔天数
    可结合IF使用，如：
    =IF(DAYS(date1, date2)>number, "超时", "")
&nbsp;

11.  LEFT, RIGHT, MID, LEN, LENB等: 本文函数，用于修改文本，或者从文本框中提取文本，或是分离文本等
    LEFT, RIGHT, MID使用十分类似，以MID为例：
    =MID(text, start_num, num_chars)，从一个文本字符串开始，截取指定数目的字符
&nbsp;

12.  CONCATENATE
    =CONCATENATE(text1, text2 ...)，将多个字符文本或单元格中的数据连接在一起，显示在一个单元格中

#### 3.常用Excel图表的绘制<sup>[6]</sup>
###### 基础图表类型：
1. 柱状图：用于同类别对比
2. 折线图：表示趋势，最适合表示随时间的变化
3. 饼状图：表示各类别占整体的百分比
4. 雷达图：用于综合评估一个整体的不同方面
5. 散点图：不同因素对某一事物的影响，同时也可用于表示相关度，注意对点的形状进行变化可用于增加表现的维度
6. 其他，如瀑布图，树状图，数据地图等

注意适当地在图中进行数字地展示与强调。

###### 高维数据的可视化
待研究...

#### 4.Excel数据透视表的使用
###### 透视表是什么？
透视表是一种交互性的表，可以用来进行一系列的操作，如计算，求和，筛选，排序等。透视表的关键在于，其可以动态地改变版面布局，以及其中的数据种类，使得我们可以非常方便地对不同组的数据进行多个角度的分析，并更为方便的从不同维度以展示出我们想展示的数据集合。

###### 透视表的建立
- 插入 - 数据透视表，选择分析数据区域和透视表放置的位置后，点击确定即可创建

###### 透视表的基础使用
- 拖拽相应的特征（features）到筛选，列，行，值中
###### 数据快速分组
- 对透视表中单元格右键，选择组合

###### 相同标签进行快速合并
- 右键选择数据透视表选项，勾选合并且居中标签

###### 根据筛选一键批量创建工作表
- 分析 - 数据透视表 - 显示报表筛选项

###### 计算所占百分比
- 选择单元格右键 - 值显示方式 - 总计的百分比

###### 交互式图表的制作
利用数据透视表，可以便捷地制作出非常强大地交互效果。简单使用时，可通过插入 - 切片器，动态透视图等。

###### 总结
大部分透视表的使用都可用工作表单以及右键中的选项以及数据透视表字段完成。功能还有许多，正待进一步探究。

#### 5. Excel一些重要的基础功能
- 数据 - 筛选：对所选表启用筛选
- 数据 - 分列：按照分隔符号进行分列
- 右键 - 设置单元格格式：更改单元格内数据的格式，十分重要
- Excel链接做表的汇总：在汇总表的单元格内使用 =[表名.xlsx]sheet名!单元格名，以链接到不同的子表中的相应单元格
- ...

#### 6. Execl中的数据前处理
通过excel，我们还可以对数据集进行简单的前处理。更确定的，对数据集进行一定程度的数据清洗。数据清洗将在另一篇文章中进行详述。
&nbsp;
一般通过Excel进行数据分析，可分为一下几个步骤：
1. 明确分析目的，观察数据集
2. 利用Excel对数据进行简单清洗
   简单清洗的步骤可包括：
   1. 去重：数据 - 删除重复项/值
   2. 对0或空白值进行分析
   3. 去除表中不符合规范的区域
3. 数据集成，对来自不同数据源的数据进行整合，并导入到同一个excel表格中。注意在不同数据源中，相同的特征可能有着不同的名称。
4. 数据归约，即得到数据集的简化表示，其相比小得多，但能够产生几乎相同的分析结果
5. 数据变换，包括数据规范化，离散化和分层；
6. 建立数据透视表
7. 对数据进行分析

#### 7. 常用的Excel快捷键
- Ctrl + S: 快速保存文件 （时刻使用）
- Ctrl + Z: 撤销
- Ctrl + 上下左右： 快速定位表的上下左右边缘
- Ctrl + Home，End（若有）：快速定位至表的左上/右下
- Ctrl + shift + 上下左右：快速选择整行/整列
- Ctrl + H: 查找+等格式替换
- Ctrl + Enter：强制复制，或将公式填充到选定的所有单元格区域中
- F5：定位
- F4：重复
- F2：输入
- ...

---

### 附录
1. https://www.zhihu.com/question/21364170/answer/127980981 
2. https://www.kaggle.com/c/house-prices-advanced-regression-techniques
3. https://grouplens.org/datasets/movielens/
4. https://www.zhihu.com/question/24277854/answer/699971802?utm_source=ZHShareTargetIDMore&utm_medium=social&utm_oi=543064272872316928
5. https://www.zhihu.com/question/30239711
6. https://www.zhihu.com/question/28936003/answer/739525435?hb_wx_block=0&utm_source=ZHShareTargetIDMore&utm_medium=social&utm_oi=543064272872316928
7. https://zhuanlan.zhihu.com/p/25494049
8. https://www.zhihu.com/search?type=content&q=excel%20%E6%95%B0%E6%8D%AE%E5%89%8D%E5%A4%84%E7%90%86
9. Han J. Data Mining: Concepts and Techniques[M]. 2005.