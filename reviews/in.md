#  Interaction Networks for Learning about Objects, Relations and Physics

**Problem**

Simulating a physics engine using learnable deep neural networks.

**Summary and Key Points**

The authors present a learnable framework called Interaction Network (IN) for modeling physical interactions between multiple objects and their environment. The object-specific dynamics and inter-object relations are explicitly modeled separately to make IN generalizable across multiple objects and varied relations. Some of the key points are:

1. IN takes in a attributed directed graph G as inputs whose nodes represents the multiple objects and edges represent the relations between them.

2. IN is modeled as a learnable framework with standard deep learning building blocks, matrix operations etc. The model is essentially comprised of aggregation functions (no parameters), the object-centric function *f<sub>o* (learnable) and the relation function *f<sub>r* (learnable). When applied sequentially (*f<sub>r* -> aggregate -> *f<sub>o* -> aggregate), IN is able to predict the next state of the objects. This strategy can be easily extended to infer abstract properties by adding another aggregation and learnable function. 

3. Both *f<sub>r* and *f<sub>o* are modeled as MLPs that are applied individually to every object-object-relation tuple and object respectively. The weights are shared across all relations and objects. The best model architectures were selected through grid search. The final output (by *f<sub>o*) is of length 2 (per object), depicting x and y velocities. 

4. IN is evaluated on 3 physical reasoning tasks - n-bodies interaction, collision of bouncing balls, and string/mass/spring systems. A custom physics engine is used to generate training data. Optimization is done over the MSE of these velocities. 

**Results**

1. Compared to simple baselines, IN showed significantly lower error rates when predicting future object states in all the tasks. Note that the training was done only for single steps, so it's impressive that errors are not getting compounded over lot of time steps.

2. IN is also able to deduce abstract system properties like potential energy by extending their proposed approach.

3. IN also shows good results for experiment settings that it wasn't trained for, like using different number of balls at test time compared to fixed number at train time. This can be attributed to its delineation of object and relation functions.

**Notes**

1. Authors could have talked about memory and time complexities as we make the system more complex.

2. It's a good starting point to model the intuitive physics engine that humans have.

