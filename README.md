# SMAPPI-Smart-Apple-Picker-Agent

The **SMAPPI** (Smart Apple Picker) Agent **(see: [Life Demo](https://nmerkle.github.io))** is a *Deep-Q-Neural-Network* agent that has the task to collect within a certain amount of actions, red apples while it has to avoid the poisened green apples and the borders of the playground. SMAPPI wins the game, if it collects all red apples by performing the maxiumum specified number of actions. SMAPPI can perform eight different actions (e.g. *MoveUp, MoveDown, MoveRight, MoveLeft, MoveUpRight, MoveDownRight, MoveUpLeft, MoveDownLeft*) for solving its task. In order to train SMAPPI, it receives reward **(+1)** values, if it collects **red apples** and punishment **(-1)** values if it collects **green poisened apples** or hits the wall (border of the playground). The blue rotating triangle together with the rotating ray indicate the directions (actions), that SMAPPI selects for every moving step. On the right side of the page is a configuration panel where you can set Hyperparameters for the DQNN algorithm such as **learning rate**, **greedy** value for setting the probabilty of selecting actions randomly and **discount** factor. Moreover, you can set the: 
* Framerate of the game (default is 30)
* Field's background color (black or white)
* Number of green and red apples
* Apples' movement status (static or moving)
* Speed (step size) of the agent
* Maximum number of actions that can be performed within an episode.
* Training or Compete mode. In ``compete`` mode every collected apple is removed from the field while in ``training`` mode the apples never get less but change randomly their position. If all given red apples in the field are collected by the agent a new episode with the pre-configured number of apples starts automatically (only) in ``compete`` mode.

Below of the playground, you find three buttons (e.g. ``Stop Game``, ``Start Game`` ``Save JSON``). The names of the buttons are self-evident. Clicking the ``Stop Game`` Button freezes the game. With ``Start Game`` you can start and continue the game. ``Save JSON`` saves the trained DQNN as JSON file on the local storage of the browser. You can reload this JSON file for configuring the agent by selecting the radio button with label *true*  on the configuration panel. By default *false* is selected which means that the agent learns its DQNN from scratch without using a pretrained DQNN.

**NOTE: The Demo is only implemented and tested with Chrome and Firefox browser. It can happen, that in other browsers the page looks different.**

![A screenshot of the game](https://github.com/nmerkle/SMAPPI-Smart-Apple-Picker-Agent/blob/master/screenshot1.png "Screenshot of the SMAPPI game.")

Below of the game and the configuration panel, you can find some statistics (e.g. histogram and line chart) about the performans of SMAPPI. The histogram shows how many negative, zero and positive rewards SMAPPI receives for all its performed actions. The line chart shows the development of the rewards for every action step. 

![The statistic panel of the game](https://github.com/nmerkle/SMAPPI-Smart-Apple-Picker-Agent/blob/master/screenshot2.png "Screenshot of the SMAPPI game.")

# The state representation of SMAPPI
The SMAPPI agent has two different sensors (distance and color sensor) pointing to 8 different directions with a range of 45° and a distance range of 3 meter (= 300px). This means that the state vector consists of ``6 * 8 = 48`` dimensions. For every distance measure a categorical dimension indicates whether the given measure is in range of the distance sensor and therefore available. Only the nearest objects (apple/wall) are considered in the state vector.

| Sensor/Range     | Distance to Wall | Measure available | Distance to red apple | Measure available | Distance to green apple | Measure available |
|------------------|------------------|-------------------|-----------------------|-------------------|-------------------------|-------------------|
| S1 (0°-44°)    | <= 300 px        | 1 or 0            | <= 300 px             | 1 or 0            | <= 300 px               | 1 or 0            |
| S2 (45°-89°)   |                  |                   |                       |                   |                         |                   |
| S3 (90°-134°)  |                  |                   |                       |                   |                         |                   |
| S4 (135°-179°) |                  |                   |                       |                   |                         |                   |
| S5 (180°-224°) |                  |                   |                       |                   |                         |                   |
| S6 (225°-269°) |                  |                   |                       |                   |                         |                   |
| S7 (270°-314°) |                  |                   |                       |                   |                         |                   |
| S8 (315°-360°) |                  |                   |                       |                   |                         |                   |

# How2Run SMAPPI
You require the following Javascript libraries:
* [PlotlyJS](https://github.com/plotly/plotly.js/) for plotting the statistics.
* [ReinforceJS](https://github.com/karpathy/reinforcejs) for the DQNN algorithm.
* [p5.js](https://github.com/processing/p5.js) for the game representation.

and a HTTP server. For testing purposes, I utilized the [Serve](https://github.com/zeit/serve) HTTP server which provides by default access at port 5000. 

**Note: In case you would like to utilize another domain (instead of e.g.localhost) and port, you have to adjust the URL which references the *robot_wiki.png* within the [index.html](https://github.com/nmerkle/nmerkle.github.io/blob/master/index.html).**

# Life demo of SMAPPI
You can access a running life demo of SMAPPI at **[nmerkle.github.io](https://nmerkle.github.io)**. After accessing the page, click ``Start Game``-Button and see how SMAPPI picks :apple:s. You can play around with the hyperparameters and the game configuration in order to improve the agent. Good luck! :+1:

**Hint: If you want to test your trained agent, you have to set the learning rate and greedy value to zero.**
