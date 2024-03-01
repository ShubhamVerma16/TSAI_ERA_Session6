# Backpropagation
# Network Diagram of the fully connected layer
![image](https://github.com/ShubhamVerma16/TSAI_ERA_Session6/assets/46774613/3d1eb267-b024-4d0a-a814-3e75d4a92a60)
- The image represents a fully connected network.
- t1, t2 are the target values against which we need to compare the loss to do the back-propagation.
- Initial values with weights are provided. No bias is included as part of this network.
The activation function used in the hidden layers is Sigmoid (σ) = $1/1+exp(-x)$

In a fully-connected network, every neuron in each layer gets input from all the neurons from the previous layer.
## h1
- h1 takes input from i1 & i2 with their corresponding weights w1 & w2. So
  <pre>h1 = w1 * i1 + w2 * i2</pre>
- The output of h1 has to be passed to the next layer.
## h2
- Since h1 is a linear equation, passing the same across the networks, collapses all layers to act like a single layer linear network. This looses capability to recognize complex patterns.
- So we need to add non-linearity before passing h1 to the next layer as input.
- Activation function is used to add non-linearity. In our model, we will use Sigmoiud as activation function
- σ is a non-linear function. This adds non-linearity to h1, which can then be passed to the next layer.
  <pre> a_h1 = σ(h1)</pre>
## h2, a_h2
<pre>h2 = w3 * i1 + w4 * i2 => a_h2 = σ(h2)
o1 = w5 * a_h1 + w6 * a_h2 => a_o1 = σ(o1)
o2 = w7 * a_h1 + w8 * a_h2 => a_o2 = σ(o2)</pre>
## Backward Propagation
- The goal of Backward propagation is to update the network's trainable parameters in such a way that the overall loss of the network is reduced.
- This target is to match or closely match the network predictions with the target values t1 & t2.
- So the values of a_o1 & a_o2 should be as close as possible to t1 & t2 respectively.
- The loss functions used to calculate the differnece between the predicted and the actual outputs is:
  <pre>E1 = ½ * (t1 - a_o1)^2
  E2 = ½ * (t1 - a_o1)^2
  E_Total = E1 + E2</pre>
- In order to mimise the loss ,we need to update the weights.
## Update the weights
In orde to update the weights, we need to find the rate of change of E_Total w.r.t to individual Weights. That is to identify how a small change in Wi will affect E_Total.
<pre>  Calculate ∂E_Total/∂Wi  ; Where i represent each of the weights in the network</pre>
<pre>For each of the weights, do
  Wi = Wi - ⴄ * ∂E_Total/∂Wi
  ⴄ is the learning rate. Helps to define how much more i can trim downor(or pull up) the updates, could be 1, 0.1, 0.01, 0.001 etc</pre>
## ∂E_Total/∂Wi
- Taking w5 as one of the weights
- <pre> ∂E_Total/∂w5 = ∂(E1 + E2)/∂w5
  Here, w5 has no impact on E2, so the derivative is constant, leading to
  ∂E_Total/∂w5 = ∂E1/∂w5</pre>
- w5 does not directly impact E1, but through many intermediates the rate at which w5 changes E1 (∂E1/∂W5), is dependent on how w5 changes o1, in turn how o1 changes a_o1 and how a_o1 changes E1. Hence we can calculate this using partial derivation:
  <pre>∂E_Total/∂w5 = ∂E1/∂w5 = (∂E1/∂a_o1) * (∂a_o1/∂o1) * (∂o1/∂w5)</pre>
## Calulation for forward pass and backward pass (∂E_Total/∂Wi) can be seen in the below image
![image](https://github.com/ShubhamVerma16/TSAI_ERA_Session6/assets/46774613/a30b3f3b-b8f8-41a8-8128-eae7761ae7ea)
Please refer S6_NN_BackPropagation.xlsx, for all the formulas included. All the above formula are key-ed in, so that we can check with different values. The file includes back-propagation updates for 68 steps. 
THe below images represent the loss curves for various learning rates:
### Learning rate = 0.1
![image](https://github.com/ShubhamVerma16/TSAI_ERA_Session6/assets/46774613/69c5660d-6d6a-4dbd-9641-8cb7924ed023)

### Learning rate = 0.2
![image](https://github.com/ShubhamVerma16/TSAI_ERA_Session6/assets/46774613/a25dddce-59b7-4387-8e36-3500cf56cc86)

### Learning rate = 0.5
![image](https://github.com/ShubhamVerma16/TSAI_ERA_Session6/assets/46774613/04f320c7-6030-4212-a57b-ec31be93ce06)

### Learning rate = 0.8
![image](https://github.com/ShubhamVerma16/TSAI_ERA_Session6/assets/46774613/88074bb7-65e4-4594-bf62-98ec8d43a6c1)

### Learning rate = 1.0
![image](https://github.com/ShubhamVerma16/TSAI_ERA_Session6/assets/46774613/42f09a07-4e39-4233-8e5b-3624c7f9d84d)

### Learning rate = 2.0
![image](https://github.com/ShubhamVerma16/TSAI_ERA_Session6/assets/46774613/3af82b74-a5dd-40b7-9e15-56de1acdcc7c)

As observed from the loss curves with changing learning rates, it shows how higher learning rate can help reach minima faster with longer strides.
#### NOTE: Higher learning rates and cause the model to get stuck on local minim. Hence, choosing the correct value of learning rates is important.









  
