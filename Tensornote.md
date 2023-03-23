# Tensor functions

In tensorflow: `axis = 0` means operate column,up and down;
`axis =1` means row, left to right


```python
import tensorflow as tf

# changing the data type into required one
tf.cast(tensor_name, dtype = datatype)

# Find the min or max value of tensor
tf.reduce_min(tensor_name)

tf.reduce_max(tensor_name)

# calculate the mean or sum value by announced axis
tf.reduce_mean(tensor_name, axis = 0 or 1)

tf.reduce_sum(tensor_name, axis = 0 or 1)

# mark the variables available for training
w = tf.Variable(tf.random.normal([2,2],mean = 0, stddev = 1))

# numerical calculate method(same dimension is required)
tf.add or tf.subtract or tf.multiply or tf.divide

# calculate the square, power and sqrt(square root)
tf.square or tf.pow or tf.sqrt

# matrix multiplication
tf.matmul(mat1,mat2)

# pair the features and label and form the dataset
data = tf.data.Dataset.form_tensor_tensor_slices((features,labels))

# calculate the gradient
with tf.GradientTape() as tape:
    variable = tf.Variable(tf.constant(3.0))
    function = ...
grad = tape.gradient(function_name,variable to derivative)
print(grad)

# traversing function, traverse every element
seq = ['one','two','three']
for i,element in enumerate(seq):
    print(i,element)
#Output:
#0    one
#1    two
#2    three

#独热码---used as label in classification problem
#this function transform data into one_hot data
tf.one_hot(origin_data, depth = classes)#param depth is number of classes

# this function makes variable fulfill requirement of possibility
# curve n output of n classes to interval [0,1]

tf.nn.softmax(x)

# assign_sub update value of param and return it
# using tf.Variable to make variable trainable before apply this function

w = tf.Variable(4)
w.assign_sub(1) # subtract 1 every time
# w becomes 3 after


# tf.argmax() return the index of maximum value(index start from 0)

tf.argmax(tensor_name, axis = 0 or 1)#0---column;1---row







```