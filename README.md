# SMAPPI-Smart-Apple-Picker-Agent

The SMAPPI (Smart Apple Picker) Agent is an Deep-Q-Neural-Network agent that has the task to collect red apples while it has to avoid the poisened green apples and the borders of the playground. SMAPPI can perform eight different actions (e.g. MoveUp, MoveDown, MoveRight, MoveLeft, MoveUpRight, MoveDownRight, MoveUpLeft, MoveUpRight) for solving its task. In order to train SMAPPI, it receives reward (+1) values, if it collects red apples and punishment (-1) values if it collects green poisened apples or hits the wall (border of the playground). The blue rotating triangle together with the rays indicate the directions (actions), that SMAPPI selects for every moving step. On the right side of the page is a configuration panel where you can set Hyperparameters for the DQNN algorithm such as learning rate, greedy value and discount factor. Moreover, you can set how many green and red apples shall be generated and if the apples shall move on the field or be static. Below of the game and the configuration panel, you can find some statistics (e.g. histogram and line chart) about the performans of SMAPPI. The histogram shows how many negative, zero and positive rewards SMAPPI received for all its performed actions. The line chart shows the development of the rewards for every action step. Below of the playground you find three buttons (e.g. *Stop Game*, *Start Game* *Save JSON*). The names of the buttons are self-evident. Clicking the *Stop Game* Button freezes the game. With *Start Game* you can continue the game. *Save JSON* saves the trained DQNN as JSON file on the local storage of the browser. You can reload this JSON file for configuring the agent by selecting the radio button with label *true*  on the configuration panel.

**NOTE: The Demo is only implemented and tested with Chrome browser. It can happen, that in other browsers the page looks different or does not work properly.**

![alt text](https://github.com/nmerkle/SMAPPI-Smart-Apple-Picker-Agent/blob/master/screenshot1.png "Screenshot of the SMAPPI game.")

![alt text](https://github.com/nmerkle/SMAPPI-Smart-Apple-Picker-Agent/blob/master/screenshot2.png "Screenshot of the SMAPPI game.")

# How2Run SMAPPI
You require the following Javascript libraries:
* [PlotlyJS](https://github.com/plotly/plotly.js/)
* [ReinforceJS](https://github.com/karpathy/reinforcejs/blob/master/index.html) 
* [p5.js](https://github.com/processing/p5.js)

and a HTTP server. For testing purposes, I utilized the [Serve](https://github.com/zeit/serve) HTTP server which provides by default access at port 5000. In case you would like to utilize another HTTP server, you have to adjust the port number within the [AgentDemo.html](https://github.com/nmerkle/SMAPPI-Smart-Apple-Picker-Agent/blob/master/AgentDemo.html).ECHO ist eingeschaltet (ON).
