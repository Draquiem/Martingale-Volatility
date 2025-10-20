# Martingale-Volatility
This repo will go over the fundamental concepts of what Martingale is and how I am attempting to implement it in Volatility-Based Trading. This concept will directly link into an algo-project that I am working on that will utilize the Martingale DCA strategy to execute trades.


Martingale Strategy in Roulette/Expected Value of Martingale Strategy

  - Learn how Martingale Strategy will accumulate positive EV over time. This directly counters the House's edge, as long as you have the equity capacity to provide for the drawdowns.
  - Your EV becomes positive after one round of Martingale.
  - This strategy emphasizes success in the long run, if you are expecting to make money with a few trades, you WILL most likely lose money.

Losing Streak Devastation in the Martingale Strategy
  - Note that total amount wager = 2^n.
    - This means that loss is exponential, so after 10 losses you will take your initial bet (b)*2047, after 20 losses it becomes over 2 million.
  - If you do not survive the short run, you WILL liquidate.

Simulation #1
  - Simulation will play until we win.
  - Note that eventually you will always end with a positive EV.
    - ALSO, note that as soon as you win, your capital is automatically positive, disregard of how many losses you have. Cumulative Equity Curve
  - You can visually see the accumulated wealth over time. | This is what it means to have a positive EV. Bet Size Over Time
  - Notice how the bet size spikes over time.
  - You are risking a significant amount of capital to recuperate your losses and also to regain that initial bet sizing.

Volatility Mean Reversion
  - We don't have a way to 50/50 the stock market
  - Ornstein-Uhlenbeck process can fundamentally be used for both rates and/or volatility, here I am just showing the process itself as a stochiastic differential equation.
  - Once simulated, it will provide a path over time with a mean-reversion level.
    - If you run this on your editor, you will notice that each time this simulation is ran, the path is different.
    - HOWEVER, path will always retrace towards the mean-reversion level, we can see processes in the financial market that emulates this behavior: VIX.

Real VIX Date and Mean Reversion
  - We can see that during these spikes, it always revert back to the mean lvels
  - One strategy can be... if volatility seems to always revert back to the mean, and if the mean is at a certain level, we can transact trades that will trend towards the direction of these means.

Implementation of Martingale
  - Simulation of using this strategy in tandem with the Mean Reversion to transact specific trades.
  - This provides a CLEAR positive EV and accumulation of wealth.
  - Notice that your max exposure is higher than your final capital, this is sort of a nightmare for your sharpe ratio but it's okay because we ball (but more like anti-ball because we are going to have to massively scale down so we don't lose all our monies).
