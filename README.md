# AI-and-DS
Artificial intelegence and data science projects.
## TOC
* kNN, decision tree, SVM - classification tasks (lesson 2)
* linear and polynomial regression - regression tasks (lesson 3)
* k-means, hierarchical clustering - clustering tasks (lesson 4)
* customer segmentation, DBSCAN - clustering tasks (lessons 4-5)
* recommendation systems (lesson 7)
* association rules (lesson 7)
* anomaly detection (lesson 8)
* basics of neural network (lesson 9)
* convolutional neural networks, cross-validation, augmented images (lessons 10-11)
* NLP, sentiment analysis, automatic text generation (lessons 12-13)
## ds-1
### The basics
* Importing modules (pandas, numpy, pyplot)
* Opening data
* Basic manipulation
### Visualization
* Pyplot histogram
* Calculations
## Data modeling with sklearn
* Creating training set
* Creating test set
## ds-2
### Cllassification
* K nearest neighbour method
  - we chose a point (k)
  - we check n closest neighbours
  - we predict what k could be
  - number of closest neighbours is always odd
* Decision tree
  - Don't use irrelevant arguments
  - 'No way back' (You can only go down the tree {Not up})
  - Least error is best
* Best cut
* Support vector machines

Possible outcomes

| .        | True | False |
|----------|------|-------|
| Positive | TP   | FP    |
| Negative | TN   | FN    |

# ds-3
## Regression
# ds-4 Analyzing customer habits
## Data prep
* Get data
* Remove N/As

## Clustering
 * sklearn.cluster
 * compute KMeans labels
 * hierarchic clustering
   * linkages
     * complete
     * ward
 * heatmaps with seaborn

# AI1
* TF basics
* using keras
* using keras datasets
* We build neural networks:
### Sequential
```python
from keras.engine.sequential import Sequential
dropout = 0.45
hidden_nodes = 256
batch_size = 128
model = Sequential()
model.add(Dense(hidden_nodes, input_dim=input_size))
model.add(Activation('relu'))
model.add(Dropout(dropout))

model.add(Dense(hidden_nodes))
model.add(Activation('relu'))
model.add(Dropout(dropout))

model.add(Dense(num_labels))
model.add(Activation('softmax'))
```
#### Model summary
```
Model: "sequential"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 dense (Dense)               (None, 256)               200960    
                                                                 
 activation (Activation)     (None, 256)               0         
                                                                 
 dropout (Dropout)           (None, 256)               0         
                                                                 
 dense_1 (Dense)             (None, 256)               65792     
                                                                 
 activation_1 (Activation)   (None, 256)               0         
                                                                 
 dropout_1 (Dropout)         (None, 256)               0         
                                                                 
 dense_2 (Dense)             (None, 10)                2570      
                                                                 
 activation_2 (Activation)   (None, 10)                0         
                                                                 
=================================================================
Total params: 269,322
Trainable params: 269,322
Non-trainable params: 0
_________________________________________________________________
```
- We compile and fit the model for 20 epochs
- We check its accuracy
- Test accuracy: 98.2%

### Convolution
```python
from hashlib import md5

model2 = Sequential()

model2.add(Conv2D(32, (3, 3), activation='relu', input_shape=(28, 28, 1)))
model2.add(MaxPooling2D((2, 2)))
model2.add(Flatten())

model2.add(Dense(100, activation='relu'))
model2.add(Dropout(dropout))

model2.add(Dense(50, activation='relu'))
model2.add(Dropout(dropout))


model2.add(Dense(10, activation='softmax'))
```
- We compile and fit the model for 20 epochs
- We check its accuracy
- Test accuracy: 98.7%
