# Developing a Neural Network Regression Model

## AIM
To develop a neural network regression model for the given dataset.

## THEORY
Regression problems involve predicting a continuous output variable based on input features. Traditional linear regression models often struggle with complex patterns in data. Neural networks, specifically feedforward neural networks, can capture these complex relationships by using multiple layers of neurons and activation functions. In this experiment, a neural network model is introduced with a single linear layer that learns the parameters weight and bias using gradient descent.

## Neural Network Model
Include the neural network model diagram.

## DESIGN STEPS
### STEP 1: Generate Dataset

Create input values  from 1 to 50 and add random noise to introduce variations in output values .

### STEP 2: Initialize the Neural Network Model

Define a simple linear regression model using torch.nn.Linear() and initialize weights and bias values randomly.

### STEP 3: Define Loss Function and Optimizer

Use Mean Squared Error (MSE) as the loss function and optimize using Stochastic Gradient Descent (SGD) with a learning rate of 0.001.

### STEP 4: Train the Model

Run the training process for 100 epochs, compute loss, update weights and bias using backpropagation.

### STEP 5: Plot the Loss Curve

Track the loss function values across epochs to visualize convergence.

### STEP 6: Visualize the Best-Fit Line

Plot the original dataset along with the learned linear model.

### STEP 7: Make Predictions

Use the trained model to predict  for a new input value .

## PROGRAM

### Name: Jerushlin Jose JB

### Register Number: 212222240039

```
import torch as t
import torch.nn as nn
import matplotlib.pyplot as plt

t.manual_seed(71)
X = t.linspace(1, 50, 50).reshape(-1, 1)
e = t.randint(-8, 9, (50, 1),dtype=t.float)
y = 2 * X + 1 + e

plt.scatter(X.numpy(), y.numpy(),color = 'purple')
plt.xlabel('X')
plt.ylabel('y')
plt.title('Generated Data for Linear REgression')
plt.show()

class Model(nn.Module):
  def __init__(self,in_features,out_features):
    super().__init__()
    self.linear = nn.Linear(in_features, out_features)

    def forward(self,x):
      return self.linear(x)

t.manual_seed(59)
model = Model(1,1)

initial_weight = model.linear.weight.item()
initial_bias = model.linear.bias.item()

print(f"Initial Weight: {initial_weight:.2f}")
print(f"Initial Bias: {initial_bias:.2f}")
print("Name: JERUSHLIN JOSE JB")
print("Register Number: 212222240039\n")
print(f'Initial Weight: {initial_weight:.8f}, Initial Bias: {initial_bias:.8f}\n')

loss_function = nn.MSELoss()
optimizer = t.optim.SGD(model.parameters(), lr = 0.001)

epochs = 100
losses = []
for epoch in range(1, epochs + 1):
    optimizer.zero_grad()
    y_pred = model(X)
    loss = loss_function(y_pred, y)
    losses.append(loss.item())

    loss.backward()
    optimizer.step()

print(f'epoch: {epoch:2}  loss: {loss.item():10.8f} '
      f'weight: {model.linear.weight.item():10.8f} '
      f'bias: {model.linear.bias.item():10.8f}')

plt.plot(range(epochs),losses,color='blue')
plt.ylabel('Loss')
plt.xlabel('Epochs')
plt.title('Loss Curve')
plt.show()

final_weight = model.linear.weight.item()
final_bias = model.linear.bias.item()
print("Name: JERUSHLIN JOSE JB")
print("Register Number: 212222240039\n")
print(f'Final Weight: {final_weight:.8f}, Final Bias: {final_bias:.8f}\n')

x1 = t.tensor([X.min().item(),X.max().item()])
y1 = x1*final_weigt + final_bias

plt.scatter(X.numpt(), y.numpy(),label = 'Original Data')
plt.plot(x1.numpy(), y1.numpy(), 'r','label = Best Fit Line')
plt.xlabel('X')
plt.ylabel('y')
plt.title('Trained Model: Best Fit Line')
plt.legend()
plt.show()

x_new = t.tensor([[120.0]])
y_new_pred = model(x_new).item()
print("Name: JERUSHLIN JOSE JB")
print("Register Number: 212222240039\n")
print(f"\nPrediction for x = 120:  {y_new_pred:.8f}")

```

### Dataset Information

![Screenshot 2025-04-17 081813](https://github.com/user-attachments/assets/6d24003b-67c0-4d21-a7b1-8f29d5ad61ce)

### OUTPUT
### Training Loss Vs Iteration Plot
![Screenshot 2025-04-17 081754](https://github.com/user-attachments/assets/252d14ff-ec3a-4270-9ed5-41b2f4a6aa09)
### Best Fit line plot
![Screenshot 2025-04-17 082130](https://github.com/user-attachments/assets/2f615acd-1227-4ec9-9c7b-2834ab44596c)

### New Sample Data Prediction
![Screenshot 2025-04-17 082121](https://github.com/user-attachments/assets/b5e70831-6be1-4398-9a9c-52695dd7c6c2)

## RESULT
Thus, a neural network regression model was successfully developed and trained using PyTorch.
