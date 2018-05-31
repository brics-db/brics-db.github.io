---
layout: ANcoding
---

{:pub: .publist}
{:ref: .reflist}
{:image: .image}
{:title: .title}
{:authors: .authors}
{:series: .series}

## AN Coding

The core of our techniques for detecting transient hardware errors (multi-bit flips) in software are based on an _arithmetic_ coding called AN Coding. It requires to encode each and every integer value and  consequently allows to detect bit flips in each and every integer value, as well. AN Coding only works on integers, but this is not a limitation, because we can view any information as a single integer or a sequence of integers (e.g. strings).

Arithmetic codes were first mentioned in the mid-1950s when Diamond proposed one form of AN coding [[1](#ref1)]. Shortly after, his work was extended by Brown in 1960 [[2](#ref2)]. Later, AN codes were developed for detecting errors in processors, mainly in the field of embedded systems  [[3](#ref3)], [[4](#ref4)]. As we noted above, AN codes received quite some attention during the previous decade and was even proposed to be used in the automotive domain [51].

There are other domains which use _coding_ operations, too, like compression and security. There, encoding is called compress and encrypt, respectively, while decoding is called decompress and decrypt. To distinguish from these domains, we use different terms: **hardening** for increasing the code strength and **softening** for reducing the code strength. We chose these terms since they underline the fact that data is literally hardened (or softened) against bit flips. We will still use "encoding" and "decoding" to add or remove code bits, respectively.

### Coding Operations

Suppose we have some arbitrary integer (data) $$d$$ which we want to encode. AN coding works by _multiplying_ a constant $$A$$ onto the data unit $$d$$:

<table>
  <colgroup>
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="40%" />
  </colgroup>
  <thead>
    <tr>
      <th></th>
      <th>Encoding</th>
      <th>Decoding</th>
      <th>Error Detection</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2">Original</th>
      <td rowspan="2" markdown="span">$$ d \cdot A = c $$</td>
      <td rowspan="2" markdown="span">$$ d = c / A $$</td>
      <td markdown="span">$$ c \% A \equiv 0 \rightarrow $$ valid</td>
    </tr>
    <tr>
      <td markdown="span">$$ c \% A \not\equiv 0 \rightarrow $$ invalid</td>
    </tr>
  </tbody>
</table>

The Original coding operations are what used to be the standard way. Obviously, the division (decoding) and modulus (error detection) operations are painfully slow, even on modern CPUs. We realized that by restricting the parameter $$A$$ to _odd_ values only, we can use the _modular multiplicative inverse_ of $$A$$, which results in the Improved coding operations for decoding and error detection shown just below.

<table>
  <colgroup>
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="40%" />
  </colgroup>
  <thead>
    <tr>
      <th></th>
      <th>Encoding</th>
      <th>Decoding</th>
      <th>Error Detection</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3">Improved</th>
      <td rowspan="3" markdown="span">$$ d \cdot A = c $$</td>
      <td rowspan="3" markdown="span">$$ d = c \cdot A^{-1} $$</td>
      <td markdown="span">$$ c \cdot A^{-1} = d^* < d_\text{min} \rightarrow $$ invalid</td>
    </tr>
    <tr>
    <td markdown="span">$$ c \cdot A^{-1} = d^* > d_\text{max} \rightarrow $$ invalid</td>
    </tr>
    <tr>
    <td markdown="span">otherwise $$ \rightarrow $$ valid</td>
    </tr>
  </tbody>
</table>

Using the inverse works, because CPUs' ALUs implicitly compute in residue class rings. This means that any arithemtic operation is implicitly $$ \text{mod } 2^n $$, where $$ n $$ is the data (register) width in bits, i.e. typically $$8$$, $$16$$, $$32$$, or $$64$$. For the improved error detection, we need to know the exact data _type_ of $$ d $$. From that, we know the smallest and largest _encodable_ values from the original data domain.

## References

1.  <a name="ref1" href="https://doi.org/10.1109/JRPROC.1955.277858">Checking codes for digital computers</a>
    {:title}

    J. M. Diamond
    {:authors}

    Proceedings of the IRE, vol. 43, no. 4, pp. 487–488, Apr. 1955.
    {:series}
2.  <a name="ref2" href="https://doi.org/10.1109/TEC.1960.5219855">Error detecting and correcting binary codes for arithmetic operations</a>
    {:title}

    D. T. Brown
    {:authors}

    IRE Transactions on Electronic Computers, vol. EC-9, no. 3, pp. 333–337, Sep. 1960.
    {:series}
3.  <a name="ref3" href="">Vital coded microprocessor: Principles and application for various transit systems</a>
    {:title}

    P. Forin
    {:authors}

    IFAC-GCCT, pp. 79–84, Sep. 1989.
    {:series}
4.  <a name="ref4" href="https://doi.org/10.1007/978-3-540-75101-4_34">Software Encoded Processing: Building Dependable Systems with Commodity Hardware</a>
    {:title}

    Ute Wappler, Christof Fetzer
    {:authors}

    International Conference on Computer Safety, Reliability, and Security, pp. 356-369, Sep. 2007.
    {:series}
{:ref}
