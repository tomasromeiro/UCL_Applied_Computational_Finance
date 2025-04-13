# Option Pricing via Finite Difference Methods  
**Course**: Applied Computational Finance
**Institution**: University College London (UCL)  

---

## Overview

This repository contains a single C++ file — `test_final.cpp` — that implements various finite difference methods to price options. The program was developed as part of the assessment for the Applied Computational Finance course and is designed to showcase proficiency in numerical methods, algorithm design, and computational finance.

The application implements multiple numerical schemes for solving the option pricing problem via backward-marching finite difference methods:
- **Explicit Scheme**
- **Fully Implicit Method**
- **Crank-Nicolson Technique**

Additionally, the program extends these methods to:
- **Price American Options**: An American option can be exercised any time prior to expiry. The code includes a function that adjusts the explicit scheme, enforcing the condition  
  \[
  U^{m-1}_n = \max\{\,U^{m-1}_n,\, P^{m-1}_n\}
  \]  
  where \(P(S,t)\) is the option payoff. Comment statements within the code discuss the impact of dividends on both call and put options.
- **Generalised Theta Method**: A function is provided that implements the theta-method — a generalised form of Crank-Nicolson — with a user-defined weight \(\theta \in [0,1]\). The code also demonstrates the special case:  
  \[
  \theta = \frac{1}{2} + \frac{1}{12} \sigma^2 \Delta t
  \]  
  with a detailed discussion in the comments regarding the significance of this choice.

---

## Key Features

- **Multiple Numerical Schemes**  
  Each method is encapsulated in its own clearly defined function. Users can choose the desired scheme via a switch statement at runtime.

- **American Option Pricing**  
  The code is augmented with a function that handles the early exercise feature of American options. It replaces the computed solution with the payoff when necessary, ensuring that the value always reflects the possibility of immediate exercise.

- **User Input and Validation**  
  All input data (e.g., today's stock price \(S_0\), strike \(E\), time to expiry \(T-t\), volatility \(\sigma\), and the risk-free interest rate \(r\)) are entered via the keyboard. An example provided in the assignment is:
  - Today's stock price \(S_0 = 100\)
  - Strike \(E = 100\)
  - Time to expiry \(T-t = 1\) year
  - Volatility \(\sigma = 20\%\)
  - Risk-free interest rate \(r = 5\%\)  
  Expected call and put prices for these parameters are approximately 10.45 and 5.57, respectively.

- **Modular Design in a Single File**  
  In accordance with the test instructions, all code is contained within a single C++ file. This structure facilitates straightforward submission and grading while ensuring compliance with exam rules (e.g., no function headers/source file splits).

---

## How to Compile and Run

1. **Compilation**  
   Use a C++ compiler (such as `g++`) to compile the code. For example:
   ```bash
   g++ -o option_pricing 24022849_test.cpp
