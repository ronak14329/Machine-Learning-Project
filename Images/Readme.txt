============================================================
To Run tcss555_images file, please fallow below steps
============================================================

1.Software Installations:

     Install python 2.7 version
          on ubuntu/linux: on terminal type: sudo apt-get install python
         
     Install scikit learn package
          on ubuntu/linux: on terminal type: pip install -U scikit-learn

     Install numpy package
          on ubuntu/linux: on terminal type: sudo apt-get install python-numpy

     Install scipy package
          on ubuntu/linux: on terminal type: sudo apt-get install python-scipy

     Install Opencv: 
          on ubuntu/linux: sudo apt-get install python-opencv

     Install Tensorflow: URL : https://www.tensorflow.org/versions/r0.7/get_started/os_setup.html
             
           

2. Inside the code in main function, change the path location of "trainingdir" to the directry of training data set on your local system.

3.Run the program using terminal window: ./tcss555_images -i /data/public-test-data -o ~/outputDir

4.The program will run and produce output XML files.

==========================================================================
Code Description
========================================================================== 

The code is implemented in python using OpenCv Face Recognizer and TensorFlow deep neural network algorithms.

In OpenCV, I have used HaarCascade classifer and LBPH face recognizer techniques.
Intially I convert the image into gray scale and then crop the face using harr cascades.

Resized the image into specific size. So, that all the images would be in same size for training.

Inside OpenCv there are existing functions like 'train', which takes inpput as set of images and labels.

There is also one builtin 'predict' method on the top of trained object.

'predict' method accepts set of testing images and returns a list of corresponding label predictions.

We have used scikit-learn accuracy score measure function, to measure the accuracy of above predicted labels Vs Actual labels.

Coming to TensorFlow,

I converted the Image into gray scale

I converted the image into multi dimensional numeric array, since tensor flow works on images as a numerical array values

I constructed a graph network, where each node represents a weight update value and edges reresents the multi dimensional numeric value array. 

This can be done in oneline using tensor flow (tf.session())

I have used Gradient Decent weight update rule to minimize 'cross-entropy' value

The internal working process is similar to back propogation algorithm


Ref : url: https://www.tensorflow.org/versions/r0.7/tutorials/mnist/pros/index.html#setup




==============================================================================================
Functions Description
==============================================================================================

def predict_gender_labels(path,testpath,recognizer): For each image in the testset, the recognizer returns predicted label. 
Finally function returns a list of all predicted labels

def public_test_data(path):Prepare the test data. Basically we exctraced each image and did preprocessing steps (crop, resize,grayscale, etc)


def test_images_and_labels(path,index,training_set):

cascadePath = cv2.CascadeClassifier('haarcascade_frontalface_default.xml') : Opencv already contains pre-trained classifiers for face, eyes, smile etc.

So loading the XML that contains these classifiers.

faceCascade = cv2.CascadeClassifier(cascadePath) 

  
faces=faceCascade.detectMultiScale(image_pic): If faces are found, it returns the position of detected faces as Rect(x,y,w,h)
    
recognizer = cv2.createLBPHFaceRecognizer() : For face recognition we will use the the LBPH Face Recognizer 

recognizer.train(t_images, np.array(t_labels)) : In opencv there is 'train' method that we can use to train our model

nbr_predicted,conf = recognizer.predict(image): In opencv there is 'predict' method that we can call 

for predictions. It returns a predicted label and confidence level


def testdata(directry): Reads all the test images and convert each image into a numpy array and store it as a list of lists for testing.


def flatten(vec): It helps fatten the image vector.


def imagevector(directry): It helps to create a set of numpy arrays for training data.


def train_age(data_gen, test_gen): Train the model to predict age. Basically, training the neural network based on label age. In tensorflow this
 
can be done in few steps. Each step in the code contains comments, so that it helps to understand better how it is working.


def train_and_test(data_gen, test_gen): Train the model to predict gender label. Same code as above, but the prediction label is different.







