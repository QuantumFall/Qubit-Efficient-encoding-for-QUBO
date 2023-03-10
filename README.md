# Qubit-Efficient-encoding-for-QUBO
Qubit efficient encoding scheme for QUBO problems. Allows for multiple choices of Ancillas. Uses Qiskit and Scipy optimizer, and collects data in parallel.

Just download all the files and necessary packages (scipy, qiskit, multiprocessing, etc) and it should be ready to run.

`NASGD.py` contains all the necessary functions to calculate the objective value (and more, such as computing gradients, ADAM optimizer, and classical simulations). Requires Qiskit.

`Multi-Ancilla ScipyOpt Jac inf mes.py` is the optimization file that uses the gradient based SLSQP and calls from `NASGD.py` to obtain the Jacobian.

`Multi-Ancilla ScipyOpt inf mes.py` uses COBYLA, a gradient free method.

`Multi-ancilla Pennylane.py` is a simpler (and trimmed down) version of the code written in PennyLane. 
Calculating the cost function is faster, and gradients can be computed automatically using autograd to be used with Pennylane's built-in optimizers. 
Statevector and finite sampling used to estimate the objective function (and its gradients) can also be used without having to rewrite chunks of code.

A randomly generated 64 variable problem is given as an example. 

 - Using minimal encoding, only 1 + log(64) = 7 qubits are needed.

 - Using 2-body encoding, only 2 + log(64/2) = 7 qubits are needed.

 - Using 4-body encoding, only 4 + log(64/4) = 8 qubits are needed.



Data collection is done in parallel and saves to a dictionary which can be loaded later and plotted.




