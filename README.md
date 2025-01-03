# Drug efficiency and Gradient Descent optimizers

This repository we will explore how different optimization algorithms of Gradient Descent ,the backbone of Machine Learning and Neural Networks, can be applied to determine the optimal drug dosage using the Hill equation.

We will work with artificial data, to simulate the relationship between drug dosage and effectiveness.
However, the optimization techniques and algorithms used here are the same foundational methods used in most state-of-the-art neural networks, allowing us to observe the way they work, in a simplified context.
---

###  Hill Equation
The function we will work with, is the Hill Equation.

E(D) = (E_max * D^n) / (K_m^n + D^n)

The Hill equation is a mathematical model used to describe the relationship between a drug's concentration and its effectiveness, commonly applied in pharmacology to study dose-response curves.

The Hill Equation depends on the following variables: 
 - Concentration (𝐷): The amount of drug being used. The higher the concentration, the more noticeable its effect (up to a limit).
 - EC50: The amount of drug needed to get halfway to the best possible effect. It tells us how strong the drug is.
 - Maximum Effect (𝐸max): The highest level of effectiveness the drug can achieve.
 - Hill Coefficient (𝑛): Controls how steeply the effect increases as more drug is added.

 In our example, we extend the basic Hill equation by introducing two additional terms: a toxicity term and an oscillation term. These modifications make the function more realistic and challenging to optimize, mimicking complex real-world scenarios. By doing so, we aim to test how well gradient descent and other optimization techniques perform, especially when faced with local minima and maxima.

### ** Adding Complexity: Toxicity Term**
We introduce a **toxicity term** to penalize high doses:

Toxicity Term = (D^2) / T

Where:
- (D): Drug dose.
- (T): Toxicity scaling factor, determining how quickly the penalty increases.

This term represents the harmful effects of taking too much of the drug, reducing effectiveness at higher doses.

---

### ** Adding Complexity: Oscillation Term**
We also include an **oscillation term** to mimic variability in drug response:

Oscillation Term = A * sin((2 * π * D) / P)

Where:
- (A): Amplitude, controlling the size of the oscillations.
- (P): Period, determining how frequently the oscillations occur.

This term introduces periodic fluctuations in effectiveness, simulating biological variability or external factors.

### **4. Final Effectiveness Function**
Combining the Hill equation with the toxicity and oscillation terms, the final effectiveness function is:

E(D) = (E_max * D^n) / (K_m^n + D^n) - (D^2 / T) + A * sin((2 * π * D) / P)


Where:
- (E(D)): The overall effectiveness as a function of dose (\(D\)).
- (E_max): Maximum possible effect.
- (K_m): Dose at half-maximal effectiveness.
- (n): Hill coefficient.
- (T): Toxicity scaling factor.
- (A): Amplitude of oscillations.
- (P): Period of oscillations.

---

### **Why Add These Terms?**
By including toxicity and oscillations:
1. The optimization problem becomes more realistic, resembling real-world challenges in pharmacology and biology.
2. Local minima and maxima in the effectiveness function provide a complex landscape for gradient-based optimization algorithms to navigate.
3. It demonstrates how optimizers perform under complex conditions, providing valuable insights into their behavior.

For the purpose of this project, all terms will remain fixed, except for the **drug dose (\(D\))**, which we will optimize to find its optimal value. This allows us to focus solely on determining the most effective dose while assuming the other parameters are stable and pre-defined.

### The Gradient Descent Optimization Algorithms We Will Explore:
- **Momentum:** Builds up speed by adding some of the previous step’s direction to the current one, helping to move faster and avoid getting stuck in small dips.  
- **Adagrad:** Adjusts the step size for each parameter based on how much it has changed in the past. Parameters that have already made large changes take smaller steps, while those that haven’t changed much take larger steps, making it useful for handling uneven data.  
- **RMSprop:** Keeps track of how steep the changes are for each parameter and adjusts the step size accordingly, ensuring the learning stays steady and controlled.  
- **Adam:** Combines the benefits of Momentum and RMSprop, moving quickly when it’s safe and slowing down when precision is needed, making it reliable for many tasks.  

### Understanding the Loss Function Through Dose Range Plotting

In our project, to better understand the **loss** and **effectiveness** functions before applying optimization algorithms, we will:

- **Take a Range of Doses:** Consider various drug doses within a specific range.
- **Plot the Loss Function:** Calculate and visualize the loss (negative effectiveness) for each dose.

![efecitvenessdose](https://github.com/user-attachments/assets/d6db59d3-e7d8-4c80-9635-c8346647dd27)
![lossdose](https://github.com/user-attachments/assets/01d9b845-2477-44fd-9b39-82af6de9bb7f)


Let's start coding and see how we can find the optimal dose!


 

## Contact

**Konstantinos Tsolakidis**  
Machine Learning Engineer  
Hatzakis Lab - University of Copenhagen  
📧 kontsolakidis25@gmail.com  
