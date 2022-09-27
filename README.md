<div align='center'>
<img src="https://github.com/MatheusReali/project003_open-DiamondPricePrediction/blob/main/images/diamonds.jpg?raw=true"  width="50%">
</div>

# DIAMOND PRICE PREDICTION

## Abstract

This project has the objective of using a Data Set of Diamond's features to build a Linear Regression Model to predict the price of another Data Set of diamonds.

## Introduction

### Technology

  - Python

### Index

  1. Importing Libraries;
  2. Understanding the Data;
  3. Data Cleaning;
  4. EDA;
  5. Building the Linear Regression Model;
  6. Predicting Prices.

## 1. Importing Libraries

Libraries used:
  - Pandas;
  - Numpy;
  - matplotlib;
  - seaborn;
  - sklearn;
  - statsmodels.

## 2. Understanding the Data

Each row of the DataFrame represents a diamond and the Columns are the attributes of these diamonds.

Description of the data:

| Column  | Description  |
|---|---|
| Price  | Price in US dollars (326-18,823)  |
| Carat  | Weight of the diamond (0.2--5.01)  |
| Cut  | Quality of the cut (Fair, Good, Very Good, Premium, Ideal)  |
| Color  | Diamond colour, from J (worst) to D (best)  |
| Clarity  | A measurement of how clear the diamond is (I1 (worst), SI2, SI1, VS2, VS1, VVS2, VVS1, IF (best))   |
| x  | Length in mm (0--10.74)  |
| y  | Width in mm (0--58.9)  |
| z  | Depth in mm (0--31.8)  |
| Depth  | Total depth percentage = z / mean(x, y) = 2 * z / (x + y) (43--79)  |
| Table  | Width of top of diamond relative to widest point (43--95)  |

### THE 4 "C"s OF A DIAMOND

<div align='center'>
<img src="https://github.com/MatheusReali/project003_open-DiamondPricePrediction/blob/main/images/4Cs.jpg"  width="50%">
</div>

<b>CUT:</b> The quality of the cut is measured by its Proportion, Symmetry and Final Polish. It represents how well a diamond refracts and reflects light.

<b>COLOR:</b> A diamond has many hues and this DataSet has only the High Quality types of colors. The scale goes from "D" (best) to "Z" (Worst), but diamonds with colors from "K" to "Z" are called tinted and are not represented in this DataSet.

<b>CLARITY:</b> Diamonds have characteristics known as inclusions (internal) and blemishes (external). Diamons without inclusions or blemishes are rare.

<b>CARAT:</b> Carat represents the weight of a diamond. 1 carat = 0.2 grams. It is expected that the heavier the diamond, the higher its price.

## 3. Data Cleaning

After importing the Data Set is important to analyse some of the statistics of the data

![image](https://user-images.githubusercontent.com/95454600/192419083-44dc0d21-0438-423b-b7d6-c07095b53d7b.png)

Using the method .describe() it is possible to see that the variables 'x', 'y' and 'z' have 'min' values as 0. This is not possible, since the diamond is a 3D object.

So let's take a look at this values

![image](https://user-images.githubusercontent.com/95454600/192419425-75fddb90-f8e4-411b-9572-9022af713bab.png)

Now we can calculate some of the variables using the formula presented on the table above. Then we will drop the rows that are missing more than 2 values.

Observing some plots, we can see outliers:

![image](https://user-images.githubusercontent.com/95454600/192421368-923a471c-074f-42e0-afe5-8a0d4927a56c.png)

Let' treat them using the previous formula

![image](https://user-images.githubusercontent.com/95454600/192420830-57fff302-9ed5-4cf9-9934-6da6de6211a1.png)

## 4. EDA

It is possible to see some relations between the 4 C's of the diamonds and the prices

![image](https://user-images.githubusercontent.com/95454600/192420992-f0676319-00f2-460a-90f6-38ab45262b95.png)
![image](https://user-images.githubusercontent.com/95454600/192421006-674e07bd-5c00-4553-b7ec-771cdfa84b25.png)
![image](https://user-images.githubusercontent.com/95454600/192421025-0003c563-7412-4fc2-a6c0-6bb17873c08e.png)

Let's plot a graph 'carat x price', then transform these variables to logarithmic scale and plot it again.

![image](https://user-images.githubusercontent.com/95454600/192422983-3dc50cf2-2faf-4a16-9c01-9d6b89829922.png)

To build the model, we have to transform the categorical data (color, clarity and cut) to numbers.

![image](https://user-images.githubusercontent.com/95454600/192423710-091fd281-861b-4113-be46-bf63246a7bd9.png)

## 5. Building the Linear Regression Model

We will use the Sklearn library to build the Linear Regression Model.

The log of the variables 'carat', 'clarity_1', 'cut_1', 'color_1', 'depth' and 'table' will be used to train the model.

![image](https://user-images.githubusercontent.com/95454600/192426266-50b8adaf-2b25-4eae-bc2c-491d15507b85.png)

### 6. Predicting Prices

After importing the Data Set that we want to predict the prices, we will transform the categorical data to numbers as above. Then we will use the model we trained to predict the prices of the new Data Set.

![image](https://user-images.githubusercontent.com/95454600/192426755-c148aafb-7a4d-4966-b9e9-bf2ae5435066.png)

With the DataFrame ready, we can export it to a csv file.

Finally we will use the website https://daft-oct2020-rick-diamonds.herokuapp.com to see our mean squared error.

![image](https://user-images.githubusercontent.com/95454600/192427403-ddd2f69f-eaf6-4d1b-8da2-b6e2283c2688.png)

## Conclusion

With this project we met our goal of predicting the prices of the diamonds with a mean squared error lesser than 900.

After several analyses, it was possible to observe that the data is quite clean, without outliers, because the more we remove data, the worse the model becomes.
It was also possible to see the importance of using the logarithmic scale for the variables, since it greatly reduces the mean squared error.

## Next steps

  As a future improvement, it is interesting to test more types of regressions to see which one better fits the problem.
  
## Links and References

  - How to evaluate diamonds: https://www.youtube.com/watch?v=YFlBxip7fjs&t=400s
  - Kaggle: https://www.kaggle.com/competitions/shai-ml/overview
  - mean squared error measurer: https://daft-oct2020-rick-diamonds.herokuapp.com

## Version

  1.0
  
## Author

Matheus Reali de Oliveira Fabricio (https://github.com/MatheusReali/MatheusReali)
