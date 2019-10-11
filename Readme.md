# What is Machine Learning?
Arthur Samuel described it as: "the field of study that gives computers the ability to learn without being explicitly programmed." This is an older, informal definition.

Tom Mitchell provides a more modern definition: "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

Example: playing checkers.

E = the experience of playing many games of checkers

T = the task of playing checkers.

P = the probability that the program will win the next game.

In general, any machine learning problem can be assigned to one of two broad classifications: Supervised learning and Unsupervised learning.

# What is Supervised learning?

In supervised learning, we are given a data set and already know what our correct output should look like, having the idea that there is a relationship between the input and the output.

Supervised learning problems are categorized into "regression" and "classification" problems. In a regression problem, we are trying to predict results within a continuous output, meaning that we are trying to map input variables to some continuous function. In a classification problem, we are instead trying to predict results in a discrete output. In other words, we are trying to map input variables into discrete categories.

Example 1:

Given data about the size of houses on the real estate market, try to predict their price. Price as a function of size is a continuous output, so this is a regression problem.
We could turn this example into a classification problem by instead making our output about whether the house "sells for more or less than the asking price." Here we are classifying the houses based on price into two discrete categories.

Example 2:

(a) Regression - Given a picture of a person, we have to predict their age on the basis of the given picture

(b) Classification - Given a patient with a tumor, we have to predict whether the tumor is malignant or benign.

<img src="images/supervisedlearning.png" width="300" height="300" class="center">

# Unsupervised Learning

Unsupervised learning allows us to approach problems with little or no idea what our results should look like. We can derive structure from data where we don't necessarily know the effect of the variables.

We can derive this structure by clustering the data based on relationships among the variables in the data.

With unsupervised learning there is no feedback based on the prediction results.

Example:

Clustering: Take a collection of 1,000,000 different genes, and find a way to automatically group these genes into groups that are somehow similar or related by different variables, such as lifespan, location, roles, and so on.

Non-clustering: The "Cocktail Party Algorithm", allows you to find structure in a chaotic environment. (i.e. identifying individual voices and music from a mesh of sounds at a cocktail party).

<img src="images/unsupervisedlearning.png" width="300" height="300" class="center">

# Model Representation

To establish notation for future use, we’ll use <img src="/tex/839bd530124f302b99b3bf7c247a4bb6.svg?invert_in_darkmode&sanitize=true" align=middle width=52.985455049999985pt height=29.190975000000005pt/> to denote the “input” variables (living area in this example), also called input features, and <img src="/tex/f1ff827dd1819f91fd40229eac1ce7b7.svg?invert_in_darkmode&sanitize=true" align=middle width=51.493891349999984pt height=29.190975000000005pt/> to denote the “output” or target variable that we are trying to predict (price).

A pair <img src="/tex/9a9ed1968ddefaa8d6f1635e03f6c72b.svg?invert_in_darkmode&sanitize=true" align=middle width=69.62915025pt height=29.190975000000005pt/> is called a training example, and the dataset that we’ll be using to learn—a list of m training examples <img src="/tex/7725b3ed04e52ec88cb35b792c1cb11c.svg?invert_in_darkmode&sanitize=true" align=middle width=155.4786387pt height=29.190975000000005pt/>—is called a training set.

Note that the superscript “<img src="/tex/945cfdab316c27e0a9475969788be662.svg?invert_in_darkmode&sanitize=true" align=middle width=18.44865989999999pt height=24.65753399999998pt/>” in the notation is simply an index into the training set, and has nothing to do with exponentiation. We will also use X to denote the space of input values, and Y to denote the space of output values. In this example, <img src="/tex/1b20a5d9f7a35a8a4fd6a5063afe967f.svg?invert_in_darkmode&sanitize=true" align=middle width=67.37420909999999pt height=22.465723500000017pt/>.

To describe the supervised learning problem slightly more formally, our goal is, given a training set, to learn a function <img src="/tex/bba86056bdbd914e17b3a73cfac216cd.svg?invert_in_darkmode&sanitize=true" align=middle width=51.27458819999998pt height=22.831056599999986pt/> so that <img src="/tex/82b61730744eb40135709391ec01cbdb.svg?invert_in_darkmode&sanitize=true" align=middle width=31.651535849999988pt height=24.65753399999998pt/> is a “good” predictor for the corresponding value of <img src="/tex/deceeaf6940a8c7a5a02373728002b0f.svg?invert_in_darkmode&sanitize=true" align=middle width=8.649225749999989pt height=14.15524440000002pt/>. For historical reasons, this function <img src="/tex/2ad9d098b937e46f9f58968551adac57.svg?invert_in_darkmode&sanitize=true" align=middle width=9.47111549999999pt height=22.831056599999986pt/> is called a hypothesis. Seen pictorially, the process is therefore like this:

<img src="images/hypothesis.png" width="300" height="300" class="center">

When the target variable that we’re trying to predict is continuous, such as in our housing example, we call the learning problem a regression problem. When y can take on only a small number of discrete values (such as if, given the living area, we wanted to predict if a dwelling is a house or an apartment, say), we call it a classification problem.

# Cost Function

We can measure the accuracy of our hypothesis function by using a cost function. This takes an average difference (actually a fancier version of an average) of all the results of the hypothesis with inputs from x's and the actual output y's.

<img src="/tex/5124250c58027b14c7d2f110b5db9b9d.svg?invert_in_darkmode&sanitize=true" align=middle width=315.4630330499999pt height=41.14169729999998pt/>

To break it apart, it is <img src="/tex/d6b19f68aacb4461f4427e1489098827.svg?invert_in_darkmode&sanitize=true" align=middle width=17.920126949999997pt height=27.77565449999998pt/> where <img src="/tex/33717a96ef162d4ca3780ca7d161f7ad.svg?invert_in_darkmode&sanitize=true" align=middle width=9.39498779999999pt height=18.666631500000015pt/> is the mean of the squares of <img src="/tex/f0e008f4b5c3add6125c62fca6b420a1.svg?invert_in_darkmode&sanitize=true" align=middle width=73.30191659999998pt height=24.65753399999998pt/>, or the difference between the predicted value and the actual value.

This function is otherwise called the "Squared error function", or "Mean squared error". The mean is halved <img src="/tex/47d54de4e337a06266c0e1d22c9b417b.svg?invert_in_darkmode&sanitize=true" align=middle width=6.552545999999997pt height=27.77565449999998pt/> as a convenience for the computation of the gradient descent, as the derivative term of the square function will cancel out the <img src="/tex/47d54de4e337a06266c0e1d22c9b417b.svg?invert_in_darkmode&sanitize=true" align=middle width=6.552545999999997pt height=27.77565449999998pt/>.

The idea is to choose the <img src="/tex/17fde55b60bb334afb4a2b303a1ea335.svg?invert_in_darkmode&sanitize=true" align=middle width=36.66667454999999pt height=22.831056599999986pt/> so that <img src="/tex/b687e9cb7f5356da0e24f1b1cac73585.svg?invert_in_darkmode&sanitize=true" align=middle width=39.088702949999984pt height=24.65753399999998pt/> is close to <img src="/tex/deceeaf6940a8c7a5a02373728002b0f.svg?invert_in_darkmode&sanitize=true" align=middle width=8.649225749999989pt height=14.15524440000002pt/> for our training examples <img src="/tex/7392a8cd69b275fa1798ef94c839d2e0.svg?invert_in_darkmode&sanitize=true" align=middle width=38.135511149999985pt height=24.65753399999998pt/>

# Cost Function - Intuition I

If we try to think of it in visual terms, our training data set is scattered on the x-y plane. We are trying to make a straight line (defined by <img src="/tex/b687e9cb7f5356da0e24f1b1cac73585.svg?invert_in_darkmode&sanitize=true" align=middle width=39.088702949999984pt height=24.65753399999998pt/> which passes through these scattered data points.

Our objective is to get the best possible line. The best possible line will be such so that the average squared vertical distances of the scattered points from the line will be the least. Ideally, the line should pass through all the points of our training data set. In such a case, the value of <img src="/tex/dde9bb45048690d27e2b6c199faf1f5d.svg?invert_in_darkmode&sanitize=true" align=middle width=60.970370999999986pt height=24.65753399999998pt/> will be 0. The following example shows the ideal situation where we have a cost function of 0.

<img src="images/costfunction1.png" width="300" height="300" class="center">

When <img src="/tex/a9c6a444f1f65977995aeafe59acd891.svg?invert_in_darkmode&sanitize=true" align=middle width=45.22819289999998pt height=22.831056599999986pt/> , we get a slope of 1 which goes through every single data point in our model. Conversely, when <img src="/tex/2bcbe5c0630d86ce638154ddcb6dc655.svg?invert_in_darkmode&sanitize=true" align=middle width=58.013625449999985pt height=22.831056599999986pt/>, we see the vertical distance from our fit to the data points increase.

<img src="images/costfunction2.png" width="300" height="300" class="center">

This increases our cost function to 0.58. Plotting several other points yields to the following graph:

<img src="images/costfunction3.png" width="300" height="300" class="center">

Thus as a goal, we should try to minimize the cost function. In this case, <img src="/tex/a9c6a444f1f65977995aeafe59acd891.svg?invert_in_darkmode&sanitize=true" align=middle width=45.22819289999998pt height=22.831056599999986pt/> is our global minimum.

# Cost Function - Intuition II

A contour plot is a graph that contains many contour lines. A contour line of a two variable function has a constant value at all points of the same line. An example of such a graph is the one to the right below.

<img src="images/costfunction4.png" width="300" height="300" class="center">

Taking any color and going along the 'circle', one would expect to get the same value of the cost function. For example, the three green points found on the green line above have the same value for <img src="/tex/8fe4007120c3df67440d00ff258ffcda.svg?invert_in_darkmode&sanitize=true" align=middle width=60.970370999999986pt height=24.65753399999998pt/> and as a result, they are found along the same line. The circled <img src="/tex/332cc365a4987aacce0ead01b8bdcc0b.svg?invert_in_darkmode&sanitize=true" align=middle width=9.39498779999999pt height=14.15524440000002pt/> displays the value of the cost function for the graph on the left when <img src="/tex/5cd8e0abe46d1d38b0144343ff33af27.svg?invert_in_darkmode&sanitize=true" align=middle width=61.66661159999999pt height=22.831056599999986pt/> and <img src="/tex/e0cc6478e5b19281c2d782203319dd99.svg?invert_in_darkmode&sanitize=true" align=middle width=79.01826899999998pt height=22.831056599999986pt/>. Taking another <img src="/tex/82b61730744eb40135709391ec01cbdb.svg?invert_in_darkmode&sanitize=true" align=middle width=31.651535849999988pt height=24.65753399999998pt/> and plotting its contour plot, one gets the following graphs:

<img src="images/costfunction5.png" width="300" height="300" class="center">

When <img src="/tex/112e0823e05422da9985658c829beed2.svg?invert_in_darkmode&sanitize=true" align=middle width=61.66661159999999pt height=22.831056599999986pt/> and <img src="/tex/a85bf85e8a0643297472863cdc9c7506.svg?invert_in_darkmode&sanitize=true" align=middle width=45.22819289999998pt height=22.831056599999986pt/>, the value of <img src="/tex/8fe4007120c3df67440d00ff258ffcda.svg?invert_in_darkmode&sanitize=true" align=middle width=60.970370999999986pt height=24.65753399999998pt/> in the contour plot gets closer to the center thus reducing the cost function error. Now giving our hypothesis function a slightly positive slope results in a better fit of the data.

<img src="images/costfunction6.png" width="300" height="300" class="center">

The graph above minimizes the cost function as much as possible and consequently, the result of <img src="/tex/edcbf8dd6dd9743cceeee21183bbc3b6.svg?invert_in_darkmode&sanitize=true" align=middle width=14.269439249999989pt height=22.831056599999986pt/> and <img src="/tex/1a3151e36f9f52b61f5bf76c08bdae2b.svg?invert_in_darkmode&sanitize=true" align=middle width=14.269439249999989pt height=22.831056599999986pt/> tend to be around 0.12 and 250 respectively. Plotting those values on our graph to the right seems to put our point in the center of the inner most 'circle'.