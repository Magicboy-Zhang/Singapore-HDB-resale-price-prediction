# 新加坡组屋转售价格预测
# Singapore-HDB-resale-price-prediction

这是一个叫做‘MH6805 金融机器学习’的南洋理工大学金融科技硕士专业的项目。
This is the project for a course named 'MH6805-MACHINE LEARNING IN FINANCE' from Fintech Master program of NTU.

### Introduction 介绍

  组屋是新加坡住房市场重要的组成部分，由政府提供，为新加坡人提供安全且负担得起的住房。预测新加坡祖屋转售的每平米价格有着现实意义，例如：帮助人们决定何时购买或者出售房子以获得最佳回报，或确保市场的社会公平性并使得低收入家庭也有机会购买合适的住房。
  接下来，我将简单的介绍本项目使用的数据集，机器学习模型以及一些比较和解释。细节见report。

  Housing Development Board (HDB) flats are a vital component of the housing market in Singapore, which provided by the government to offer safe and affordable housing options for Singaporen. Predicting the price per sqm of Singapore HDB has real-world significance, for instance, help people decide when to buy or sell a property for the best return, or ensuring social equity in the market and low-income families have chance to buy a suitable housing.
	Next, I will brifely describe the dataset used for this project, how we attempted to get a comprehensive understanding of the dataset, which machine learning models we used, and some comparison and interpretation of our models. Details are in the report above.

### 数据集 Dataset 

![image](https://github.com/Magicboy-Zhang/Singapore-HDB-resale-price-prediction/assets/74690677/039ef116-50fd-495a-a82c-6782ec3cad21)

1) ‘month’: the date of resold
2) ‘town’: the town where the resold housing is located
3) ‘flat_type’: the flat type of the resold housing
4) ‘block’: the block of the resold housing
5) ‘street_name’: the name of the street where the resold housing is located
6) ‘storey_range’: the range of storey of the resold housing
7) ‘floor_area_sqm’: the area of the resold housing
8) ‘flat_model’: the flat model of the resold housing
9) ‘lease_commence_Date’: Remaining lease term of the house (year)
10) ‘remaining_lease’: the remaining lease of the resold housing
11) ‘resale_price’: the resale price of the resold housing

20429 samples in total.

After processing, this dataset has 87 features in total.

### 建模 & 比较 Modeling & Comparison 

Validation set approach: 
| | MAE |	R^2 |
|---|---|---|
| Ordinary Linear regression | 506.496 | 0.757 |
| Linear Regression - Ridge |	509.611 |	0.754 |
| Linear Regression - Lasso |	509.632 |	0.754 |
| Decision Tree |	349.386 |	0.871 |
| Bagging |	280.463 |	0.921 |
| Random Forest |	280.729 |	0.921 |
| FNN(Mini Batch-SGD) |	381.757 |	0.842 |

Cross-Validation (5-fold):
|	| MAE |
|---|---|
| Linear Regression - Ridge |	508.593 |
| Linear Regression - Lasso |	508.623 |
| Decision Tree |	351.592 |
| Bagging |	288.216 |
| Random Forest |	284.332 |


### 一些解释 Interpretation

  房屋的纬度与房屋的剩余租期是两个非常重要的因素。一些房型和较低或较高的楼层以及所处的小镇同样都会对价格有很大的影响。

  ![image](https://github.com/Magicboy-Zhang/Singapore-HDB-resale-price-prediction/assets/74690677/8c77734d-0c2f-40b7-9e23-8e01746c7659)

  The latitude and the years of remaining lease of HDB are two very important factors. Some house types and lower or higher floors as well as the town in which it is located can also have a big impact on the price.

  众所周知，剩余租期越长，买家就应该支付更高的价格。但从这组数据来看，情况似乎并非如此。(图片由 Matlab 处理）

  ![image](https://github.com/Magicboy-Zhang/Singapore-HDB-resale-price-prediction/assets/74690677/a5e6846b-ef15-4b6e-a036-a75a2f38ad34)

  很明显，当剩余租期超过 80 到 90 之间的某个点时，散点图中密集区的位置不是上升而是下降。代码中的数字也显示了同样的结果： 非线性特征的 R 方（0.1925）大于线性的（0.1529）。经过调查，出现这种现象的原因是新加坡的政策规定剩余租约与购房者年龄之和不能超过某个整数。因此，当剩余租约增加到较高水平时，建屋局必须降价以确保有人愿意购买。

  As is known to us all, the longer remaining lease is, the higher price buyer should pay. But based on this data set, thing doesn't seem to be the case. (picture processed by Matlab)

  It is obvious that when the remaining lease exceeds a certain point between 80 and 90, the position of the dense area of the scatter plot does not rise but falls. Figures from code also show the same result: R-square of 2 degree polynomial (0.1925) is larger than linear model (0.1529). After investigation, the reason for this phenomenon is that Singapore’s policy stipulates that the sum of the remaining lease and the age of the purchaser cannot exceed a certain integer. Therefore, when remaining lease increasing to a high level, HDB must reduce its price to make sure someone is willing to buy it.
