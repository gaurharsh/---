𝗦𝘁𝗼𝗰𝗸-𝗽𝗿𝗲𝗱𝗶𝗰𝘁𝗶𝗼𝗻 


>  Python Library for Stock Market Prediction and Modelling."*
> 𝐃𝐞𝐯𝐞𝐥𝐨𝐩𝐞𝐝 𝐚 𝐬𝐭𝐨𝐜𝐤 𝐩𝐫𝐞𝐝𝐢𝐜𝐭𝐢𝐨𝐧 𝐦𝐨𝐝𝐞𝐥 𝐰𝐢𝐭𝐡 𝐨𝐯𝐞𝐫 𝟖𝟎% 𝐚𝐜𝐜𝐮𝐫𝐚𝐜𝐲 𝐮𝐬𝐢𝐧𝐠 𝐦𝐚𝐜𝐡𝐢𝐧𝐞 𝐥𝐞𝐚𝐫𝐧𝐢𝐧𝐠 𝐭𝐞𝐜𝐡𝐧𝐢𝐪𝐮𝐞𝐬 𝐚𝐧𝐝 𝐡𝐢𝐬𝐭𝐨𝐫𝐢𝐜𝐚𝐥 𝐬𝐭𝐨𝐜𝐤 𝐝𝐚𝐭𝐚.
• 𝐈𝐧𝐭𝐞𝐠𝐫𝐚𝐭𝐞𝐝 𝐭𝐡𝐞 𝐦𝐨𝐝𝐞𝐥 𝐢𝐧𝐭𝐨 𝐚𝐧 𝐞𝐱𝐢𝐬𝐭𝐢𝐧𝐠 𝐭𝐫𝐚𝐝𝐢𝐧𝐠 𝐩𝐥𝐚𝐭𝐟𝐨𝐫𝐦 𝐚𝐧𝐝 𝐢𝐦𝐩𝐥𝐞𝐦𝐞𝐧𝐭𝐞𝐝 𝐚 𝐦𝐨𝐧𝐢𝐭𝐨𝐫𝐢𝐧𝐠 𝐝𝐚𝐬𝐡𝐛𝐨𝐚𝐫𝐝 𝐭𝐨 𝐢𝐦𝐩𝐫𝐨𝐯𝐞 𝐩𝐞𝐫𝐟𝐨𝐫𝐦𝐚𝐧𝐜𝐞.
• 𝐂𝐨𝐥𝐥𝐚𝐛𝐨𝐫𝐚𝐭𝐞𝐝 𝐰𝐢𝐭𝐡 𝐜𝐫𝐨𝐬𝐬-𝐟𝐮𝐧𝐜𝐭𝐢𝐨𝐧𝐚𝐥 𝐭𝐞𝐚𝐦𝐬, 𝐜𝐨𝐧𝐭𝐫𝐢𝐛𝐮𝐭𝐞𝐝 𝐭𝐨 𝐫𝐞𝐬𝐞𝐚𝐫𝐜𝐡 𝐞𝐟𝐟𝐨𝐫𝐭𝐬, 𝐚𝐧𝐝 𝐦𝐞𝐧𝐭𝐨𝐫𝐞𝐝 𝐣𝐮𝐧𝐢𝐨𝐫 𝐝𝐞𝐯𝐞𝐥𝐨𝐩𝐞𝐫𝐬 𝐭𝐨 𝐞𝐧𝐬𝐮𝐫𝐞 𝐡𝐢𝐠𝐡-𝐪𝐮𝐚𝐥𝐢𝐭𝐲
𝐜𝐨𝐝𝐞 𝐚𝐧𝐝 𝐜𝐨𝐧𝐭𝐢𝐧𝐮𝐨𝐮𝐬 𝐮𝐩𝐝𝐚𝐭𝐞𝐬.


### Table of Contents
* [Installation](#installation)
* [Usage](#usage)
* [Dependencies](#dependencies)
* [License](#license)

### Installation
Clone the git repository:
```console

```

Install necessary dependencies
```console
$ pip install -r requirements.txt
```

Go ahead and install as follows:
```console
$ python setup.py install
```

You may have to install TensorFlow:
```console
$ pip install tensorflow     # CPU
$ pip install tensorflow-gpu # GPU - Requires CUDA, CuDNN
```

### Usage
#### 1. Prediction
##### a. Loading
Create a share object.
```python
>>> import bulbea as bb
>>> share = bb.Share('YAHOO', 'GOOGL')
>>> share.data
# Open        High         Low       Close      Volume  \
# Date                                                                     
# 2004-08-19   99.999999  104.059999   95.959998  100.339998  44659000.0   
# 2004-08-20  101.010005  109.079998  100.500002  108.310002  22834300.0   
# 2004-08-23  110.750003  113.479998  109.049999  109.399998  18256100.0   
# 2004-08-24  111.239999  111.599998  103.570003  104.870002  15247300.0   
# 2004-08-25  104.960000  108.000002  103.880003  106.000005   9188600.0
...
```
##### b. Preprocessing
Split your data set into training and testing sets.
```python
>>> from bulbea.learn.evaluation import split
>>> Xtrain, Xtest, ytrain, ytest = split(share, 'Close', normalize = True)
```

##### c. Modelling
```python
>>> import numpy as np
>>> Xtrain = np.reshape(Xtrain, (Xtrain.shape[0], Xtrain.shape[1], 1))
>>> Xtest  = np.reshape( Xtest, ( Xtest.shape[0],  Xtest.shape[1], 1))

>>> from bulbea.learn.models import RNN
>>> rnn = RNN([1, 100, 100, 1]) # number of neurons in each layer
>>> rnn.fit(Xtrain, ytrain)
# Epoch 1/10
# 1877/1877 [==============================] - 6s - loss: 0.0039
# Epoch 2/10
# 1877/1877 [==============================] - 6s - loss: 0.0019
...
```

##### d. Testing
```python
>>> from sklearn.metrics import mean_squared_error
>>> p = rnn.predict(Xtest)
>>> mean_squared_error(ytest, p)
0.00042927869370525931
>>> import matplotlib.pyplot as pplt
>>> pplt.plot(ytest)
>>> pplt.plot(p)
>>> pplt.show()
```


#### 2. Sentiment Analysis
Add your Twitter credentials to your environment variables.
```bash

```
And then,
```python
>>> bb.sentiment(share)
0.07580128205128206
```




### License
This code has been released under the [Apache 2.0 License](LICENSE).

