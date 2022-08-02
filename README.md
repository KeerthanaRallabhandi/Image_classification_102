**Oxford -102 Flowes: Image Classification**

This repo highlights the training and recognition of different species of flowers through transfer learning methods using the 102 flower dataset from Oxford.

Flowers 102 Dataset Brief

This dataset contains 102 different categories of flowers in the United Kingdom. Each flower category contains between min 40 and max 258 images, respectively.

**Steps:**

1. Loading the dataset and label map file for mapping the class label with its respective class name.

2. Resizing/Rescale the images, building and Training the pretrained model on the dataset.

3. Saving and loading the trained model to perform inference on the unseen images.

**Approach:**

Load the Data - Downlaod and unzip the data 102 flowers from Oxford using the Tensorflow Datasets repo. The dataset contains 1020-Train, 1020-Valid and 6149-Test slipts with 102 feature labels/number of classes. 

Vizualizing the Images in order to know the shape of images corresponding to its label for resizing and normalizing the images.

Label Mapping - Loading the label_map.json from the label to its category name which is dict that maps the integer coded labels to the actual names of the flowers.

Normalizing, Resizing and create pipeline for each of the data splits with respect to its image and label batches.

Build and Train - To build and train the classifier, the MobileNet pre-trained model from TensorFlow Hub is used to get the image features. Building and training a new feed-forward classifier using those features.

Loading the MobileNet-V2 pre-trained network from TensorFlow Hub.

Defining untrained feed-forward network as a linear classifier.
- Feature Extarctor and Softmax layer with respect to 102 classes

Training the classifier.
- Epoch - 20
- Batch size - 64
- img size - 224
- optimizer - Adam 

Save the trained model as a Keras model and loading the trained model.
- saved_keras_model_best.h5 file

Testing and Inference - the performance of the trained model is tested on the test data. This provides an estimate for the model's performance on completely new images.
- Model's prediction - predicted labels v/s true labels using classification report which indicates the per class prediction score.

- Inference for classification - Using trained network for inference. predict function that takes an image, trained model and then returns the top  5  most likely class labels along with its probabilities.

- The process_image function takes in an image (NumPy array) and returns an image in the form of a NumPy array with shape (224, 224, 3).

- Converting image into a TensorFlow Tensor and then resizing it to the appropriate size using tf.image.resize.

- The pixel values of the input images (integers) in the range 0-255, converting the pixel values to floats range 0-1 which requires normalizing the pixel values.

- Finally, converting image back to a NumPy array.

- Top 5 label Predictions on the unseen data (sample images passed using Test folder) using the trained model.
  - Class propbailites acheiving upto to 0.7 with Test accuracy upto 70%











