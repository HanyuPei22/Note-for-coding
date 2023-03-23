# tf functions



#### tf.where()
```python
tf.where(if ... , A,B)# if ... is true, return A,else return B

tf.greater(A,B)# return the bigger entries of element

```

example:
```python
a = tf.constant([1,2,3,1,1])
b = tf.constant([0,1,3,4,5])

c = tf.where(tf.greater(a,b), a, b)
print(c)

#Output: tf.tensor([1 2 3 4 5], shape=(5,),dtype=int32 )
```
#### np.random.Randomstate.rand()

`np.random.Randomstate.rand(dimension)` return a random number in [0,1)

#### np.vstack()
`a,b = np.array`
`np.vstack((a,b))`将数组a，b沿垂直方向叠加







