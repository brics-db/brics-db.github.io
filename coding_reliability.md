---
layout: coding_reliability
---

## <center>Coding Reliability</center>

On these pages we provide our findings and results regarding code reliability. More contents will follow in the near future.

### AN Coding

For AN coding, the choice of the code parameter $$A$$ is the most crucial part. As it turned out in our studies, for each <em>data bit width</em> each A behaves differently! Since in-memory database systems operate on each individual data width ranging from 1 to 32 bits, we had to compute the "goodness" of each A for all these bit widths.

For a given $$A$$ and data bit width $$k$$, we can compute the probability of silent data corruption (SDC) for a certain bit flip weight $$b$$. This means, how likely it is for a specific AN code (with given $$k$$ and $$A$$) that a $$b$$-bit flip results in another code word and is therefore not detectable.

For each combination of data bit width ($$k$$) and bit width of the parameter $$A$$ ($$h$$) we want a "best" $$A$$. We define "goodness" as giving a maximum lower bound of the detectable bit flip weight. In other words, it is those $$A$$ which generate AN codes of width $$n=h+k$$ with _largest_ minimal Hamming distance. For each combination of $$k$$ and $$h$$, there is typically a _set_ of candidate $$A$$s, from which _the_ best $$A$$ needs to be selected. To select a single best $$A$$, you can define optimization functions and an optimality criterion. In our case, we define two optimization functions:

1. For a given data width $$k$$ and some $$A$$, this functions returns the lower bound of the detectable bit flip weight:<br/>$$\eta(k,A) = \max b \quad, \varphi_x^{k,A}=0 \wedge 0 \leq x \leq b$$<br/>This essentially defines the candidate set.
2. From that candidate set, we select that $$A$$ which has the lowest first non-zero probability of silent data corruption (SDC):<br/>$$\psi(k,A) = \varphi_{b=\eta(k,A)+1}^{k,A}$$

Using these optimization functions, we define our optimality criterion:

$$\Psi_\eta(k,h)=\max \big( \eta(k,A), 1 - \psi(k,A) \big) \quad,~|A| = h$$

It takes all (computed) $$A$$s of a given parameter bit width ($$k$$) and checks for the largest minimal detectable bit flip weight (the guarantee to detect all $$1 \dots x$$-bit flips, with maximum x among the available $$A$$s) and the smallest first non-zero SDC probability.

|   |_\8. $$k$$ |
| $$|A|$$  | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
|  2 |     3  |     3  |     3  |     3  |     3  |     3  |     3  |     3  |
|  3 |     7  |     7  |     7  |     7  |     7  |     7  |     7  |     7  |
|  4 |    15  |    13  |    13  |    13  |    13  |    13  |    13  |    13  |
|  5 |    31  |    29  |    29  |    27  |    29  |    29  |    29  |    29  |
|  6 |    63  |    53  |    45  |    45  |    45  |    45  |    59  |    59  |
|  7 |   127  |   117  |    89  |    89  |   117  |   115  |   115  |   115  |
|  8 |   255  |   213  |   229  |   229  |   233  |   233  |   217  |   233  |
|  9 |   511  |   469  |   467  |   467  |   443  |   471  |   471  |   487  |
| 10 |  1023  |   853  |   917  |   933  |   933  |   809  |   933  |   857  |
| 11 |  2047  |  1877  |  1837  |  1867  |  1909  |  1899  |  1803  |  1939  |
| 12 |  4095  |  3285  |  3673  |  3737  |  3787  |  3813  |  3813  |  3813  |
| 13 |  8191  |  6613  |  7349  |  6777  |  7085  |  7837  |  7637  |  7463  |
| 14 | 16383  | 13141  | 13779  | 14937  | 15221  | 14159  | 13963  | 13963  |
| 15 | 32767  | 26453  | 23733  | 31385  | 31373  | 31373  | 27247  | 27247  |
| 16 | 65535  | 52565  | 56501  | 47729  | 59973  | 62739  | 55831  | 55831  |

## Contributing and Feedback

[<svg height="32" class="octicon octicon-mark-github" viewBox="0 0 16 16" version="1.1" width="32" aria-hidden="true"><path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0 0 16 8c0-4.42-3.58-8-8-8z"/></svg>GitHub / brics-db / coding_reliability](https://github.com/brics-db/coding_reliability){:hreflang="en"}{:target="_blank"}

Please feel free to fork on [github](https://github.com/brics-db/coding_reliability){:hreflang="en"}{:target="_blank"}, send pull requests, and file issues in the [issue tracker](https://github.com/brics-db/coding_reliability/issues){:hreflang="en"}{:target="_blank"}.

## Disclosure

The SVG image for the link to the GitHub page is taken from GitHub.
