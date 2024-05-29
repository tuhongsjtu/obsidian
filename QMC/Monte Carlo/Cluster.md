# Wolff-Cluster

AFM??

For
$$
\mathcal{H} = \sum_{\langle ij \rangle} -J_{ij} \sigma_{i} \sigma_{j}.
$$
All we need to do is just change the add probability $P_{\text{add}}$ from $1 - e^{-2\beta J}$ to
$$
P_{\text{add}} = 1 - e^{-2\beta J_{ij}}.
$$

# Geometry Cluster
The proof is similar with Wolff-Cluster algorithm. Consider two configurations $\mu$ and $\nu$, we have
$$
\frac{g_{\mu \rightarrow \nu}}{g_{\nu \rightarrow \mu}} \frac{A_{\mu \rightarrow \nu}}{A_{\nu \rightarrow \mu}} = e^{-\beta(E_{\nu} - E_{\mu})}.
$$
In geometric cluster algorithm, two clusters are formed simultaneously by exchanging spins. In the process $\mu \rightarrow \nu$, there are two kinds of boundary: $\Delta_{ik} \gt 0$ and $\Delta_{ik} \le 0$, where $\Delta_{ik}$ is
$$
\Delta_{ik} = \beta J (s_{i}s_{k} + s_{i'}s_{k'} - s_{i}s_{k'} - s_{i'}s_{k}).
$$
Only bonds with $\Delta_{ik} > 0$ are probably connected and the sign of $\Delta_{ik}$ will change in the process $\nu \rightarrow \mu$.

Now let's calculate $E_{\nu} - E_{\mu}$.
$$
\begin{aligned}
E_{\mu} = E_{in} + E_{ex} - J \sum_{\langle ik \rangle} s_i s_k - J \sum_{\langle i' k' \rangle} s_{i'} s_{k'}, \\
E_{\nu} = E_{in} + E_{ex} - J \sum_{\langle i'k \rangle} s_{i'} s_k - J \sum_{\langle i k' \rangle} s_{i} s_{k'}. \\
\end{aligned}
$$
$$
\begin{aligned}
\frac{g_{\mu \rightarrow \nu}}{g_{\nu \rightarrow \mu}} \frac{A_{\mu \rightarrow \nu}}{A_{\nu \rightarrow \mu}}
&= \prod_{\langle i i' k k' \rangle} \exp[{-\beta J(s_{i}s_{k} + s_{i'} s_{k'} - s_{i'} s_k - s_{i} s_{k'} )}] \\
&= \frac{1 - p_{add}(1)}{1} \frac{1 - p_{add}(2)}{1} \cdots \frac{1 - p_{add}(m)}{1} \frac{1}{1 - p_{add}(m+1)} \cdots \frac{1}{1 - p_{add}(N)}
\end{aligned}
$$
Where we have $N$ bonds in total and $m$ bonds with $\Delta_{ik} \gt 0$ in the process $\mu \rightarrow \nu$. By choosing $p_{add}(i) = 1 - \exp[-\beta J(s_{i}s_{k} + s_{i'} s_{k'} - s_{i'} s_k - s_{i} s_{k'})]$ we have $A_{\mu \rightarrow \nu} / A_{\nu \rightarrow \mu} = 1$ and the acceptance probability is $1$.

When considering 
$$
\mathcal{H} = - \sum_{\langle ij \rangle} J_{ij} s_i s_j,
$$
the formula is a little complex due to the $E_{\mu} - E_{\nu}$ contains $4$ terms. The results are
$$
p_{add}(i) = 1 - \exp[-\beta (J_{ik} s_is_k - J_{ik} s_{i'} s_k + J_{i'k'} s_{i'} s_{k'} - J_{i'k'} s_{i} s_{k'})]
$$
