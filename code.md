## Dummy variables
```python

import patsy
X=patsy.dmatrix('column',data=df,return_type='dataframe')
cars2=cars.join(X)

```
## Preprocessing
```python
# first we normalize our features ..
from sklearn import preprocessing
cars_trans=preprocessing.normalize(cars,axis=0)

# turn back in DF
cars_trans=pd.DataFrame(cars_trans,columns=cars.columns)

```

## Generating fake random data

```python
# We start by seeding the random number generator so that everyone will have the same "random" results
np.random.seed(9)

# Function that returns the sin(2*pi*x)
def f(x):
    return np.sin(2 * np.pi * x)

# generate points used to plot
# This returns 100 evenly spaced numbers from 0 to 1
x_plot = np.linspace(0, 1, 100)

# generate points and keep a subset of them
n_samples = 100
# Generate the x values from the random uniform distribution between 0 and 1
X = np.random.uniform(0, 1, size=n_samples)[:, np.newaxis]
# Generate the y values by taking the sin and adding a random Gaussian (normal) noise term
y = f(X) + np.random.normal(scale=0.3, size=n_samples)[:, np.newaxis]
```

## Polynomial Model
```python
fig,ax = plt.subplots(1,1)
degree = 2
# Generate the model type with make_pipeline
# This tells it the first step is to generate 3rd degree polynomial features in the input features and then run
# a linear regression on the resulting features
est = make_pipeline(PolynomialFeatures(degree), LinearRegression())
# Fit our model to the training data
est.fit(X, y)
# Plot the results
plot_approximation(est, ax, label='degree=%d' % degree)
```

## Train Test Split
```python
X_train, X_test, y_train, y_test = train_test_split(df_X, df['log_dtg'], test_size=0.25)
```

# Pickling
- What is it?
  - Serialize and deserialize
  - Turn objects to byte stream
  - You can just dump the pickle in a file
```python
# Save a dictionary into a pickle file.
import pickle

favorite_color = { "lion": "yellow", "kitty": "red" }

pickle.dump( favorite_color, open( "save.p", "wb" ) )

# import it back
favorite_color = pickle.load( open( "save.p", "rb" ) )
favorite_color is now { "lion": "yellow", "kitty": "red" }


```


  # Deep Copy
  ```python
  a = b[:] # copies contents of b to a
  # problem: this is not a deep copy
  # solution: import deep copy
  a = [1, 2, [3, 4]]
  # a[3] copied is a reference
  from copy import deepcopy
  b = deepcopy(a)
  ```

# Pandas
- You can't see the intermediate state for Groupby
- Pandas groupby will operate on columns that have meaning.
- Max will keep all of the values, sum will only keep the values you groupby with. Diff will keep everything
- Pandas has a concept of index, multilayered index allows you to manipulate columns and assign it to a new column

## Merge
- You can merge 2 dataframes by providing which column you want to merge it on
- The result can be from 0 - len(df1) * len(df2)
- Result will always be a dataframe
- If you want to merge, but you don't want to lose data, you use how='left'

## Scatter 2 categories
plt.figure(figsize=(10, 8), dpi=80)
plt.scatter(set1[0],set1[1], c='b')
plt.scatter(set2[0],set2[1], c='r',alpha =.8)
plt.xlabel('sepal length')
plt.ylabel('sepal width')
plt.show()

## sql
```sql
CREATE TABLE IF NOT EXISTS AllstarFull (
    playerID varchar(20) NOT NULL,
    yearID int NOT NULL,
    gameNum varchar(20) NOT NULL,
    gameID varchar(12) DEFAULT NULL,
    teamID text DEFAULT NULL,
    lgID text DEFAULT NULL,
    GP varchar(20) DEFAULT NULL,
    startingPos varchar(20) DEFAULT NULL,
    PRIMARY KEY (playerID,yearID,gameNum)
);

COPY AllstarFull FROM '/home/username/baseballdata/AllstarFull.csv' DELIMITER ',' CSV HEADER;

```

## Decorators
```python
def talky(func):
  def wrapped(*args, **kwargs):
    output = func(*args, **kwargs)
    print("Oh hi!")
    print("The result sure is {}!".format(output))
  return wrapped

@talky
def square(x):
  return x * x

def talky_with(name):
  def wrap(f):
    def wrapped_f(*args, **kwargs):
      print ("Oh hi {}!".format(name))
      output = f(*args, **kwargs)
      print ("The result sure is {}!".format(output))
    return wrapped_f
  return wrap

@talky_with("Aaron")
def square(x):
  return x * x
```

## Selenium
```python
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time

import os
chromedriver = "/Applications/chromedriver"
os.environ["webdriver.chrome.driver"] = chromedriver


driver = webdriver.Chrome(chromedriver)
driver.get(link)
driver.find_element_by_xpath("//*[@data-modal-class='modal_project_by']").click()
```

## Matching with names

```python
m = re.match(r"(?P<int>\d+)\.(\d*)", '3.14')
```
