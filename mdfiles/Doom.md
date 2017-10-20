#POWERING AI TO PLAY DOOM IN OPENAI GYM

The project was done as part of the online course [Artificial Intelligence A-Z](https://www.udemy.com/artificial-intelligence-az/). Here, I have implemented Deep Convolutional Q-Learning to create a model which will play Doom in OpenAI Gym.

<div class = "middle"> 
<iframe width="560" height="315" style=""src="https://www.youtube.com/embed/X_riUKeWabc" frameborder="0" allowfullscreen></iframe>
</div>

##### First and Fifth attempt my AI to play Doom.

## Test Data

The images of AI playing Doom in AI GYM are obtained from the API provided by the OpenAI Gym.  The images acquired are `preprocessed` and are stored in a large array to implement `Experience Reply`. Experience Replay is randomly sampling the large pool The large pool of memory is randomly sampled and the images are fed into the neural network. The advantage of using experience replay is that it helps the network for better convergence. Another advantage is that when sampling from a large pool, the network will not forget previous learnings. This feature can also be used when the model is trained to play different levels of the game. Hence, the network will not forget how to play the first level after playing the next few levels.

## Eligibility Trace

Instead of backpropogating loss after every step to update the weights I have implemented `Eligibility Trace`. Eligibility trace is the process of evaluating the cumulative reward or loss after n-steps instead of a single step. It obtains the steps which are responsible for the negative reward, and the algorithm also keeps track of which step needs to be updated based on that reward. For this project, I have implemented a ten step eligibility trace. So, the model will calculate the cumulative reward/loss after ten steps.

## Neural Network

The model will be using three convolutional layers and then two fully connected layers with all the layers using `ReLU activation function` to alleviate the `Vanishing gradient problem` associated with many of the other activation functions. The program is structured such that the randomly sampled images are fed into the convolutional neural network.  The first two convolutional layers are designed to generate 32 feature images each as they are used for acquiring the high-level features of the images. The feature images attained are then fed into the third convolutional layer which generates 64 feature images. The third layer generates a greater number of feature images as its objective is to obtain more complex features of the images.  

The feature maps from the final convolutional layer are then fed into a layer fully connected network. Here two fully connected layers are used, and the number of output neurons of the second layer is equal to the number of input actions available for the game.


The output is then fed into a `Softmax function` which will convert the Q values into probabilities and select an action accordingly. The softmax function is also given a `temperature variable` which decides the amount of exploration that will be done. The action selected by the softmax function is implemented, and the reward associated with the step is stored in an array. The loss is calculated at the end of ten steps using `Mean Squared Error Method`, and the loss is `back-propagated` into the neural network and the weights are updated using the `Adam Optimizer`. Thus, the steps which are responsible for the losses are identified and replaced by the neural network.

## Training

The neural network is trained in `200 epochs` of `10 steps` each. The program is set to terminate when the AI acquires the average reward of 1500. However, an average reward of greater than 1000 would be sufficient for the AI to beat the game. But the AI can still update itself so that it can complete the game more efficiently. The first and last attempt of the AI playing the can be viewed in the video below. 

The video provided above shows the AI's first attempt and the last attempt at beating the game. As you can see in the 5th trial the AI successfully beats the game. We can also see all the five attempts made by the AI in the video below to get an idea of how quickly the AI is capable of learning.



