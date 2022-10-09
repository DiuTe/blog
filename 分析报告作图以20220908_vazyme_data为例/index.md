# 分析报告作图（以20220908_Vazyme_data为例）

# 分析报告作图（以20220908_Vazyme_data为例）

##背景介绍

- 针对不同样本类型（gDNA、ctDNA），采用一套建库试剂盒（ND627）， 设计方案使其同时满足 gDNA、ctDNA 的文库构建，并在性能上与 KK8514、 KK8504 一致或更优。ND627分别与不同的扩增模块在不同的打断时间下分组实验，每组实验重复三次。gDNA为ND627分别与（N616,N618）在打断时间为（37℃ 12min,65℃ 30min）的条件下建库与KK8514作为比较共三组。CtDNA为ND627分别于（N616，N618）在打断时间为（20℃ 15min，65℃ 15min/65℃ 30 min）的条件下建库与KK8504作为比较共五组。
- ctdna中有8个参考突变位点，gdna中有13个参考突变位点

##分析思路

#barplot
1. 首先分别在ctdna和gdna样本中匹配其对应的参考突变位点，并对相应的在不同条件下的分组实验添加type列用于区分组别。(见ctDNA/gdna_match_result.txt)
2. 在R中导入上述数据文件，运行 plot_code.R中对应代码即可按照突变位点的不同将不同组别的不同样本中匹配到的突变位点的 AF值以柱状图的形式展示

#heatmap

1.除了展示突变位点在不同样本中的 AF值，还需要按照组别以求平均值的方式绘制热图，展示不同突变位点在不同组别中的差异
2.在 barplot的 ctDNA/gdna_match_result.txt文件的基础上将文件处理为矩阵格式（见ctDNA/gdna_match_result_avg1.txt）
3.导入上述矩阵文件，运行plot_code.R中对应代码即可

##参数

- geom_bar()柱状图柱体分布参数
- scale_fill_manual()柱状图分组颜色参数
- theme()坐标字体参数
- x/ylim横纵坐标显示数值范围参数
- geom_text()柱状图数值等具体信息调整参数
- geom_hline()参考线绘制参数

