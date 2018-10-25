# Recurrent_Neural_Networks_Keras
I have implemented Recurrent Neural Networks using Keras.

Step 1: Here we begin with importing the libraries which are required. We have imported numpy library for performing mathematical operations, structuring the input, output and data labels.After this, we have imported some specific functions of Keras used for building our RNN. The specific role of different functions will be discussed in later steps.

Step 2: For performing the actual code implementation, we will require the input data. Here the input data is a monologue from Othello. You can get the text file from here. Remember to save the text file in the same directory where the python/Jupyter notebook is kept.The input data which is available is in the form of text and we want to convert it into the form compatible with Keras. For the same reason, we are converting the text into lowercase which is a form of normalization.
After this, we are creating sorted () list of character in the text and store number of characters in the dataset in the ‘totalchars’. Lastly we are storing the length of characters which will consist the number of unique characters.

Step 3:	For representing each character in for numbers, we will be using dictionaries for the same.First we are creating the dictionary where character is the key and each key character is represented using a number. In the next line of code, we are doing the opposite of the previous line. Lastly, we are deciding the number of characters to be trained in one time step i.e. one training example.

Step 4: The following counter is used for looping 100 times (number of characters learned).Now we have created empty lists for storing formatted data in the form of input ‘charX’ and output ‘y’. ‘theInputChars’ is used for storing the first 100 input characters and after this loop is repeated as it takes the next 100 input characters and this loop is continued for the rest of the inputs.‘theOutputChars’ stores only one character which is the next character after the final character in ‘theInputChars’
Lastly, in the ‘charX’ list we are appending 100 integers which are trained in the iteration and these integers are representing the ID’s of characters which were the input. Along with this, the integer ID is also appended to the ‘y’ list which is the output of single character in ‘theOutputChars’.

Step 5: After the above steps, we want the data to be in correct form for Keras.
First we are shaping the input array where the three parameters represent ‘samples’ , ‘time-steps’ and ‘features’, this form is necessary for Keras. For efficient and effective results we are normalising the data.

Now we are transforming the ‘y’ into a one-hot vector. The one-hot vector is an array of 0’s and 1’s. In this vector 1’s occur only at positions where the ID is found to be true. This same process is followed for 100 different examples having the length of ‘numberOfUniqueChars’.

Step 6: Finally it’s time to build our Recurrent Neural Network model.In the code snippet, Line 1 uses the Sequential () which is imported from Keras. It is used for creating an empty template model used for building RNN.
In the next line, we add the first layer to the empty template model. This layer is LSTM layer containing 256 units and ‘input_shape’ as its one of the parameters.
‘Dropout’ import ensures that overfitting which occurs frequently in RNN is restricted to minimum. For restricting overfitting, this imported function randomly selects neurons and ignores them during training. Here ‘Dropout’ is provided with a parameter as ‘0.2’ which means 20% of the neurons will be dropped.
‘Dense’ is used for getting the output in the form of a layer of any neural network/recurrent neural network.
Using the ‘add’ function from the import, the available layer acts an output layer. Here we use the activation of the dot of the weights and inputs along with bias.

Now in configuration settings, we have loss function with parameter as ‘categorical_crossentropy’ and optimizer is ‘Adam’.
With the fit () function we will run the training algorithm. Here the epochs are specifying the number of times the batches are to be evaluated. In this tutorial the number of epochs is taken as 100 and if you want you can change the number of epochs and see what different results you can get. With the batch size number, we are specifying the number of input data set we want to evaluate. For this practical, it is set as 128 i.e. first 128 examples are going as input then next 128 and this continues for the whole data set.
At last, the training is completed and we can save the weights. Moreover, we can also load the previously trained weights.

Output:
The following is the output which is expected when we start the training process, it will take some time. You can see that each of the 100 epochs are executed and the error i.e. loss value is continuously decreased which is a good sign.
Once this computing is finished, the code will now jump to the code for predicting the text. So let’s have a look at it.

Step 7:
Initially in Line 1 we are generating random values from 0 to one less than the length of input data. In Line 2 we get the starting sentence in form of integer form.
With Line 3 we are initiating a loop for 500 times, this value can be changed to see the different results, the value 500 means we are generating 500 characters through this loop.
Using Line 4 we are generating a data example used for predicting the next character. After normalising in Line 5, we supply it to the prediction model in Line 6. In Line 7 we get the index of the next predicted character after that sentence. In Line 8 and 9 we are appending the character predicted to the starting sentence which gives 101 characters and so we can omit the first character to get next 100 characters.
Lastly, we are looping until 500 and printing out the generated text by conversion of ID’s to the designated characters.

Finally, we will get the output which is dependent upon the number of epochs i.e. the training which is provided to the model. The output will be still not very understandable since this is a basic model of RNN.







