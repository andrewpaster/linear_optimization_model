# Linear Optimization Model for Daily Diet

This program uses the PuLP library to solve a linear optimization model for a daily diet. The model uses data containing the cost per serving and nutrients per serving of a variety of foods.

The code contains three different models. 
* **model 1** - basic model optimizing for cost and constrained 
by the maximum and minimum recommended nutrient intake
* **model 2** - same as model 1 but with extra constraints requiring minimum servings
of 1/10, allowing only broccoli or celery but not both, 
and at least 3 protein rich foods
* **model 3** - uses a larger data set, optimizes for low cholesterol,
 and has the same constraints
as model 1 plus the 1/10 serving size of model 2

#### Model 1

For model 1, the variables, objective, and constraints are the following:

##### variables

* x<sub>i</sub> - the number of servings of food i
* c<sub>i</sub> - the cost per serving of food i
* n<sub>ij</sub> - the nutrients per servings of food i, nutrient j

##### objective

* Minimize the cost = sum(c<sub>i</sub> * x<sub>i</sub>) for all i

##### constraints

* x<sub>i</sub> >= 0 for all i (servings must be zero or positive)
* minimum nutrients daily value <= sum(x<sub>i</sub> * n<sub>i</sub>)<= maximum nutrient daily value for all nutrients j

#### Model 2

For model 2, the variables, objective, and constraints are the following:

##### variables

* x<sub>i</sub> - the number of servings of food i
* c<sub>i</sub> - the cost per serving of food i
* n<sub>ij</sub> - the nutrients per servings of food i, nutrient j
* b<sub>i</sub> - binary variable if food i was chosen

##### objective

* Minimize the cost = sum(c<sub>i</sub> * x<sub>i</sub>) for all i

##### constraints

* x<sub>i</sub> >= 0 for all i (servings must be zero or positive)
* minimum nutrients daily value <= sum(x<sub>i</sub> * n<sub>i</sub>)<= maximum nutrient daily value for all nutrients j
* x<sub>i</sub> * b<sub>i</sub> >= 0.1 for all food i
* x<sub>i</sub> <= 100 * b<sub>i</sub> for all food i
* b<sub>broccoli</sub> + b<sub>celery</sub> <= 1
* b<sub>i</sub> for all food i considered high in protein (meat/chicken/fish/eggs)

#### Model 3

For model 3, the variables, objective, and constraints are the following:

##### variables

* x<sub>i</sub> - the number of servings of food i
* c<sub>i</sub> - the cholesterol per serving of food i
* n<sub>ij</sub> - the nutrients per servings of food i, nutrient j
* b<sub>i</sub> - binary variable if food i was chosen

##### objective

* Minimize the cholesterol = sum(c<sub>i</sub> * x<sub>i</sub>) for all i

##### constraints

* x<sub>i</sub> >= 0 for all i (servings must be zero or positive)
* minimum nutrients daily value <= sum(x<sub>i</sub> * n<sub>i</sub>)<= maximum nutrient daily value for all nutrients j
* x<sub>i</sub> * b<sub>i</sub> >= 0.1 for all food i
* x<sub>i</sub> <= 100 * b<sub>i</sub> for all food i

