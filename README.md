# POTW-IITBHU-Quant
This repository includes the solutions to Problem of The Week by Quant Club of IIT BHU
<b>
Author - Abhinava Kalita
Language used - Python
</b>

<b><u>Problem 1 (Ding and Gukesh)</u></b><br>
To solve the problem we use total probability theorem. Firstly I've made two matrices G and D that contain the transition probabilities of the state of the board after Gukesh and Ding play a move respectively. The percentages are converted to fractions. 
<br>
The state of the board is 3 initially. It is Gukesh's turn. We declare a 1D array called State that will store the value of probability of the state of the board being 1/2/3/4/5 at index numbers 0,1,2,3,4 respectively. The probability of board being at State 1 after Gukesh's move = transition probability(state 3 to 1) in matrix G. This value is stored in State[0]. Similarly transition probability(state 3 to 2) in matrix G {which will be 3rd row 2nd column} will be stored in State[1] and so on...We notice that the array State equals the third row of matrix G.
<br>
Next, Ding plays a move. The probability of State being 1 = [probability that state was 1 {i.e. State[0]} * transition probability(state 1 to 1) in matrix D {row1 col1}] + <br>
[probability that state was  2 {i.e. State[1]} * transition probability(state 2 to 1) in matrix D {row2 col1}] +<br>
[probability that state was  3 {i.e. State[2]} * transition probability(state 3 to 1) in matrix D {row3 col1}] +<br>
[probability that state was  4 {i.e. State[3]} * transition probability(state 4 to 1) in matrix D {row4 col1}] +<br>
[probability that state was  5 {i.e. State[4]} * transition probability(state 5 to 1) in matrix D {row5 col1}] +<br>
This is total probability theoream. Similarly Probabilities for states 2,3,4,5 is calculated and stored in the array State.<br>
We notice that the i-th value of the updated array State equals the matrix multiplication of the previous array State and column i of D.<br>
We also notice that this is true for all the subsequent moves (instead of matrix D it is G for Gukesh's move and D for Ding's moves)
<br>
Therefore we run a loop to account for the 10 moves that each player played and after total of 40(=30+10) moves we now know the probability of the board being in each of the states. Now if  it is State 1, Gukesh wins with 90% probability. if it is state 2 Gukesh wins with 70% probability. Otherwise gukesh never wins. Therefore probability of Gukesh winning = probability of State 1 {i.e. State[0]} * 0.9 + probability of State 2 {i.e. State[1]} * 0.7 by total probability thm.<br>
Similarly we calculate probability of draw and Ding winning.


