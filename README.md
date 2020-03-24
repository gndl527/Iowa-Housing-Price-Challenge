# Creating Real Estate Pricing Model for Ames, Iowa

(Won 2nd Place Globally in Kaggle Competition)

### Problem Statement 

The Iowa Assessor's Office in Ames published a robust dataset that detailed out the sales record of real properties in the city of Ames from 2007 - 2010. Our goal is to build a regression model that leverages this dataset to establish a fair price for properties in Ames.

**Author**

[David Li](https://www.linkedin.com/in/davidgnli/)

This project was completed in cooperation with [General Assembly](https://generalassemb.ly) in October 2019.

---

### Project Files

Here is the workflow order to follow when running through the notebooks, which can be found in the [code folder](./code):

- [Project 2 Jupyter Notebook Code](./code/Project_2_Code.ipynb)
- [Project 2 Presentation](./slides/project_2.pdf)

---

### Executive Summary

Modeling is a simple representation of reality. I did not come up with this quote but it's nevertheless one of the more inspiring things I've heard since becoming a business strategist. The three key words here are: simplicity, representation and reality. 

I have always been an advocate for building simple and unbiased valuation or pricing models. While those two features don't always walk along holding hands, it is the data scientist's job to find the best balance between the two. On the one hand, complex models drive people away from the core and introduce unnecessary uncertainty into the model. On the other hand, a model too simple is subject to high bias and therefore cannot be a great representation of reality. Finding the balance between the two concepts is as much art as it is science.

The way I approached this data is creating accuracy using high-quality, independent and well-represented variables to paint a picture of a reasonable fair price of real estate prices in Ames, Iowa. 

I quickly started with the numerical variables after the initial data cleaning and EDA. We are very lucky to find 13 numerical variables highly correlated to the sales price. For the first version of our model, we took these variables without asking too many questions. Again, the goal here is to find high quality variables first so that we can think of ways to transform them later to better fit our model. After applying linear regression for the numerical variables taken out of the list, we got an OK model with a solid R^2 score.

The next step of the process is a deep dive into the categorical variables. While the quantity and completeness of these variables is nothing short of impressive, we cannot use all of them in our model. We need to pick and choose the best ones and start from there. I selected these variables based on 3 criteria:

1. **Independence**: It's very important that our variables don't overlap with each other. In other words, we only pick one variable to represent a specific characteristic of the house. For example, if we had chosen the variable 'Overall Kitchen Quality', we will leave variables such as 'Overall Kitchen Conditions' out of the list as those variables are highly correlated.
2. **Representative of Pricing Gap**: Another very important factor to think about is the distribution of sale prices. We want to see a great pricing gap for different categories within a specific variable so that the variable would have clear impact on the price of the property.
3. **Well-distributed Proportion of Counts**: We want balanced proportion of counts across different categories within a variable. Unbalanced counts will result in a variable adding more noise than value to our final product.

Finally, after collecting the variables, we conducted power transformation to our data followed with conducting a standard scale. This allows us to get our target and certain variables to resemble a normal distribution and therefore improve the accuracy of the model. We ran the target and variables against 3 regression models:

1. Linear Regression
2. Ridge Regression
3. Lasso Regression

---

### Conclusion and Next Steps

As a result of this exercise, we selected a Lasso Regression model that gave us the best score of around 23,000.

We need to note a number of constraints in our model as it is only useful to price real properties in a very specific range:

1. The model can be applied only to price houses in Ames, Iowa and not the broader Iowa, United States or other global markets.
2. The model can only be applied in a specific period in history, namely 2007-2010. This model is extremely unfit to predict prices in any other period other than the specified as it is subject to significant historical bias. This is especially the case considering the years 2007-2010 lays right in the middle of the financial crisis.
3. The model is intended to price the properties. It is not a useful way to value the properties. To evaluate the intrinsic value of the properties, we a forward-looking, free cash flow-based model that requires a completely different set of data and context.
