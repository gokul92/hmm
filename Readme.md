# Hidden-Markov-Model
Hidden Markov Model with files to extract open, high, low and close prices, convert data to discrete states and learn emission and transition probability matrices from time series data to predict future states.  

The get_data_class.py file contains a class that reads a file, extracts the open, high, low and close prices (hereafter called ohlc prices).
It also has functions that can extract necessary information from the file at will.

The get_states.py file contains a function that creates two states for the observation variable/output variable - denoted by x.
These states are created by analysing the relationship between the ohlc prices.
Overall, there are two states that are possible. 
State 7 means that the closing price for that time interval is lower than the opening price.
State 8 means that the closing price for that time interval is higher than the opening price.

The hmm.py file is the main file that contains the hidden markov model implementation.
It first creates the object that takes as input the filename which points to the file where the data is stored.

Once the data is extracted, the transition probability matrix A and emission probability matrix B are initialized appropriately.

The first step in the algorithm is the expectation step.
The expectation step uses the forward algorithm to compute parameter alpha and backward algorithm to compute beta.
The alpha and beta computed are such that they prevent underflow to very low values. This is done by scaling them at every iteration.

The next step is the maximization step.
The maximization step calculates the initial probability vector pi, the transition probability matrix A and emission probability matrix B
based on the values of alpha and beta computed in the expectation step.

The expectation and maximization steps are looped till convergence to an arbitrary level is reached. Convergence is determined based on difference between successive values. 

The learned parameters are used to predict the probability of states in the next time step. This is the expectation step. 
