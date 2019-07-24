### Model training specification:
- input layer
 - recevies spectrum power with feature size of 81
- Hidden layers
 - 3 layer of 2d conv layer followed by 7 layers of Bidirectional RNN-LSTM(512 hidden units each)
 - Dropout is applied and batch normalization as well.
- Fully connected output layer

#### Training data specficiation 
- train : 44838 audio files (wav), all audio files are less than 12 secs in durartion. Range(5secs to 12 secs)
  - 95.6 hours of audio data
- Validation: 2362 audio files (wav), all audio files are less than 12 secs in durartion Range(5secs to 12 secs)
  - 3.8 hours of audio data
- test : 1956 audio files (wav), all audio files are less than 12 secs in durartion Range(5secs to 12 secs)
  - 3.2 hours of audio data
  
#### Problem:
- I have more than 1000 hour of training data and I am not able to use them, if I use them all 1 epoch will take 23.5 hours to 
train. Which means it will take 40 days if I want the model to train for 40 epochs. 
- Curent training take per epoch 2.1 hour which mean it will take 3-4 days to complete the training. I am just using 1/10 th of librispeech data.

#### Good news:
- I have created a distributed training program which can be train on multiple gpu. (completed)
- We can queue in data and keep the model for training for ever, and use the latest model to setup a test server and run 
inference. (completed )
- Write program to record audio wav file and perform inference (in progress), till we get all pacakeages approved on domino 
we cannot run this model on domino.

### I did some prediction, during the training, specifically after completion of 9 epochs.
07-24 11:41:30 Ground Truth :gradually relief came to all of us
 
07-24 11:41:30 ArSI Prediction :gradually beleve came all of us

07-24 11:41:30 Word Error Rate :0.2857142857142857 Charchter Error Rate:0.20588235294117646


07-24 11:41:47 Ground Truth :i promise you i will do you no harm

07-24 11:41:47 ArSI Prediction :i proase you i will do you no harm

07-24 11:41:47 Word Error Rate :0.1111111111111111 Charchter Error Rate:0.05714285714285714


07-24 11:41:52 Ground Truth :i could not help my friend

07-24 11:41:52 ArSI Prediction :i could not help my friend

07-24 11:41:52 Word Error Rate :0.0 Charchter Error Rate:0.0


07-24 11:42:01 Ground Truth :she had lost him years and years before and now she saw him he was there and she knew him

07-24 11:42:01 ArSI Prediction :she had lostd him years an years before and now she ta him he was there and she knew him
07-24 11:42:01 Word Error Rate :0.15 Charchter Error Rate:0.0449438202247191

07-24 11:42:06 Ground Truth :but here the only thing that occurred to her was to stop and look in one of the shops till he should ask her what she was looking at
07-24 11:42:06 ArSI Prediction :but here the only thing that accured to her was the stop and look in one of the shops til he should aske her what she was looking at
07-24 11:42:06 Word Error Rate :0.13793103448275862 Charchter Error Rate:0.045454545454545456

07-24 11:42:36 Ground Truth :to the pickle add two large onions cut in quarters two fresh carrots and about one ounce of mixed whole allspice black peppers cloves and bay leaves
07-24 11:42:36 ArSI Prediction :through the pickle ad to largurnians cout incarders to frish herit and about one hount of mixed hal al pice what peppers clos and balives
07-24 11:42:36 Word Error Rate :0.7037037037037037 Charchter Error Rate:0.27702702702702703

07-24 11:41:00 Ground Truth :the people must wait outside for there is no room for them in the palace
07-24 11:41:00 ArSI Prediction :the people miss we ouside for there is no room for them in etalace
07-24 11:41:00 Word Error Rate :0.3333333333333333 Charchter Error Rate:0.1388888888888889

07-24 11:43:56 Ground Truth :this is the problem of race
07-24 11:43:56 ArSI Prediction :this is the proble of race
07-24 11:43:56 Word Error Rate :0.16666666666666666 Charchter Error Rate:0.037037037037037035

07-24 11:44:43 Ground Truth :yes many times
07-24 11:44:43 ArSI Prediction :yes many tine
07-24 11:44:43 Word Error Rate :0.3333333333333333 Charchter Error Rate:0.14285714285714285


