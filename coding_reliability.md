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

<table>
	<thead>
		<tr>
			<th rowspan="2">$$|A|$$</th>
			<th colspan="8">$$|k|$$</th>
		</tr>
		<tr>
			<th>1</th>
			<th>2</th>
			<th>3</th>
			<th>4</th>
			<th>5</th>
			<th>6</th>
			<th>7</th>
			<th>8</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th>2</th>
			<td>3</td>
			<td>3</td>
			<td>3</td>
			<td>3</td>
			<td>3</td>
			<td>3</td>
			<td>3</td>
			<td>3</td>
		</tr>
		<tr>
			<th>3</th>
			<td>7</td>
			<td>7</td>
			<td>7</td>
			<td>7</td>
			<td>7</td>
			<td>7</td>
			<td>7</td>
			<td>7</td>
		</tr>
		<tr>
			<th>4</th>
			<td>15</td>
			<td>13</td>
			<td>13</td>
			<td>13</td>
			<td>13</td>
			<td>13</td>
			<td>13</td>
			<td>13</td>
		</tr>
		<tr>
			<th>5</th>
			<td>31</td>
			<td>29</td>
			<td>29</td>
			<td>27</td>
			<td>29</td>
			<td>29</td>
			<td>29</td>
			<td>29</td>
		</tr>
		<tr>
			<th>6</th>
			<td>63</td>
			<td>53</td>
			<td>45</td>
			<td>45</td>
			<td>45</td>
			<td>45</td>
			<td>59</td>
			<td>59</td>
		</tr>
		<tr>
			<th>7</th>
			<td>127</td>
			<td>117</td>
			<td>89</td>
			<td>89</td>
			<td>117</td>
			<td>115</td>
			<td>115</td>
			<td>115</td>
		</tr>
		<tr>
			<th>8</th>
			<td>255</td>
			<td>213</td>
			<td>229</td>
			<td>229</td>
			<td>233</td>
			<td>233</td>
			<td>217</td>
			<td>233</td>
		</tr>
		<tr>
			<th>9</th>
			<td>511</td>
			<td>469</td>
			<td>467</td>
			<td>467</td>
			<td>443</td>
			<td>471</td>
			<td>471</td>
			<td>487</td>
		</tr>
		<tr>
			<th>10</th>
			<td>1023</td>
			<td>853</td>
			<td>917</td>
			<td>933</td>
			<td>933</td>
			<td>809</td>
			<td>933</td>
			<td>857</td>
		</tr>
		<tr>
			<th>11</th>
			<td>2047</td>
			<td>1877</td>
			<td>1837</td>
			<td>1867</td>
			<td>1909</td>
			<td>1899</td>
			<td>1803</td>
			<td>1939</td>
		</tr>
		<tr>
			<th>12</th>
			<td>4095</td>
			<td>3285</td>
			<td>3673</td>
			<td>3737</td>
			<td>3787</td>
			<td>3813</td>
			<td>3813</td>
			<td>3813</td>
		</tr>
		<tr>
			<th>13</th>
			<td>8191</td>
			<td>6613</td>
			<td>7349</td>
			<td>6777</td>
			<td>7085</td>
			<td>7837</td>
			<td>7637</td>
			<td>7463</td>
		</tr>
		<tr>
			<th>14</th>
			<td>16383</td>
			<td>13141</td>
			<td>13779</td>
			<td>14937</td>
			<td>15221</td>
			<td>14159</td>
			<td>13963</td>
			<td>13963</td>
		</tr>
		<tr>
			<th>15</th>
			<td>32767</td>
			<td>26453</td>
			<td>23733</td>
			<td>31385</td>
			<td>31373</td>
			<td>31373</td>
			<td>27247</td>
			<td>27247</td>
		</tr>
		<tr>
			<th>16</th>
			<td>65535</td>
			<td>52565</td>
			<td>56501</td>
			<td>47729</td>
			<td>59973</td>
			<td>62739</td>
			<td>55831</td>
			<td>55831</td>
		</tr>
	</tbody>
</table>

## Contributing and Feedback

[<svg height="32" class="octicon octicon-mark-github" viewBox="0 0 16 16" version="1.1" width="32" aria-hidden="true"><path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0 0 16 8c0-4.42-3.58-8-8-8z"/></svg>GitHub / brics-db / coding_reliability](https://github.com/brics-db/coding_reliability){:hreflang="en"}{:target="_blank"}

Please feel free to fork on [github](https://github.com/brics-db/coding_reliability){:hreflang="en"}{:target="_blank"}, send pull requests, and file issues in the [issue tracker](https://github.com/brics-db/coding_reliability/issues){:hreflang="en"}{:target="_blank"}.

## Disclosure

The SVG image for the link to the GitHub page is taken from GitHub.
