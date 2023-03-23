# Example for Iris dataset

## load dataset

```python
from sklearn import datasets
from pandas import DataFrame
import pandas as pd

x_data = datasets.load_iris().data
y_data = datasets.load_iris().target

x_data = DataFrame(x_data, columns = ['length','width','f_length','l_width']) 
pd.set_option('display.unicode.east_asian_width',True)  #列名对齐

x_data['classes'] = y_data # add a column 'classes', data is y_data

```

## classification by neural network

```python
np.random.seed(116) # make random result stays the same
np.random.shuffle(x_data)
np.random.seed(116)
np.random.shuffle(y_data)
tf.random.set_seed(116)


# put a batch of data[features,label] every time to nn
train_db = tf.data.Dataset.from_tensor_slices((x_train,y_train)).batch(32) 

test_db = tf.data.Dataset.from_tensor_slices((x_test,y_test)).batch(32) 


# Define all trainable parameter in nn
# There are 3 outputs 4 inputs therefore[4,3]
w1 = tf.Variable(tf.random.truncated_normal([4,3], stddev = 0.1, seed=1)) 

# must remain same with the [.,3](bias term in each node)
b1 = tf.Variable(tf.random.truncated_normal([3], stddev = 0.1, seed=1)) 

# use for to iterate, 'with' structure update the param, display the loss
for epoch in range(epoch)


```