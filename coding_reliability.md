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

Using these target functions, we define our optimization problem:

$$\Psi_\eta(k,h)=\max \big( \eta(k,A), 1 - \psi(k,A) \big) \quad,~|A| = h$$

It takes all (computed) $$A$$s of a given parameter bit width ($$k$$) and checks for the largest minimal detectable bit flip weight (the guarantee to detect all $$1 \dots x$$-bit flips, with maximum x among the available $$A$$s) and the smallest first non-zero SDC probability.

In the following four tables we list all of the <em>golden $$A$$s</em> determined through the above optimization problem. In small font and parantheses we also list for the given combination of $$A$$ and $$k$$ the minimal detectable bit flip weight.

<table class="listofA">
	<thead>
		<tr>
			<th rowspan="2">$$|A|$$</th>
			<th colspan="8">$$k$$</th>
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
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
		</tr>
		<tr>
			<th>3</th>
			<td>7 <small>(2)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
		</tr>
		<tr>
			<th>4</th>
			<td>15 <small>(3)</small></td>
			<td>13 <small>(2)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
		</tr>
		<tr>
			<th>5</th>
			<td>31 <small>(4)</small></td>
			<td>29 <small>(2)</small></td>
			<td>29 <small>(2)</small></td>
			<td>27 <small>(2)</small></td>
			<td>29 <small>(2)</small></td>
			<td>29 <small>(2)</small></td>
			<td>29 <small>(2)</small></td>
			<td>29 <small>(2)</small></td>
		</tr>
		<tr>
			<th>6</th>
			<td>63 <small>(5)</small></td>
			<td>53 <small>(3)</small></td>
			<td>45 <small>(3)</small></td>
			<td>45 <small>(2)</small></td>
			<td>45 <small>(2)</small></td>
			<td>45 <small>(2)</small></td>
			<td>59 <small>(2)</small></td>
			<td>59 <small>(2)</small></td>
		</tr>
		<tr>
			<th>7</th>
			<td>127 <small>(6)</small></td>
			<td>117 <small>(3)</small></td>
			<td>117 <small>(3)</small></td>
			<td>89 <small>(3)</small></td>
			<td>117 <small>(3)</small></td>
			<td>115 <small>(2)</small></td>
			<td>115 <small>(2)</small></td>
			<td>115 <small>(2)</small></td>
		</tr>
		<tr>
			<th>8</th>
			<td>255 <small>(7)</small></td>
			<td>213 <small>(4)</small></td>
			<td>229 <small>(3)</small></td>
			<td>229 <small>(3)</small></td>
			<td>233 <small>(3)</small></td>
			<td>233 <small>(3)</small></td>
			<td>217 <small>(3)</small></td>
			<td>233 <small>(3)</small></td>
		</tr>
		<tr>
			<th>9</th>
			<td>511 <small>(8)</small></td>
			<td>469 <small>(4)</small></td>
			<td>467 <small>(4)</small></td>
			<td>467 <small>(3)</small></td>
			<td>443 <small>(3)</small></td>
			<td>471 <small>(3)</small></td>
			<td>471 <small>(3)</small></td>
			<td>487 <small>(3)</small></td>
		</tr>
		<tr>
			<th>10</th>
			<td>1023 <small>(9)</small></td>
			<td>853 <small>(5)</small></td>
			<td>917 <small>(4)</small></td>
			<td>933 <small>(4)</small></td>
			<td>933 <small>(4)</small></td>
			<td>809 <small>(3)</small></td>
			<td>933 <small>(3)</small></td>
			<td>857 <small>(3)</small></td>
		</tr>
		<tr>
			<th>11</th>
			<td>2047 <small>(10)</small></td>
			<td>1877 <small>(5)</small></td>
			<td>1837 <small>(5)</small></td>
			<td>1867 <small>(4)</small></td>
			<td>1909 <small>(4)</small></td>
			<td>1899 <small>(4)</small></td>
			<td>1803 <small>(4)</small></td>
			<td>1939 <small>(4)</small></td>
		</tr>
		<tr>
			<th>12</th>
			<td>4095 <small>(11)</small></td>
			<td>3285 <small>(6)</small></td>
			<td>3673 <small>(5)</small></td>
			<td>3737 <small>(4)</small></td>
			<td>3787 <small>(4)</small></td>
			<td>3813 <small>(4)</small></td>
			<td>3813 <small>(4)</small></td>
			<td>3813 <small>(4)</small></td>
		</tr>
		<tr>
			<th>13</th>
			<td>8191 <small>(12)</small></td>
			<td>6613 <small>(6)</small></td>
			<td>7349 <small>(6)</small></td>
			<td>6777 <small>(5)</small></td>
			<td>7085 <small>(5)</small></td>
			<td>7837 <small>(5)</small></td>
			<td>7637 <small>(4)</small></td>
			<td>7463 <small>(4)</small></td>
		</tr>
		<tr>
			<th>14</th>
			<td>16383 <small>(13)</small></td>
			<td>13141 <small>(7)</small></td>
			<td>13779 <small>(6)</small></td>
			<td>14937 <small>(5)</small></td>
			<td>15221 <small>(5)</small></td>
			<td>14159 <small>(5)</small></td>
			<td>13963 <small>(5)</small></td>
			<td>13963 <small>(5)</small></td>
		</tr>
		<tr>
			<th>15</th>
			<td>32767 <small>(14)</small></td>
			<td>26453 <small>(7)</small></td>
			<td>23733 <small>(7)</small></td>
			<td>31385 <small>(6)</small></td>
			<td>31373 <small>(6)</small></td>
			<td>31373 <small>(5)</small></td>
			<td>27247 <small>(5)</small></td>
			<td>27247 <small>(5)</small></td>
		</tr>
		<tr>
			<th>16</th>
			<td>65535 <small>(15)</small></td>
			<td>52565 <small>(8)</small></td>
			<td>56501 <small>(7)</small></td>
			<td>47729 <small>(6)</small></td>
			<td>59973 <small>(6)</small></td>
			<td>62739 <small>(6)</small></td>
			<td>55831 <small>(6)</small></td>
			<td>55831 <small>(6)</small></td>
		</tr>
	</tbody>
</table>
<table class="listofA">
	<thead>
		<tr>
			<th rowspan="2">$$|A|$$</th>
			<th colspan="8">$$k$$</th>
		</tr>
		<tr>
			<th>9</th>
			<th>10</th>
			<th>11</th>
			<th>12</th>
			<th>13</th>
			<th>14</th>
			<th>15</th>
			<th>16</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th>2</th>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
		</tr>
		<tr>
			<th>3</th>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
		</tr>
		<tr>
			<th>4</th>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
		</tr>
		<tr>
			<th>5</th>
			<td>29 <small>(2)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
		</tr>
		<tr>
			<th>6</th>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
		</tr>
		<tr>
			<th>7</th>
			<td>123 <small>(2)</small></td>
			<td>123 <small>(2)</small></td>
			<td>123 <small>(2)</small></td>
			<td>123 <small>(2)</small></td>
			<td>123 <small>(2)</small></td>
			<td>119 <small>(2)</small></td>
			<td>119 <small>(2)</small></td>
			<td>119 <small>(2)</small></td>
		</tr>
		<tr>
			<th>8</th>
			<td>185 <small>(3)</small></td>
			<td>185 <small>(3)</small></td>
			<td>233 <small>(2)</small></td>
			<td>215 <small>(2)</small></td>
			<td>215 <small>(2)</small></td>
			<td>233 <small>(2)</small></td>
			<td>233 <small>(2)</small></td>
			<td>233 <small>(2)</small></td>
		</tr>
		<tr>
			<th>9</th>
			<td>487 <small>(3)</small></td>
			<td>451 <small>(3)</small></td>
			<td>451 <small>(3)</small></td>
			<td>463 <small>(3)</small></td>
			<td>463 <small>(3)</small></td>
			<td>463 <small>(3)</small></td>
			<td>463 <small>(3)</small></td>
			<td>463 <small>(3)</small></td>
		</tr>
		<tr>
			<th>10</th>
			<td>857 <small>(3)</small></td>
			<td>857 <small>(3)</small></td>
			<td>857 <small>(3)</small></td>
			<td>857 <small>(3)</small></td>
			<td>947 <small>(3)</small></td>
			<td>947 <small>(3)</small></td>
			<td>947 <small>(3)</small></td>
			<td>947 <small>(3)</small></td>
		</tr>
		<tr>
			<th>11</th>
			<td>1939 <small>(4)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
		</tr>
		<tr>
			<th>12</th>
			<td>3621 <small>(4)</small></td>
			<td>3739 <small>(4)</small></td>
			<td>3739 <small>(4)</small></td>
			<td>3737 <small>(4)</small></td>
			<td>3349 <small>(4)</small></td>
			<td>3349 <small>(3)</small></td>
			<td>3349 <small>(3)</small></td>
			<td>3349 <small>(3)</small></td>
		</tr>
		<tr>
			<th>13</th>
			<td>5729 <small>(4)</small></td>
			<td>6717 <small>(4)</small></td>
			<td>6717 <small>(4)</small></td>
			<td>6717 <small>(4)</small></td>
			<td>7413 <small>(4)</small></td>
			<td>6717 <small>(4)</small></td>
			<td>7785 <small>(4)</small></td>
			<td>7785 <small>(4)</small></td>
		</tr>
		<tr>
			<th>14</th>
			<td>15717 <small>(5)</small></td>
			<td>15469 <small>(4)</small></td>
			<td>14139 <small>(4)</small></td>
			<td>14139 <small>(4)</small></td>
			<td>14139 <small>(4)</small></td>
			<td>14139 <small>(4)</small></td>
			<td>14139 <small>(4)</small></td>
			<td>14781 <small>(4)</small></td>
		</tr>
		<tr>
			<th>15</th>
			<td>27425 <small>(5)</small></td>
			<td>27425 <small>(5)</small></td>
			<td>27425 <small>(5)</small></td>
			<td>29925 <small>(5)</small></td>
			<td>27825 <small>(5)</small></td>
			<td>28619 <small>(4)</small></td>
			<td>28183 <small>(4)</small></td>
			<td>28183 <small>(4)</small></td>
		</tr>
		<tr>
			<th>16</th>
			<td>55831 <small>(6)</small></td>
			<td>59965 <small>(5)</small></td>
			<td>58901 <small>(5)</small></td>
			<td>62749 <small>(5)</small></td>
			<td>62749 <small>(5)</small></td>
			<td>63877 <small>(5)</small></td>
			<td>63877 <small>(5)</small></td>
			<td>63877 <small>(5)</small></td>
		</tr>
	</tbody>
</table>
<table class="listofA">
	<thead>
		<tr>
			<th rowspan="2">$$|A|$$</th>
			<th colspan="8">$$k$$</th>
		</tr>
		<tr>
			<th>17</th>
			<th>18</th>
			<th>19</th>
			<th>20</th>
			<th>21</th>
			<th>22</th>
			<th>23</th>
			<th>24</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th>2</th>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
		</tr>
		<tr>
			<th>3</th>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
		</tr>
		<tr>
			<th>4</th>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
		</tr>
		<tr>
			<th>5</th>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
		</tr>
		<tr>
			<th>6</th>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
			<td>61 <small>(2)</small></td>
		</tr>
		<tr>
			<th>7</th>
			<td>119 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
		</tr>
		<tr>
			<th>8</th>
			<td>233 <small>(2)</small></td>
			<td>233 <small>(2)</small></td>
			<td>233 <small>(2)</small></td>
			<td>233 <small>(2)</small></td>
			<td>233 <small>(2)</small></td>
			<td>237 <small>(2)</small></td>
			<td>237 <small>(2)</small></td>
			<td>237 <small>(2)</small></td>
		</tr>
		<tr>
			<th>9</th>
			<td>393 <small>(3)</small></td>
			<td>393 <small>(2)</small></td>
			<td>393 <small>(2)</small></td>
			<td>393 <small>(2)</small></td>
			<td>423 <small>(2)</small></td>
			<td>423 <small>(2)</small></td>
			<td>423 <small>(2)</small></td>
			<td>423 <small>(2)</small></td>
		</tr>
		<tr>
			<th>10</th>
			<td>947 <small>(3)</small></td>
			<td>947 <small>(3)</small></td>
			<td>947 <small>(3)</small></td>
			<td>985 <small>(3)</small></td>
			<td>985 <small>(3)</small></td>
			<td>985 <small>(3)</small></td>
			<td>985 <small>(3)</small></td>
			<td>981 <small>(3)</small></td>
		</tr>
		<tr>
			<th>11</th>
			<td>1909 <small>(3)</small></td>
			<td>1909 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1909 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
		</tr>
		<tr>
			<th>12</th>
			<td>3349 <small>(3)</small></td>
			<td>3349 <small>(3)</small></td>
			<td>3349 <small>(3)</small></td>
			<td>3091 <small>(3)</small></td>
			<td>3091 <small>(3)</small></td>
			<td>3091 <small>(3)</small></td>
			<td>3091 <small>(3)</small></td>
			<td>3829 <small>(3)</small></td>
		</tr>
		<tr>
			<th>13</th>
			<td>7785 <small>(4)</small></td>
			<td>7785 <small>(4)</small></td>
			<td>7985 <small>(4)</small></td>
			<td>7985 <small>(4)</small></td>
			<td>6311 <small>(3)</small></td>
			<td>6311 <small>(3)</small></td>
			<td>6311 <small>(3)</small></td>
			<td>6311 <small>(3)</small></td>
		</tr>
		<tr>
			<th>14</th>
			<td>14781 <small>(4)</small></td>
			<td>15207 <small>(4)</small></td>
			<td>16089 <small>(4)</small></td>
			<td>16089 <small>(4)</small></td>
			<td>15507 <small>(4)</small></td>
			<td>15993 <small>(4)</small></td>
			<td>15993 <small>(4)</small></td>
			<td>15993 <small>(4)</small></td>
		</tr>
		<tr>
			<th>15</th>
			<td>32343 <small>(4)</small></td>
			<td>32343 <small>(4)</small></td>
			<td>32343 <small>(4)</small></td>
			<td>32343 <small>(4)</small></td>
			<td>30987 <small>(4)</small></td>
			<td>30987 <small>(4)</small></td>
			<td>30987 <small>(4)</small></td>
			<td>29675 <small>(4)</small></td>
		</tr>
		<tr>
			<th>16</th>
			<td>63859 <small>(5)</small></td>
			<td>63859 <small>(5)</small></td>
			<td>58659 <small>(4)</small></td>
			<td>58659 <small>(4)</small></td>
			<td>58659 <small>(4)</small></td>
			<td>58659 <small>(4)</small></td>
			<td>58659 <small>(4)</small></td>
			<td>64311 <small>(4)</small></td>
		</tr>
	</tbody>
</table>
<table class="listofA">
	<thead>
		<tr>
			<th rowspan="2">$$|A|$$</th>
			<th colspan="8">$$k$$</th>
		</tr>
		<tr>
			<th>25</th>
			<th>26</th>
			<th>27</th>
			<th>28</th>
			<th>29</th>
			<th>30</th>
			<th>31</th>
			<th>32</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th>2</th>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
			<td>3 <small>(1)</small></td>
		</tr>
		<tr>
			<th>3</th>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
			<td>7 <small>(1)</small></td>
		</tr>
		<tr>
			<th>4</th>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
			<td>13 <small>(1)</small></td>
		</tr>
		<tr>
			<th>5</th>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
			<td>29 <small>(1)</small></td>
		</tr>
		<tr>
			<th>6</th>
			<td>61 <small>(1)</small></td>
			<td>61 <small>(1)</small></td>
			<td>61 <small>(1)</small></td>
			<td>61 <small>(1)</small></td>
			<td>61 <small>(1)</small></td>
			<td>61 <small>(1)</small></td>
			<td>61 <small>(1)</small></td>
			<td>61 <small>(1)</small></td>
		</tr>
		<tr>
			<th>7</th>
			<td>111 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
			<td>111 <small>(2)</small></td>
			<td>125 <small>(2)</small></td>
			<td>125 <small>(2)</small></td>
			<td>125 <small>(2)</small></td>
		</tr>
		<tr>
			<th>8</th>
			<td>225 <small>(2)</small></td>
			<td>225 <small>(2)</small></td>
			<td>225 <small>(2)</small></td>
			<td>225 <small>(2)</small></td>
			<td>225 <small>(2)</small></td>
			<td>225 <small>(2)</small></td>
			<td>225 <small>(2)</small></td>
			<td>225 <small>(2)</small></td>
		</tr>
		<tr>
			<th>9</th>
			<td>423 <small>(2)</small></td>
			<td>423 <small>(2)</small></td>
			<td>423 <small>(2)</small></td>
			<td>423 <small>(2)</small></td>
			<td>423 <small>(2)</small></td>
			<td>445 <small>(2)</small></td>
			<td>445 <small>(2)</small></td>
			<td>445 <small>(2)</small></td>
		</tr>
		<tr>
			<th>10</th>
			<td>981 <small>(3)</small></td>
			<td>981 <small>(3)</small></td>
			<td>951 <small>(3)</small></td>
			<td>951 <small>(3)</small></td>
			<td>835 <small>(3)</small></td>
			<td>835 <small>(3)</small></td>
			<td>881 <small>(3)</small></td>
			<td>881 <small>(3)</small></td>
		</tr>
		<tr>
			<th>11</th>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>1939 <small>(3)</small></td>
			<td>2029 <small>(3)</small></td>
			<td>2029 <small>(3)</small></td>
		</tr>
		<tr>
			<th>12</th>
			<td>3829 <small>(3)</small></td>
			<td>3829 <small>(3)</small></td>
			<td>3829 <small>(3)</small></td>
			<td>3829 <small>(3)</small></td>
			<td>3829 <small>(3)</small></td>
			<td>3829 <small>(3)</small></td>
			<td>3973 <small>(3)</small></td>
			<td>3973 <small>(3)</small></td>
		</tr>
		<tr>
			<th>13</th>
			<td>6311 <small>(3)</small></td>
			<td>7841 <small>(3)</small></td>
			<td>7841 <small>(3)</small></td>
			<td>7841 <small>(3)</small></td>
			<td>7841 <small>(3)</small></td>
			<td>7841 <small>(3)</small></td>
			<td>7841 <small>(3)</small></td>
			<td>7841 <small>(3)</small></td>
		</tr>
		<tr>
			<th>14</th>
			<td>15685 <small>(4)</small></td>
			<td>15203 <small>(4)</small></td>
			<td>15203 <small>(4)</small></td>
			<td>15203 <small>(3)</small></td>
			<td>15203 <small>(3)</small></td>
			<td>15203 <small>(3)</small></td>
			<td>15203 <small>(3)</small></td>
			<td>15331 <small>(3)</small></td>
		</tr>
		<tr>
			<th>15</th>
			<td>29685 <small>(4)</small></td>
			<td>29685 <small>(4)</small></td>
			<td>29685 <small>(4)</small></td>
			<td>29685 <small>(4)</small></td>
			<td>29685 <small>(4)</small></td>
			<td>30597 <small>(4)</small></td>
			<td>30221 <small>(4)</small></td>
			<td>30221 <small>(4)</small></td>
		</tr>
		<tr>
			<th>16</th>
			<td>64311 <small>(4)</small></td>
			<td>64311 <small>(4)</small></td>
			<td>64311 <small>(4)</small></td>
			<td>64311 <small>(4)</small></td>
			<td>64311 <small>(4)</small></td>
			<td>64311 <small>(4)</small></td>
			<td>64311 <small>(4)</small></td>
			<td>64311 <small>(4)</small></td>
		</tr>
	</tbody>
</table>



## Contributing and Feedback

[<svg height="32" class="octicon octicon-mark-github" viewBox="0 0 16 16" version="1.1" width="32" aria-hidden="true"><path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0 0 16 8c0-4.42-3.58-8-8-8z"/></svg>GitHub / brics-db / coding_reliability](https://github.com/brics-db/coding_reliability){:hreflang="en"}{:target="_blank"}

Please feel free to fork on [github](https://github.com/brics-db/coding_reliability){:hreflang="en"}{:target="_blank"}, send pull requests, and file issues in the [issue tracker](https://github.com/brics-db/coding_reliability/issues){:hreflang="en"}{:target="_blank"}.

## Disclosure

The SVG image for the link to the GitHub page is taken from GitHub.
