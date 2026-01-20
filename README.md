# Compounding Problem with Fixed Transaction Costs

TODO INTRO

## The Problem

Fix the nominal interest rate $r \in \mathbb{R}_{\ge 0}$ and the compounding cost $c \in \mathbb{R}_{\ge 0}$.

Find a best compounding strategy function

$$
s: \mathbb{R} \rightarrow \mathbb{R}_{\ge 0}
$$

which maps the current principal $p \in \mathbb{R}$ to a waiting time $s(p) \in \mathbb{R}_{\ge 0}$ until the next compounding action.

$s$ is best if it eventually dominates any alternative strategy in terminal principal: for any other compounding strategy function $s_\star$, there exists a horizon threshold $t_\ast$ such that $\forall t > t_\ast \in \mathbb{R}_{\ge 0}$:

$$
y_s(t, 1) \ge y_{s_\star}(t, 1)
$$

where $y_s(t, p)$ denotes the terminal principal when starting from principal $p$ with remaining time $t$ and following strategy $s$. At each step, the strategy chooses a waiting time $w = s(p)$; if $w$ fits within the remaining horizon, you wait $w$ time units and then update the principal by applying the compounding operation. If $w$ does not fit, no further actions are taken and the process terminates.

$$
y_s(t, p) =
\begin{cases}
y_s(t - w, p + prw - c) & 0 \le w = s(p) \le t \\
p & \text{else}
\end{cases}
$$

# The Solution

TODO

$$
s(\frac{c}{p+prs(p)-c})=s(p)-\frac{c}{pr}
$$
