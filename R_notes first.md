- [1. R语言笔记](#1-r语言笔记)
  - [1.1. 基础知识内容](#11-基础知识内容)
    - [1.1.1. 变量命名规则](#111-变量命名规则)
    - [1.1.2. 变量赋值](#112-变量赋值)
    - [1.1.3. 变量查看](#113-变量查看)
    - [1.1.4. 变量的删除](#114-变量的删除)
    - [1.1.5. 向量](#115-向量)
    - [1.1.6. 向量中元素查询](#116-向量中元素查询)
    - [1.1.7. 向量运算](#117-向量运算)
    - [1.1.8. 平均数计算](#118-平均数计算)
    - [1.1.9. 方差计算](#119-方差计算)
      - [1.1.9.1. R语言](#1191-r语言)
      - [1.1.9.2. excel里](#1192-excel里)
    - [1.1.10. 标准差](#1110-标准差)
    - [1.1.11. 标准误（样本均值的标准误 Standard Error for the Sample Mean）](#1111-标准误样本均值的标准误-standard-error-for-the-sample-mean)
    - [1.1.12. 标准化（消除单位）](#1112-标准化消除单位)
    - [1.1.13. 数据中心化](#1113-数据中心化)
    - [1.1.14. 向量和直接数据的区分](#1114-向量和直接数据的区分)
    - [1.1.15. 向量的其他表达](#1115-向量的其他表达)
    - [1.1.16. 查找子集](#1116-查找子集)
    - [1.1.17. 屏蔽数据（删除数据）](#1117-屏蔽数据删除数据)
    - [1.1.18. 变量的灵活使用](#1118-变量的灵活使用)
  - [1.2. 常见指令/函数](#12-常见指令函数)
    - [1.2.1. 打开包的数据](#121-打开包的数据)
    - [1.2.2. 关联数据包或者解绑](#122-关联数据包或者解绑)
    - [1.2.3. 获取数据表头](#123-获取数据表头)
    - [1.2.4. 查看数据包的行列数](#124-查看数据包的行列数)
    - [1.2.5. 取出某一列的所有数据](#125-取出某一列的所有数据)
    - [1.2.6. 查看数据概况](#126-查看数据概况)
    - [1.2.7. 茎叶图绘制](#127-茎叶图绘制)
    - [1.2.8. 数据筛选实例](#128-数据筛选实例)
  - [1.3. 图像绘制](#13-图像绘制)
    - [1.3.1. 直方图](#131-直方图)
    - [1.3.2. 散点图](#132-散点图)
    - [1.3.3. 残差图](#133-残差图)
# 1. R语言笔记
## 1.1. 基础知识内容
### 1.1.1. 变量命名规则
变量开头必须是字母，不要使用空格或者-，尽量不要和函数名称重复 
### 1.1.2. 变量赋值
使用<- = `arrange(`)`都可以赋值，最好使用<-以展示是R语言
### 1.1.3. 变量查看
使用`objects()`查看已有的所有向量
### 1.1.4. 变量的删除
使用`rm()`或者`remove()`可以删除变量
### 1.1.5. 向量
用`c(元素)`给变量赋以向量，单个元素也叫标量
### 1.1.6. 向量中元素查询
直接使用向量名称加上中括号，中括号中输入数值，代表查询该向量中第几个元素。  

多个元素查询可以采取用向量访问向量，例如：`x[1:3]`查询1到3的元素;  
`x[c(1,2,1)]`查询输出第一个、第二个、第一个元素
直接输入向量名称可以获得所有元素
###  1.1.7. 向量运算
可以直接用标量对向量进行四则运算，如`2*x`，就是对x中所有元素乘以二

---
### 1.1.8. 平均数计算
`mean()`
### 1.1.9. 方差计算
#### 1.1.9.1. R语言
`var()`计算的是样本方差；  
样本方差和总体方差，总体方差是理想的也就是标准公式，样本方差则是考虑实际情况，所以总体方差计算分母是n，样本方差计算分母是n-1。
#### 1.1.9.2. excel里
`VAR.S`是样本方差,`VAR.P`是总体方差
### 1.1.10. 标准差
`sd()`
### 1.1.11. 标准误（样本均值的标准误 Standard Error for the Sample Mean）
不存在直接计算的公式，需要自己转化  

### 1.1.12. 标准化（消除单位）
`c_1<-(b-mean(b))/sd(b)`  
`scale(data, center=T,scale=T)  `  
每一个值减去平均值再除以标准差
### 1.1.13. 数据中心化 
`scale(data, center=T,scale=F)`
### 1.1.14. 向量和直接数据的区分
    a<-c(1,2,3)  
    mean(a) #[1]2  
    mean(1,2,3) #[1]1  
    mean(c(1,2,3)) #[1]2

计算平均数和方差时不能使用标量，必须是向量或者数据框等格式，使用标量会出现错误结果。 
### 1.1.15. 向量的其他表达
`a<-seq(1,20,by=0.1)` 1到20间隔0.1的向量 

---
### 1.1.16. 查找子集  
查找元素同理，可以使用新变量接受子集，也就是可以直接将查找出的子集分离出。
### 1.1.17. 屏蔽数据（删除数据）
使用查找子集的方式赋值时位置向量加符号  
>aa<-observations   
aa[-2]  

将observations赋值给变量aa，屏蔽第二个数据。此时第二个数据任然存在只是此时不显示，并不会改变aa里的数据，只是显示屏蔽。  
完成数据删除，将屏蔽语句赋予原变量即可。  
>aa<-aa[-2]  

删除元素，改变了aa变量
### 1.1.18. 变量的灵活使用
合理利用变量和向量c()对变量进行操作  
如：重复相同数据  
>cc<-c(cc,cc)   

cc是变量，c是向量的标志。将cc和cc拼接起来赋给cc，也就是cc重复了一遍元素。
###　运算选择
>aa<-observations[observations>4]   
  
从原向量(observations)中选出大于4的数据，原理是逻辑运算，所以要选出等于的数据需要使用==。  
通过[observations>4] 一一对比，等到一个长度和observations一样，元素只有True和False的向量，observations[]再一次读取逻辑向量，True输出，False不输出，达到效果。  
Tip:‘=’多为赋值，‘==’为逻辑判断

---
## 1.2. 常见指令/函数
### 1.2.1. 打开包的数据
`data()` 查看已经包的数据的打开情况  
`data("name")`打开具体的包的数据  
### 1.2.2. 关联数据包或者解绑  
`attach("name")`关联  
`detach("name")`解绑  
关联之后可以直接输出某一列名称得出数据
### 1.2.3. 获取数据表头
`names(name)` 显示表头  
### 1.2.4. 查看数据包的行列数  
`dim(name)` 结果是：行数 列数  
### 1.2.5. 取出某一列的所有数据  
数据包名称\$具体的某一行名称，此处的某一列名称可以通过names()得到。例如：'trees$Girth'，查看trees数据包里的Girth这一列所有数据。  
trees\$Girth可以看作向量，可以直接用作计算，例如，计算树的体积：  
>vol=trees\$Girth^2*trees\$Height/(4*pi) 
  
### 1.2.6. 查看数据概况
`summary(变量)` 展示各类数据的概要，不局限于最值、中位数、平均值等
### 1.2.7. 茎叶图绘制
`stem()`
### 1.2.8. 数据筛选实例  
>trees\$Volume[vol>2000]  

长度一样的向量进行判断，此处用体积大于2000的数据筛选volume,实际上volume里所有的数据都没有大于2000的。这是因为筛选使用的是***逻辑运算***
  
---
## 1.3. 图像绘制
### 1.3.1. 直方图  
`hist(x,col=)` 如果x只是一维向量，图形会是以频率为y轴，数据大小为x轴进行绘制。`col=‘’`是颜色参数，默认为0
### 1.3.2. 散点图
`plot(x,y)` 绘制x,y散点图，x和y一一对应绘制出的点
### 1.3.3. 残差图 
`residual(y~x)`  残差：估计值与真实值之差  

 `lm(y~x)`

---  
    