---
title: Linear Regression
author: Manohar
date: 2023-02-14 17:24:00 +0530
categories: [Tutorial, Machine learning]
tags: [Linear Regression]
#thumbnail: https://ik.imagekit.io/wrdkwox8l/thumbnails/self_learning_robot_realistic.png
img_path: /posts/Linear-Regression/
image:
  path: robot.png
#  lqip: data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAACWCAYAAABkW7XSAAANIElEQVR4Ae2dB1xUV9rH/2WlyvSzDQtNQ04tq2mrY2NNjQ0NCuE3WzLg5pQyWRZklmZZXHrEvYp0pQnKYl1ECWIkihKCkoJRrHMBFOMq6AyOFGiJLCUmaFJMq5AFMY4hFJoU5gTGORYEwjoQmSFJmBMrkAExjiEUmiDmBMY5FCE2KEpBCWIliRAooKSQmSFJmPZgDIoQmSFJMmQSiCmSFJmBMZOcmQlUOCE2KEpBCWIliRApEnL0J0gKGiJLCUmaFJK3CwyjMxMDDU3N1X3HB8fDyIjIwEBAVVVVUpKSlSU1NDBw0N9e7d+xufn5+vTpo0UPvzwQ3nzzzRdeXl6PDw8Dy83N7PZmYmKj49PcHExMTY2Njaenp6WlmZmYMCBYaGtr29/fHjx8fBxsbKzswMBA8PDw4ODgYGBhw8eVK1euVKdOnaVmZmZsbGzgwcP37/P39/HjBkzTJkzp49WqlWr7NixwcHBwMDA6tWrcnJyFBQUhISHJzc+PDhw8DAwMCuvPDKQnJxMUFJSkp6dHhYWFubm5hMmTChAmTZqI2Njcvr6+xsbGqampAQIC3t7e+ffu+++97t7e3q1avt7e3x8fGRkZJWVlTExMT+/bt09HRUXt7e5k2bRo9e/aU2bNm4dHRUUFBQYGhtbY3Nzds2bPx8fEhISGBgYCrK2txMTE0bdo0kpKShK1bt+u2228bOzubMmaMnToUDExMPz8/LCwsKcOXOGTTz5p+/fppMnTqhRo8a+fOnTp48QHx+Pz8/Pz8fHx8fEhIS2trbV69epff/0VGRkZycnIR7e3tr1apXW1tbysrK+Pn5+fj4+Pf39/c3NyEhoZiYmIYDAQBAWFhQcnJyQoKChg7dy7vv/8+ePXvGz8/PxQVFRXx8fKSkpOjz/+mPt2rWLr7/+mqamp6enq1apVKykpER0d7eHs7Ozppk6dKnt7e8+XLFy9XGxobr66qu3u7rZ

  alt: Credits:- Self Learned Machine Learning Robot (openai.com/dall-e-2)
mermaid: true
math: true
pin: false
---

## Linear Regression

---

To describe the supervised learning problem slightly more formally, our goal is, given a training set, to learn a function h : X → Y so that h(x) is a “good” predictor for the corresponding value of y. For historical reasons, this function h is called a `hypothesis`.

![Model Representation](Model_representation_kmUIa0Ffj.png){: w="395" h="340" style="border-radius:1%" .shadow}
*Figure 1 : Model Representation*

$$
h_{\theta }(X) = y
$$

> Linear regression with one variable - Univariate linear regression
> {: .prompt-info}

### Cost Function

We can measure the accuracy of our hypothesis function by using a **cost function**. This takes an average difference (actually a fancier version of an average) of all the results of the hypothesis with inputs from x's and the actual output y's.

$$
J\left(\theta_0, \theta_1\right)=\frac{1}{2 m} \sum_{i=1}^m\left(\hat{y}_i-y_i\right)^2=\frac{1}{2 m} \sum_{i=1}^m\left(h_\theta\left(x_i\right)-y_i\right)^2
$$

To break it apart, it is 21​ $\bar{x}$ where $\bar{x}$ is the mean of the squares of $h_\theta\left(x_i\right)-y_i$ , or the difference between the predicted value and the actual value.

This function is otherwise called the "Squared error function", or "Mean squared error". The mean is halved $\frac{1}{2}$ as a convenience for the computation of the gradient descent, as the derivative term of the square function will cancel out the $\frac{1}{2}$ term. The following image summarizes what the cost function does:

![Cost Function Representation](cost-function_kD48BJ4Zn.png){: w="495" h="440" style="border-radius:1%" .shadow}
*Figure 2 : Cost Function Representation*

### Cost Function - Intuition I

If we try to think of it in visual terms, our training data set is scattered on the x-y plane. We are trying to make a straight line (defined by $h_\theta\left(x\right)$ which passes through these scattered data points.

Our objective is to get the best possible line. The best possible line will be such so that the average squared vertical distances of the scattered points from the line will be the least. Ideally, the line should pass through all the points of our training data set. In such a case, the value of $J\left(\theta_0, \theta_1\right)$ will be 0. The following example shows the ideal situation where we have a cost function of 0.

![Cost Function Representation](cost-function_NXrsXSCml.png){: w="495" h="440" style="border-radius:1%" .shadow}
*Figure 3 : Cost Function Intuition 1*



When $\theta_1​=1$, we get a slope of 1 which goes through every single data point in our model. Conversely, when $\theta_1$​=0.5, we see the vertical distance from our fit to the data points increase.

![Cost Function Representation](cost-function_VXFBRi4h1.png){: w="495" h="440" style="border-radius:1%" .shadow}
*Figure 4 : Cost Function Intuition 1*

This increases our cost function to 0.58. Plotting several other points yields to the following graph:

![Cost Function Representation](cost-function_J91LeTj1m.png){: w="495" h="440" style="border-radius:1%" .shadow}
*Figure 5 : Cost Function Intuition 1*