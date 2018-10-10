
## Assignment
#### 2A: [REFERENCE](https://www.analyticsvidhya.com/blog/2017/05/neural-network-from-scratch-in-python-and-r/) change all the random values and redo the assignment in markdown format.

___
### Visualization of steps for Neural Network methodology

Note:
- For good visualization images, I have rounded decimal positions at 2 or 3 positions
- Yellow filled cells represent current active cell
- Orange cell represents the input used to populate values of current cell
___
#### Step 0: Read input and output

| X    |      |      |      | wh   |      |      | bh   |      |      | hidden_layer_input |      |      | hidden_layer_activations |      |      | wout | bout | output | y    | E    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------ | ---- | ---- | ------------------------ | ---- | ---- | ---- | ---- | ------ | ---- | ---- |
| 1    | 0    | 1    | 0    |      |      |      |      |      |      |                    |      |      |                          |      |      |      |      |        | 1    |      |
| 1    | 0    | 1    | 1    |      |      |      |      |      |      |                    |      |      |                          |      |      |      |      |        | 1    |      |
| 0    | 1    | 0    | 1    |      |      |      |      |      |      |                    |      |      |                          |      |      |      |      |        | 0    |      |
___
#### **Step 1:** Initialize weights and biases with random values (There are methods to initialize weights and biases but for now initialize with random values)

| X    |      |      |      | wh   |      |      | bh   |      |      | hidden_layer_input |      |      | hidden_layer_activations |      |      | wout | bout | output | y    | E    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------ | ---- | ---- | ------------------------ | ---- | ---- | ---- | ---- | ------ | ---- | ---- |
| 1    | 0    | 1    | 0    | 0.39 | 0.81 | 0.67 | 0.55 | 0.86 | 0.13 |                    |      |      |                          |      |      | 0.33 | 0.77 |        | 1    |      |
| 1    | 0    | 1    | 1    | 0.11 | 0.83 | 0.55 |      |      |      |                    |      |      |                          |      |      | 0.21 |      |        | 1    |      |
| 0    | 1    | 0    | 1    | 0.59 | 0.23 | 0.45 |      |      |      |                    |      |      |                          |      |      | 0.24 |      |        | 0    |      |
|      |      |      |      | 0.91 | 0.22 | 0.48 |      |      |      |                    |      |      |                          |      |      |      |      |        |      |      |
___
#### **Step 2:** Calculate hidden layer input:

*hidden_layer_input= matrix_dot_product(X,wh) + bh*

| X    |      |      |      | wh   |      |      | bh   |      |      | hidden_layer_input |      |      | hidden_layer_activations |      |      | wout | bout | output | y    | E    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------ | ---- | ---- | ------------------------ | ---- | ---- | ---- | ---- | ------ | ---- | ---- |
| 1    | 0    | 1    | 0    | 0.39 | 0.81 | 0.67 | 0.55 | 0.86 | 0.13 | 1.53               | 1.9  | 1.25 |                          |      |      | 0.33 | 0.77 |        | 1    |      |
| 1    | 0    | 1    | 1    | 0.11 | 0.83 | 0.55 |      |      |      | 2.44               | 2.12 | 1.73 |                          |      |      | 0.21 |      |        | 1    |      |
| 0    | 1    | 0    | 1    | 0.59 | 0.23 | 0.45 |      |      |      | 1.57               | 1.91 | 1.16 |                          |      |      | 0.24 |      |        | 0    |      |
|      |      |      |      | 0.91 | 0.22 | 0.48 |      |      |      |                    |      |      |                          |      |      |      |      |        |      |      |
___
#### **Step 3:** Perform non-linear transformation on hidden linear input

*hiddenlayer_activations = sigmoid(hidden_layer_input)*

| X    |      |      |      | wh   |      |      | bh   |      |      | hidden_layer_input |      |      | hidden_layer_activations |      |      | wout | bout | output | y    | E    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------ | ---- | ---- | ------------------------ | ---- | ---- | ---- | ---- | ------ | ---- | ---- |
| 1    | 0    | 1    | 0    | 0.39 | 0.81 | 0.67 | 0.55 | 0.86 | 0.13 | 1.53               | 1.9  | 1.25 | 0.82                     | 0.87 | 0.78 | 0.33 | 0.77 |        | 1    |      |
| 1    | 0    | 1    | 1    | 0.11 | 0.83 | 0.55 |      |      |      | 2.44               | 2.12 | 1.73 | 0.92                     | 0.89 | 0.85 | 0.21 |      |        | 1    |      |
| 0    | 1    | 0    | 1    | 0.59 | 0.23 | 0.45 |      |      |      | 1.57               | 1.91 | 1.16 | 0.83                     | 0.87 | 0.76 | 0.24 |      |        | 0    |      |
|      |      |      |      | 0.91 | 0.22 | 0.48 |      |      |      |                    |      |      |                          |      |      |      |      |        |      |      |

___

#### **Step 4:** Perform linear and non-linear transformation of hidden layer activation at output layer

output_layer_input = matrix_dot_product (hiddenlayer_activations * wout ) + bout
output = sigmoid(output_layer_input)

| X    |      |      |      | wh   |      |      | bh   |      |      | hidden_layer_input |      |      | hidden_layer_activations |      |      | wout | bout | output | y    | E    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------ | ---- | ---- | ------------------------ | ---- | ---- | ---- | ---- | ------ | ---- | ---- |
| 1    | 0    | 1    | 0    | 0.39 | 0.81 | 0.67 | 0.55 | 0.86 | 0.13 | 1.53               | 1.9  | 1.25 | 0.82                     | 0.87 | 0.78 | 0.33 | 0.77 | 0.80   | 1    |      |
| 1    | 0    | 1    | 1    | 0.11 | 0.83 | 0.55 |      |      |      | 2.44               | 2.12 | 1.73 | 0.92                     | 0.89 | 0.85 | 0.21 |      | 0.81   | 1    |      |
| 0    | 1    | 0    | 1    | 0.59 | 0.23 | 0.45 |      |      |      | 1.57               | 1.91 | 1.16 | 0.83                     | 0.87 | 0.76 | 0.24 |      | 0.80   | 0    |      |
|      |      |      |      | 0.91 | 0.22 | 0.48 |      |      |      |                    |      |      |                          |      |      |      |      |        |      |      |

------

#### **Step 5:** Calculate gradient of Error(E) at output layer

*E = y-output*

| X    |      |      |      | wh   |      |      | bh   |      |      | hidden_layer_input |      |      | hidden_layer_activations |      |      | wout | bout | output | y    | E     |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------ | ---- | ---- | ------------------------ | ---- | ---- | ---- | ---- | ------ | ---- | ----- |
| 1    | 0    | 1    | 0    | 0.39 | 0.81 | 0.67 | 0.55 | 0.86 | 0.13 | 1.53               | 1.9  | 1.25 | 0.82                     | 0.87 | 0.78 | 0.33 | 0.77 | 0.80   | 1    | 0.20  |
| 1    | 0    | 1    | 1    | 0.11 | 0.83 | 0.55 |      |      |      | 2.44               | 2.12 | 1.73 | 0.92                     | 0.89 | 0.85 | 0.21 |      | 0.81   | 1    | 0.19  |
| 0    | 1    | 0    | 1    | 0.59 | 0.23 | 0.45 |      |      |      | 1.57               | 1.91 | 1.16 | 0.83                     | 0.87 | 0.76 | 0.24 |      | 0.80   | 0    | -0.80 |
|      |      |      |      | 0.91 | 0.22 | 0.48 |      |      |      |                    |      |      |                          |      |      |      |      |        |      |       |

------

#### **Step 6:** Compute slope at output and hidden layer

*Slope_output_layer= derivatives_sigmoid(output)*
*Slope_hidden_layer = derivatives_sigmoid(hiddenlayer_activations)*

| Slope Hidden Layer |      |      |
| ------------------ | ---- | ---- |
| 0.15               | 0.11 | 0.17 |
| 0.07               | 0.10 | 0.13 |
| 0.14               | 0.11 | 0.18 |

| Slope O/P |
| --------- |
| 0.16      |
| 0.15      |
| 0.16      |

------

#### **Step 7:** Compute delta at output layer

*d_output = E \* slope_output_layer*lr*

| delta output |
| ------------ |
| 0.03         |
| 0.03         |
| -0.13        |

------

#### **Step 8:** Calculate Error at hidden layer

*Error_at_hidden_layer = matrix_dot_product(d_output, wout.Transpose)*

| Error at hidden layer |        |        |
| --------------------- | ------ | ------ |
| 0.009                 | 0.008  | 0.007  |
| 0.009                 | 0.007  | 0.007  |
| -0.038                | -0.032 | -0.029 |

------

#### **Step 9:** Compute delta at hidden layer

*d_hiddenlayer = Error_at_hidden_layer \* slope_hidden_layer*

| delta hidden layer |        |        |
| ------------------ | ------ | ------ |
| 0.001              | 0.001  | 0.001  |
| 0.001              | 0.001  | 0.001  |
| -0.005             | -0.004 | -0.005 |

------

#### **Step 10:** Update weight at both output and hidden layer

wout = wout + matrix_dot_product(hiddenlayer_activations.Transpose, d_output) * learning_rate
wh =  wh+ matrix_dot_product(X.Transpose,d_hiddenlayer) * learning_rate

| X    |      |      |      | wh      |         |         | bh   |      |      | hidden_layer_input |      |      | hidden_layer_activations |      |      | wout | bout | output | y    | E     |
| ---- | ---- | ---- | ---- | ------- | ------- | ------- | ---- | ---- | ---- | ------------------ | ---- | ---- | ------------------------ | ---- | ---- | ---- | ---- | ------ | ---- | ----- |
| 1    | 0    | 1    | 0    | 0.39020 | 0.81016 | 0.67021 | 0.55 | 0.86 | 0.13 | 1.53               | 1.9  | 1.25 | 0.82                     | 0.87 | 0.78 | 0.32 | 0.77 | 0.80   | 1    | 0.20  |
| 1    | 0    | 1    | 1    | 0.10946 | 0.82964 | 0.54947 |      |      |      | 2.44               | 2.12 | 1.73 | 0.92                     | 0.89 | 0.85 | 0.20 |      | 0.81   | 1    | 0.19  |
| 0    | 1    | 0    | 1    | 0.59020 | 0.23016 | 0.45021 |      |      |      | 1.57               | 1.91 | 1.16 | 0.83                     | 0.87 | 0.76 | 0.24 |      | 0.80   | 0    | -0.80 |
|      |      |      |      | 0.90952 | 0.21971 | 0.47955 |      |      |      |                    |      |      |                          |      |      |      |      |        |      |       |

------

#### Step 11: Update biases at both output and hidden layer

*bh = bh + sum(d_hiddenlayer, axis=0) \* learning_rate*
*bout = bout + sum(d_output, axis=0) \* learning_rate*

| X    |      |      |      | wh      |         |         | bh   |      |      | hidden_layer_input |      |      | hidden_layer_activations |      |      | wout | bout | output | y    | E     |
| ---- | ---- | ---- | ---- | ------- | ------- | ------- | ---- | ---- | ---- | ------------------ | ---- | ---- | ------------------------ | ---- | ---- | ---- | ---- | ------ | ---- | ----- |
| 1    | 0    | 1    | 0    | 0.39020 | 0.81016 | 0.67021 | 0.55 | 0.86 | 0.13 | 1.53               | 1.9  | 1.25 | 0.82                     | 0.87 | 0.78 | 0.32 | 0.76 | 0.80   | 1    | 0.20  |
| 1    | 0    | 1    | 1    | 0.10946 | 0.82964 | 0.54947 |      |      |      | 2.44               | 2.12 | 1.73 | 0.92                     | 0.89 | 0.85 | 0.20 |      | 0.81   | 1    | 0.19  |
| 0    | 1    | 0    | 1    | 0.59020 | 0.23016 | 0.45021 |      |      |      | 1.57               | 1.91 | 1.16 | 0.83                     | 0.87 | 0.76 | 0.24 |      | 0.80   | 0    | -0.80 |
|      |      |      |      | 0.90952 | 0.21971 | 0.47955 |      |      |      |                    |      |      |                          |      |      |      |      |        |      |       |
