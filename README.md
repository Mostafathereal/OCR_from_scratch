# Optimized_MNIST_by_hand

## Performance

Batch             |  Mini-Batch
:-------------------------:|:-------------------------:
![](PerformanceCharts/BatchGD_All_performances(train-cost).jpg)  | ![](PerformanceCharts/Mini-BatchGD_All_performances(train-cost).jpg) 


## Optimization Algorithms

### Momentum Gradient Descent

Plain gradient descent limits you from increasing the learning rate to avoid noise near the minimum, and divergence. Momentum reduces this noise and allows you to more safely apporach the min point, meaning you can safely increase the learning rate (to an extent). Momentum Gradient Descent almost always works faster than plain Gradient Descent

- Compute regular gradients
- Compute exponentially weighted averages of gradients
- update the weights and biases with these new gradients

Momentum Gradient Descent:

<a href="https://www.codecogs.com/eqnedit.php?latex=\\&space;V\partial&space;w,&space;\&space;V&space;\partial&space;b&space;=&space;0&space;\\On&space;\&space;Iteration&space;\&space;t;&space;\\&space;\indent{}&space;Compute&space;\&space;\partial&space;w&space;\&space;and&space;\&space;\partial&space;b&space;\\&space;\indent{}&space;V&space;\partial&space;w&space;=&space;\beta&space;V&space;\partial&space;w&space;&plus;&space;(1-\beta)\partial&space;w&space;\\&space;\indent{}&space;V&space;\partial&space;b&space;=&space;\beta&space;V&space;\partial&space;b&space;&plus;&space;(1-\beta)\partial&space;b&space;\\&space;\indent{}&space;w&space;:=&space;w&space;-&space;\alpha&space;V&space;\partial&space;w&space;\\&space;\indent{}&space;b&space;:=&space;b&space;-&space;\alpha&space;V&space;\partial&space;b" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\\&space;V\partial&space;w,&space;\&space;V&space;\partial&space;b&space;=&space;0&space;\\On&space;\&space;Iteration&space;\&space;t;&space;\\&space;\indent{}&space;Compute&space;\&space;\partial&space;w&space;\&space;and&space;\&space;\partial&space;b&space;\\&space;\indent{}&space;V&space;\partial&space;w&space;=&space;\beta&space;V&space;\partial&space;w&space;&plus;&space;(1-\beta)\partial&space;w&space;\\&space;\indent{}&space;V&space;\partial&space;b&space;=&space;\beta&space;V&space;\partial&space;b&space;&plus;&space;(1-\beta)\partial&space;b&space;\\&space;\indent{}&space;w&space;:=&space;w&space;-&space;\alpha&space;V&space;\partial&space;w&space;\\&space;\indent{}&space;b&space;:=&space;b&space;-&space;\alpha&space;V&space;\partial&space;b" title="\\ V\partial w, \ V \partial b = 0 \\On \ Iteration \ t; \\ \indent{} Compute \ \partial w \ and \ \partial b \\ \indent{} V \partial w = \beta V \partial w + (1-\beta)\partial w \\ \indent{} V \partial b = \beta V \partial b + (1-\beta)\partial b \\ \indent{} w := w - \alpha V \partial w \\ \indent{} b := b - \alpha V \partial b" /></a>

### RMSProp - Root Mean Squared Prop.A
Again, this allows us to increase the learning rate by dampening the oscillations (noise) as we move closer to the minimum (of the cost func.)

- Compute regular gradients
- Compute exponentially weighted averages of gradients (using possibly different EWA constant - <a href="https://www.codecogs.com/eqnedit.php?latex=\beta_2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\beta_2" title="\beta_2" /></a>)
- update the weights and biases with these new gradients using root mean squared method

RMSProp:

<a href="https://www.codecogs.com/eqnedit.php?latex=\\&space;S&space;\partial&space;w,&space;\&space;S&space;\partial&space;b&space;=&space;0&space;\\On&space;\&space;Iteration&space;\&space;t;&space;\\&space;\indent{}&space;Compute&space;\&space;\partial&space;w&space;\&space;and&space;\&space;\partial&space;b&space;\\&space;\indent{}&space;S&space;\partial&space;w&space;=&space;\beta&space;_2S&space;\partial&space;w&space;&plus;&space;(1-\beta_2)\partial&space;w^2&space;\\&space;\indent{}&space;S&space;\partial&space;b&space;=&space;\beta&space;_2S&space;\partial&space;b&space;&plus;&space;(1-\beta_2)\partial&space;b^2&space;\\&space;\indent{}&space;w&space;:=&space;w&space;-&space;\alpha&space;\frac{\partial&space;w}{\sqrt{S&space;\partial&space;w}&space;&plus;&space;\varepsilon&space;}&space;\\&space;\indent{}&space;b&space;:=&space;b&space;-&space;\alpha&space;\frac{\partial&space;b}{\sqrt{S&space;\partial&space;b}&space;&plus;&space;\varepsilon&space;}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\\&space;S&space;\partial&space;w,&space;\&space;S&space;\partial&space;b&space;=&space;0&space;\\On&space;\&space;Iteration&space;\&space;t;&space;\\&space;\indent{}&space;Compute&space;\&space;\partial&space;w&space;\&space;and&space;\&space;\partial&space;b&space;\\&space;\indent{}&space;S&space;\partial&space;w&space;=&space;\beta&space;_2S&space;\partial&space;w&space;&plus;&space;(1-\beta_2)\partial&space;w^2&space;\\&space;\indent{}&space;S&space;\partial&space;b&space;=&space;\beta&space;_2S&space;\partial&space;b&space;&plus;&space;(1-\beta_2)\partial&space;b^2&space;\\&space;\indent{}&space;w&space;:=&space;w&space;-&space;\alpha&space;\frac{\partial&space;w}{\sqrt{S&space;\partial&space;w}&space;&plus;&space;\varepsilon&space;}&space;\\&space;\indent{}&space;b&space;:=&space;b&space;-&space;\alpha&space;\frac{\partial&space;b}{\sqrt{S&space;\partial&space;b}&space;&plus;&space;\varepsilon&space;}" title="\\ S \partial w, \ S \partial b = 0 \\On \ Iteration \ t; \\ \indent{} Compute \ \partial w \ and \ \partial b \\ \indent{} S \partial w = \beta _2S \partial w + (1-\beta_2)\partial w^2 \\ \indent{} S \partial b = \beta _2S \partial b + (1-\beta_2)\partial b^2 \\ \indent{} w := w - \alpha \frac{\partial w}{\sqrt{S \partial w} + \varepsilon } \\ \indent{} b := b - \alpha \frac{\partial b}{\sqrt{S \partial b} + \varepsilon }" /></a>

### Adam Optimization
This algorithm puts Momentum and RMSProp together. It is shown to generalize well and work over a wide range of applications. Note that the typical implementation of Adam Optimization includes bias correction where as Momentum and RMSProp dont. Bias correction is

- compute regular gradients
- compute momentum gradients
- compute RMSProp gradients
- perform bias correction
- update parameters using both Momentum and RMSProp corrected gradients

Adam:

<a href="https://www.codecogs.com/eqnedit.php?latex=\\V&space;\partial&space;w,&space;\&space;V&space;\partial&space;b,&space;\&space;S&space;\partial&space;w,&space;\&space;S&space;\partial&space;b&space;=&space;0&space;\\On&space;\&space;Iteration&space;\&space;t;&space;\\&space;\indent{}&space;Compute&space;\&space;\partial&space;w&space;\&space;and&space;\&space;\partial&space;b&space;\\&space;\indent{}&space;V&space;\partial&space;w&space;=&space;\beta_1&space;V&space;\partial&space;w&space;&plus;&space;(1-\beta_1)\partial&space;w&space;\\&space;\indent{}&space;V&space;\partial&space;b&space;=&space;\beta_1&space;V&space;\partial&space;b&space;&plus;&space;(1-\beta_1)\partial&space;b&space;\\&space;\indent{}&space;S&space;\partial&space;w&space;=&space;\beta&space;_2S&space;\partial&space;w&space;&plus;&space;(1-\beta_2)\partial&space;w^2&space;\\&space;\indent{}&space;S&space;\partial&space;b&space;=&space;\beta&space;_2S&space;\partial&space;b&space;&plus;&space;(1-\beta_2)\partial&space;b^2&space;\\&space;\indent{}&space;V&space;\partial&space;w^{corrected}&space;=&space;\frac{V&space;\partial&space;w}{1-\beta_1^t}&space;\\&space;\indent{}&space;V&space;\partial&space;b^{corrected}&space;=&space;\frac{V&space;\partial&space;b}{1-\beta_1^t}&space;\\&space;\indent{}&space;S&space;\partial&space;w^{corrected}&space;=&space;\frac{S&space;\partial&space;w}{1-\beta_2^t}&space;\\&space;\indent{}&space;S&space;\partial&space;b^{corrected}&space;=&space;\frac{S&space;\partial&space;b}{1-\beta_2^t}&space;\\&space;\indent{}&space;w&space;:=&space;w&space;-&space;\alpha&space;\frac{V\partial&space;w^{corrected}}{\sqrt{S&space;\partial&space;w^{corrected}}&space;&plus;&space;\varepsilon&space;}&space;\\&space;\indent{}&space;b&space;:=&space;b&space;-&space;\alpha&space;\frac{V\partial&space;b^{corrected}}{\sqrt{S&space;\partial&space;b^{corrected}}&space;&plus;&space;\varepsilon&space;}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\\V&space;\partial&space;w,&space;\&space;V&space;\partial&space;b,&space;\&space;S&space;\partial&space;w,&space;\&space;S&space;\partial&space;b&space;=&space;0&space;\\On&space;\&space;Iteration&space;\&space;t;&space;\\&space;\indent{}&space;Compute&space;\&space;\partial&space;w&space;\&space;and&space;\&space;\partial&space;b&space;\\&space;\indent{}&space;V&space;\partial&space;w&space;=&space;\beta_1&space;V&space;\partial&space;w&space;&plus;&space;(1-\beta_1)\partial&space;w&space;\\&space;\indent{}&space;V&space;\partial&space;b&space;=&space;\beta_1&space;V&space;\partial&space;b&space;&plus;&space;(1-\beta_1)\partial&space;b&space;\\&space;\indent{}&space;S&space;\partial&space;w&space;=&space;\beta&space;_2S&space;\partial&space;w&space;&plus;&space;(1-\beta_2)\partial&space;w^2&space;\\&space;\indent{}&space;S&space;\partial&space;b&space;=&space;\beta&space;_2S&space;\partial&space;b&space;&plus;&space;(1-\beta_2)\partial&space;b^2&space;\\&space;\indent{}&space;V&space;\partial&space;w^{corrected}&space;=&space;\frac{V&space;\partial&space;w}{1-\beta_1^t}&space;\\&space;\indent{}&space;V&space;\partial&space;b^{corrected}&space;=&space;\frac{V&space;\partial&space;b}{1-\beta_1^t}&space;\\&space;\indent{}&space;S&space;\partial&space;w^{corrected}&space;=&space;\frac{S&space;\partial&space;w}{1-\beta_2^t}&space;\\&space;\indent{}&space;S&space;\partial&space;b^{corrected}&space;=&space;\frac{S&space;\partial&space;b}{1-\beta_2^t}&space;\\&space;\indent{}&space;w&space;:=&space;w&space;-&space;\alpha&space;\frac{V\partial&space;w^{corrected}}{\sqrt{S&space;\partial&space;w^{corrected}}&space;&plus;&space;\varepsilon&space;}&space;\\&space;\indent{}&space;b&space;:=&space;b&space;-&space;\alpha&space;\frac{V\partial&space;b^{corrected}}{\sqrt{S&space;\partial&space;b^{corrected}}&space;&plus;&space;\varepsilon&space;}" title="\\V \partial w, \ V \partial b, \ S \partial w, \ S \partial b = 0 \\On \ Iteration \ t; \\ \indent{} Compute \ \partial w \ and \ \partial b \\ \indent{} V \partial w = \beta_1 V \partial w + (1-\beta_1)\partial w \\ \indent{} V \partial b = \beta_1 V \partial b + (1-\beta_1)\partial b \\ \indent{} S \partial w = \beta _2S \partial w + (1-\beta_2)\partial w^2 \\ \indent{} S \partial b = \beta _2S \partial b + (1-\beta_2)\partial b^2 \\ \indent{} V \partial w^{corrected} = \frac{V \partial w}{1-\beta_1^t} \\ \indent{} V \partial b^{corrected} = \frac{V \partial b}{1-\beta_1^t} \\ \indent{} S \partial w^{corrected} = \frac{S \partial w}{1-\beta_2^t} \\ \indent{} S \partial b^{corrected} = \frac{S \partial b}{1-\beta_2^t} \\ \indent{} w := w - \alpha \frac{V\partial w^{corrected}}{\sqrt{S \partial w^{corrected}} + \varepsilon } \\ \indent{} b := b - \alpha \frac{V\partial b^{corrected}}{\sqrt{S \partial b^{corrected}} + \varepsilon }" /></a>
