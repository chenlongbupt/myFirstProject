# myFirstProject
#通用组件
## DataTable
DataTable中设置了三个参数，src, link, widthSize.
```
src：表格数据的来源文件路径
link: 表格第一列内容所对应链接的地址
widthSize: 表格列宽，如果不设置默认为120，否则取设置值。
```
Example:
```
<DataTable src="/xxx.csv" link="http://www.baidu.com" widthSize="100">
```
xxx.csv:
```
合约,净盈亏,Sharpe
IC1807,6462.78,10.4
IF1807,12990.01,28.0
IH1807,5599.54,16.4
TT1809,736.79,7.4
Total,25789.12,27.1
```
Output:

合约 | 净盈亏 | Sharpe
:--| :--|:--
[IC1807](http://www.baidu.com) | 6462.78| 10.4
[IF1807](http://www.baidu.com) | 12990.01 | 28.0
[IH1807](http://www.baidu.com) | 5599.54 | 16.4
[TT1809](http://www.baidu.com) | 736.79 | 7.4
Total | 25789.12 | 27.1

## ImgViewer
Imgviewer中设置了两个参数：col, src.
```
col参数指定了一列放几个图片
src参数指定了图片的来源路径以及图片点击后访问的链接地址
```
Example：
```
<ImgViewer col={1} src={"huatai_apus_04.portfolio.trade.pnl.png"} />
```
Output:
![img](http://repo.flowam.com/report/apus/20180716/huatai_apus_04.portfolio.trade.pnl.png)

# 自定义页面
如果你仅仅想生成单个表格或者图片，你可以这样写
```
<DataTable src="xxx.xxx.csv" />
或者是
<ImgViewer src={"xxx.xxx.png"} />
```
但是如果你想要所有站点的相关表格，你也许可以更方便一些
```
<%#data%>
<DataTable src="<%&siteName%>.xxx.csv" />
<%/data%>
```
当然别忘了在开头加上data变量(数组)所在的数据文件路径,data中包含了siteName的数组
```
---
yourUrl.meta.json
---
```
而yourUrl.meta.json中可能是这样的：
```
{
    "data": [
    {"siteName": "haitong_apus_04"},
    {"siteName": "huatai_apus_04"}
    ]
}
```
最后的结果将会是这样的:
```
<DataTable src="haitong_apus_04.xxx.csv" />
<DataTable src="huatai_apus_04.xxx.csv" />
```
