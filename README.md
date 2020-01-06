# SMAPPI-Smart-Apple-Picker-Agent

The **SMAPPI** (Smart Apple Picker) Agent **(see: [Life Demo](https://nmerkle.github.io))** is a *Deep-Q-Neural-Network* agent that has the task to collect red apples while it has to avoid the poisened green apples and the borders of the playground. SMAPPI can perform eight different actions (e.g. **MoveUp, MoveDown, MoveRight, MoveLeft, MoveUpRight, MoveDownRight, MoveUpLeft, MoveUpRight**) for solving its task. In order to train SMAPPI, it receives reward **(+1)** values, if it collects **red apples** and punishment **(-1)** values if it collects **green poisened apples** or hits the wall (border of the playground). The blue rotating triangle together with the rotating ray indicate the directions (actions), that SMAPPI selects for every moving step. On the right side of the page is a configuration panel where you can set Hyperparameters for the DQNN algorithm such as **learning rate**, **greedy** valu and **discount** factor. Moreover, you can set how many green and red apples shall be generated and if the apples shall move on the field or be static. Below of the playground, you find three buttons (e.g. ``Stop Game``, ``Start Game`` ``Save JSON``). The names of the buttons are self-evident. Clicking the ``Stop Game`` Button freezes the game. With ``Start Game`` you can start and continue the game. ``Save JSON`` saves the trained DQNN as JSON file on the local storage of the browser. You can reload this JSON file for configuring the agent by selecting the radio button with label *true*  on the configuration panel. By default *false* is selected which means that the agent learns its DQNN from scratch without using a pretrained DQNN.

**NOTE: The Demo is only implemented and tested with Chrome and Firefox browser. It can happen, that in other browsers the page looks different.**

![alt text](https://github.com/nmerkle/SMAPPI-Smart-Apple-Picker-Agent/blob/master/screenshot1.png "Screenshot of the SMAPPI game.")

Below of the game and the configuration panel, you can find some statistics (e.g. histogram and line chart) about the performans of SMAPPI. The histogram shows how many negative, zero and positive rewards SMAPPI receives for all its performed actions. The line chart shows the development of the rewards for every action step. 

![alt text](https://github.com/nmerkle/SMAPPI-Smart-Apple-Picker-Agent/blob/master/screenshot2.png "Screenshot of the SMAPPI game.")

# The state representation of SMAPPI
The state vector of SMAPPI consists of the *euklidean* distances to all apples, the *apple color* (1 for red, and 0 for green), the *angles* of the agent relative to every apple and the x and y position of the agent. The number of states is computed by the following equation:

``` javascript
const stateVectorNum = (numRedApples * 3) + (numGreenApples * 3) + numAgentCoordinates
```
For instance, if 20 red and 20 green apples are in the field then the state vector number would be computed by:

``` console
stateVectorNum = 20 * 3 + 20 * 3 + 2 = 122
```

# How2Run SMAPPI
You require the following Javascript libraries:
* [PlotlyJS](https://github.com/plotly/plotly.js/) for plotting the statistics.
* [ReinforceJS](https://github.com/karpathy/reinforcejs/blob/master/index.html) for the DQNN algorithm.
* [p5.js](https://github.com/processing/p5.js) for the game representation.

and a HTTP server. For testing purposes, I utilized the [Serve](https://github.com/zeit/serve) HTTP server which provides by default access at port 5000. 

**Note: In case you would like to utilize another domain (instead of e.g.localhost) and port, you have to adjust the URL which references the *robot_wiki.png* within the [index.html](https://github.com/nmerkle/nmerkle.github.io/blob/master/index.html).**

# Life demo of SMAPPI
You can access a running life demo of SMAPPI at **[nmerkle.github.io](https://nmerkle.github.io)**. After accessing the page, click ``Start Game``-Button and see how SMAPPI picks :apple:s.
