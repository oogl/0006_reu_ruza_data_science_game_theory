# [Game Theory | Mixed strategy] Card game "Le Her"
**Number of players:** 2 (Dealer & Reciever)

**Number of cards:** 52 (ordinary deck)

**Order of value:** A, 2, 3, 4, 5, 6, 7, 8, 9, 10, J, Q, K 

**Game process:**

> Dealer gives a card from deck at random to a Reciever, and takes one himself; neither player sees the other's card. The main object is for each to obtain a higher card than his opponent. If the Reciever is not content with his card, he may compel the Dealer to change with him; but if the Dealer has a King, he is allowed to retain it. If the Dealer is not content with the card which he at first obtained, or which he has been compelled to take from the Reciever, he is allowed to change it for another taken out of the deck at random; but if the card he then draws is a King, he is not allowed to have it, but must keep the card which he held after the Reciever exercised his option. The two players then compare cards, and the player with the higher card wins. If the Dealer and Reciever have cards of the same calue, the Dealer wins.
>
> -- _Melvin Dresher "Games of Strategy. Theory and Applications"_

## Step 1. The heatmap of the Dealer's win rate depending on the strategies
Both players have the same strategies: to hold i-th (or j-th) card and above.

<img src="pictures/le_her_removing_strategies_0.png">

## Step 2. Removing dominated strategies
First, the Reciever will try to find the best strategy, removing dominated strategies (if every probability of the Dealer's win in one row is higher than in the other, it has to be removed as inefficient). Then the same the Dealer will do. If nessesary, the Reciever will try again, and so on.

### Step 2.1
<img src="pictures/le_her_removing_strategies_1.png">

### Step 2.2
<img src="pictures/le_her_removing_strategies_2.png">

### Step 2.3
<img src="pictures/le_her_removing_strategies_3.png">

## Step 3. Obtaining the optimal strategy
The cells left above shows us that the is no clear optimal strategy for both of the players. That means that they will need to have mixed strategies with probabilities of following each of the particular strategies:

The Reciever:
- to hold 7 and above
- to hold 8 and above

The Dealer:
- to hold 8 and above
- to hold 9 and above

Solving the 2x2 game, we can calculate such probabilities with the help of these **formulas**:

- The matrix of our probabilities:
$
\quad\quad
\begin{Vmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{Vmatrix}
$


- Reciever probabilities:
$
\quad\quad
p_{1} = \frac{a_{22} - a_{21}}{a_{11} + a_{22} - a_{21} - a_{12}}
\quad\quad
p_{2} = \frac{a_{11} - a_{12}}{a_{11} + a_{22} - a_{21} - a_{12}}
$


- Subcalc:
$
\quad\quad
v = \frac{a_{11} * a_{22} - a_{21} * a_{12}}{a_{11} + a_{22} - a_{21} - a_{12}}
$


- Dealer probabilities:
$
\quad\quad
q_{1} = \frac{v - a_{12}}{a_{11} - a_{12}}
\quad\quad
q_{2} = \frac{a_{11} - v}{a_{11} - a_{12}}
$

**OPTIMAL STRATEGIES:**
The Reciever:  0.625, 0.375
The Dealer:    0.375, 0.625

**THE PRICE OF THE GAME:**
The value for the Reciever:  0.4875
The value for the Dealer:    0.5125

**PROBABILITIES OF SUCCESS:**
The Reciever:  0.5125
The Dealer:    0.4875

## Step 4. Conclusion

>Applying the minimax principle, we can determine that optimal strategy for the Dealer dictates mixing his two strategies in the ratio of 3:5. Reciever's optimal strategy is ($5/8, 3/8$). Probability of success for the Dealer is ~0.4875 and therefore 0.5125 for the Reciever, an expectation (for the Dealer) of -0.025. Although it may appear that the advantage lies with the Dealer since he wins the ties, the reverse is true owing to the greater ability of Reciever to influence the game's outcome.
>
> -- _Richard Epstein "The Theory of Gambling and Statistical Logic."_
