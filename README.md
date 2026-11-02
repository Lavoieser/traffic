# traffic
Week 5 CS50 AI with Python
First part of the work was load_data
Main difficulties:  understand os tools to manipulate path information
                    familiarization with cv2 for cv2.imread and cv2.imresize
                    understanding numpy.ndarray
After lot of trial and error, seems to work fine.

Pretty difficult to navigate through the TensionFlow guide. I finaly found this location https://www.tensorflow.org/api_docs/python/tf/keras/layers that was quite usefu. I also found https://www.tensorflow.org/tutorials/images/cnn which specifically explain computer vision applications.
I use the same sequential model as the course's digit problem. My first runs gave accuracies lower than 25%. Not impressive.
I finally realized that I did not normalize the RGB value from 0-255 to 0-1. I added the line     images = np.array(images) / 255.0, the accuracy increased to 96% - good enough.
Epoch 10/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 6s 12ms/step - accuracy: 0.8642 - loss: 0.4239 
333/333 - 2s - 6ms/step - accuracy: 0.9567 - loss: 0.1801

I got a message from the system when running the original program: 
    UserWarning: Do not pass an `input_shape`/`input_dim` argument to a layer. When using Sequential models, prefer using an `Input(shape)` object as the first layer in the model instead.
In response, I changed the definition of the model to add a specific line for the shape of the input as this:
    Corrected version:
         model = tf.keras.models.Sequential([
        tf.keras.Input(shape=(IMG_WIDTH, IMG_HEIGHT, 3)),

    # Convolutional layer. Learn 32 filters using a 3x3 kernel
        tf.keras.layers.Conv2D(
            32, (3, 3), activation="relu",
        ), ......
    Original version (which generated to warning message):
      tf.keras.layers.Conv2D(
            32, (3, 3), activation="relu", input_shape=(IMG_WIDTH, IMG_HEIGHT,3)
        ), .......

Final result, 95.78% accuracy.
Epoch 1/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 9s 14ms/step - accuracy: 0.3703 - loss: 2.3648     
Epoch 2/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 6s 12ms/step - accuracy: 0.6462 - loss: 1.1807 
Epoch 3/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 6s 12ms/step - accuracy: 0.7384 - loss: 0.8436 
Epoch 4/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 6s 12ms/step - accuracy: 0.7802 - loss: 0.6892 
Epoch 5/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 6s 11ms/step - accuracy: 0.8154 - loss: 0.5803 
Epoch 6/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 6s 12ms/step - accuracy: 0.8313 - loss: 0.5260 
Epoch 7/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 6s 12ms/step - accuracy: 0.8473 - loss: 0.4688 
Epoch 8/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 6s 12ms/step - accuracy: 0.8575 - loss: 0.4368 
Epoch 9/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 6s 12ms/step - accuracy: 0.8652 - loss: 0.3964 
Epoch 10/10
500/500 ━━━━━━━━━━━━━━━━━━━━ 6s 11ms/step - accuracy: 0.8759 - loss: 0.3821 
333/333 - 2s - 7ms/step - accuracy: 0.9678 - loss: 0.1432