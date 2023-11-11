---
title: 'The Queen and the treasure'
date: 2020-06-14
permalink: /posts/2020/06/2020-06-14-queen-treasure/
tags:
  - secret-sharing
---

An elder Queen wants to leave a treasure to her heirs $H_1, H_2, H_3$. Since the Queen is passionate about technology, the treasure is a huge amount of digital cash stored on a blockchain and it is protected by a secret key $s$.

The secret key $s$ has to be shared among the heirs in a way that it can be reconstructed if and only if the 3 heirs cooperate or one of them cooperate with a notary $N$.
This implies that a number of heirs smaller than 3 or the notary alone cannot reconstruct the secret key $s$. For simplicity, it is assumed that the shares are delivered to the parties when the Queen dies.

In other words, suppose the Queen wants the heirs to have access to the treasure if and only if all of them are unite after her death or at least one of them is smart and pays a visit to the notary, who is a good man but not enough to just give him the whole secret key $s$.

This can be achieved by using a technique of **secret sharing schemes for general access structures** introduced by Ito et. al. [[1](#ref1)] (following the approach of [[2](#ref2)]) based on a simple $n$-out-of-$n$ additive secret sharing scheme.

Let $P = \\{H_1, H_2, H_3, N\\}$ and $s \in \mathbb{Z}_q$.

Let $\Pi = \\{\\{H_1,H_2\\}, \\{H_1,H_3\\}, \\{H_2,H_3\\}, \\{N\\}\\}$ be the secrecy structure described in terms of maximal unqualified sets, i.e., the maximal sets of parties not able to reconstruct the secret $s$. 

Let $T_1 = \\{H_1,H_2\\}$, $T_2 = \\{H_1,H_3\\}$  and so on.

Then, compute

$\hat{T}_1 = P \setminus T_1 = \\{H_3, N\\}$

$\hat{T}_2 = P \setminus T_2 = \\{H_2, N\\}$

$\hat{T}_3 = P \setminus T_3 = \\{H_1, N\\}$

$\hat{T}_4 = P \setminus T_4 = \\{H_1, H_2, H_3\\}$.

At this point the Queen, acting as the dealer, splits $s$ in $s_1,\dots,s_4$, i.e., randomly samples $s_1,\dots, s_{3}$ from $\mathbb{Z}_q$ and sets $s_4 = s - (s_1 + \dots + s_3)$ and, for $i = 1, \dots , 4$, sends $s_i$ to all parties $P_j \in \hat{T}_i$.

In that way, the shares are distributed among the parties as follows (an empty space means that a certain share is not available to the corresponding party):

|       | $s_1$ | $s_2$ | $s_3$ | $s_4$ |
|-------|-------|-------|-------|-------|
| $H_1$ |       |       | Yes   | Yes   |
| $H_2$ |       | Yes   |       | Yes   |
| $H_3$ | Yes   |       |       | Yes   |
| $N$   | Yes   | Yes   | Yes   |       |

Since all the shares $s_1, s_2, s_3, s_4$ are necessary to reconstruct the secret $s$, from the table above it is evident that $H_1, H_2, H_3$ or any of them and $N$ are forced to cooperate to do so and, of course, the Queen knew it!


## References

<a name="ref1"></a> [1] [Ito, M., Saito, A., & Nishizeki, T. (1989). Secret sharing scheme realizing general access structure. Electronics and Communications in Japan (Part III: Fundamental Electronic Science), 72(9), 56-64.](http://archiv.infsec.ethz.ch/education/fs08/secsem/ItSaNi87.pdf)

<a name="ref2"></a> [2] [Maurer, U. (2006). Secure multi-party computation made simple. Discrete Applied Mathematics, 154(2), 370-381.](https://core.ac.uk/download/pdf/82654945.pdf)
