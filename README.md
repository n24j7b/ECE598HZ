java c
ECE598HZ: Advanced Topics in Machine Learning and Formal Methods 
Fall 2024 
Homework 1 
Due Sep 23 11:59pm CT
Typeset your solutions using LATEX, create a single zip file including your solutions (in a single
PDF file), your code, and instructions to run your code. Name your zip file as netid-598-F24 . zip and upload this file through Canvas.
Problem 1: Boolean Satisfiability Problem and DPLL (30pts) Suppose you are working as an intern in an e-commerce company. You are building a machine learning model to predict whether a customer will buy a product based on a very large datasest with six features: A,B,C,D,E, and F. However, due to computational constraints, your manager asks you to only use three features in your final model.
You have the following information about the features:
• If feature A is selected, theneither feature B or feature C must also be selected.
• Feature C and feature D cannot be selected together.
• If feature E is selected, then feature F must not be selected.
• At least one of features B,C, or D must be selected.
• If feature F is selected, theneither feature A or feature E must also be selected.
1. Formulate this feature selection problem as a Boolean satisfiability problem. (15pts)
2. Use the DPLL algorithm to find a satisfying assignment that represents a valid selection of three features. If such an assignment does not exist, report that the solution does not exist. Show your steps. (15pts)
Problem 2: 4-SAT, 3-SAT, and 2-SAT problems (20pts) 
1. A 4-SAT problem inCNF form. has 4 literals in each clause. An example 4-SAT problem is given below:
φ4-SAT  := (x1∨ x2∨ x3∨ x4) Λ (¬x1∨ ¬x2∨ x3∨ ¬x4) Λ (x1∨ ¬x2∨ ¬x3∨ x4)Convert this 4-SAT problem to an equivalent 3-SAT problem, i.e., find a 3-SAT formula φ3-SAT which is satisfiable if and only if φ4-SAT is satisfiable (hint: you may introduce additional variables) (5 pts)2. Discussion how to convert any 4-SAT problem to a 3-SAT problem. If the 4-SAT problem has m variables and n clauses, what is the worst-case number of variables and clauses in your converted 3-SAT problem? (5pts)3. Convert the following 3-SAT problem to a 2-SAT problem. You may have an arbitrary number of clauses in your 2-SAT problem, but don’t introduce any new variables (use x1, x2, x3  and their negations only in each clause). If such a conversion is not possible, provide a proof of the impos- sibility. (10pts)
ϕ3  := (x1V x2V x3)
Problem 3: SMT and Machine Learning Coding Problem (50pts) 
You are given a set of points labeled as class +1 or class -1.  Your task is to find a small neural network with ReLU activation that classifies the points correctly.
The network has two input features x1  and x2, one hidden layer with ReLU activation function, and a single output y. Mathematically, it is defined as:
h1 = ReLU(w11 · x1 + w12 · x2 + b1)                          (1)
h2 = ReLU(w21 · x1 + w22 · x2 + b2)                          (2)
y = v1 · h1 + v2 · h2 + c                                            (3)Here w11 , w12 , w21 , w22 are the weights of the first linear layer, v1 , v2  are the weights of the second linear layer. b1 , b2 are the biases of the first linear layer, and c is the bias of the second linear layer. The network classifies the input as +1 when y > 0, and -1 when y < 0.
You are given two sets of training data points, presented in Table 1 and Table 2.Point x1 x2 Label P1 1 1 +1 P2 1 -1 -1 P3 -1 1 -1 P4 -1 -1 代 写ECE598HZ: Advanced Topics in Machine Learning and Formal Methods Fall 2024 Homework 1Python
代做程序编程语言+1 
Table 1: Training set 1
In this problem, we will consider solving the neural network using an SMT formulation as well as using a regular machine learning approach (e.g., gradient descent). Complete the following tasks:
1. First, consider only the points P1 and P2 from training set 1.  Write the problem of finding one solution of neural network parameters w11 , w12 , w21 , w22 , v1 , v2 ,c to classify P1 and P2
Point x1 x2 Label P1 0.1 0.1 +1 P2 0.2 0.1 -1 P3 0.3 0.2 +1 P4 0.4 0.3 -1 P5 -0.1 -0.1 +1 P6 -0.2 -0.1 -1 P7 -0.3 -0.2 +1 P8 -0.4 -0.3 -1 P9 0.5 0.4 +1 P10 -0.5 -0.4 -1 

Table 2: Training set 2correctly as an SMT problem. You can use nonlinear functions such as ReLU in your formu- lation. (Hint: think the process of finding neural network parameters that classify P1 and P2 correctly as finding a satisfiable solution of an SMT formula) (10pts)
2. Now consider all points in each training set. Write a Python program to call the SMT solver Z3. For each training set, use Z3 to solve the network parameters such that all points in each training set are classified correctly. Report that no solution exists if Z3 reportsUNSAT for the SMT problem. A program template (z3nn template.py) has been given to you. (15pts)
3. Using any machine learning framework (such as PyTorch), create the neural network defined in this problem (equations (1) to (3)). If you obtained a solution for w11 , w12 , w21 , w22 , v1 , v2 , c in the previous task (Z3 does not report UNSAT), plug these parameters in your network and report the training set accuracy on the corresponding training set. (5pts)
4. Train two networks for the two training sets using regular cross-entropy loss for classifi- cation and optimize the loss with gradient descent (any gradient-based optimizer, such as Adam, can be used). Initialize your neural networks randomly. Tune hyperparameters with your best effort. Plot loss function values vs. the number of optimization iterations. Can the training loss be reduced to 0 for each dataset? Report the training accuracy on the two networks you obtained on the two training sets, respectively. (10pts)
5. Based on your experience when solving tasks 2 and 4, discuss the strengths and weaknesses of solving a neural network using Z3 vs. typical machine learning approaches such as gra- dient descent. (10pts)
For tasks 2,3 and 4, please submit your programs and also a README file containing instructions to run your code. Be sure that you have good instructions.
Resources: First install Z3 in your computer. This is a very quick process. On Linux and MacOS pip  install  z3-solver does it in less than a minute (using a virutal Python environment like
venv or condais suggested.). You can find more instructions about z3 from:
https://github.com/Z3Prover/z3. There is a lot of help available online for installation related issues. Some tutorials that you may find useful are listed below:
• https://ericpony.github.io/z3py-tutorial/guide-examples.htm 
• https://github.com/philzook58/z3_tutorial/blob/master/Z3%20Tutorial. ipynb 
If you need a tutorial on PyTorch for training neural networks, you can refer to these tutorials:
• https://weiliu2k.github.io/CITS4012/pytorch/nn_oop.html 
• https://gist.github.com/santi-pdp/d0e9002afe74db04aa5bbff6d076e8fe 
• https://courses.cs.washington.edu/courses/cse446/18wi/sections/section8/ XOR-Pytorch.html 







         
加QQ：99515681  WX：codinghelp
