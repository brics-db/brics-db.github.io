---
layout: AHEAD
---

{:pub: .publist}
{:ref: .reflist}
{:image: .image}
{:title: .title}
{:authors: .authors}
{:series: .series}

## <center>AHEAD<br/>&mdash;<br/> Adaptable Data Hardening for On-the-Fly Hardware Error Detection during Database Query Processing</center>

<em>AHEAD</em> is our in-memory column store prototype which incorporates AN Coding for detecting (transient) hardware errors during query processing &ndash; at run-time! The respective paper ["AHEAD: Adaptable Data Hardening for On-the-Fly Hardware Error Detection during Database Query Processing"](#pub1) was accepted at SIGMOD'18.

We will gradually fill these sections with more contents.

## Bit Flip Detection Opportunities

When do we do bit flip detection?

## SSB results

We evaluated AHEAD using the [Star Schema Benchmark (SSB)](#ref1).

You can download the raw output, plot scripts and other material we used for our SIGMOD'18 paper [here](https://wwwdb.inf.tu-dresden.de/misc/brics/SIGMOD18ssb.zip).

## Contributing and Feedback

[<svg height="32" class="octicon octicon-mark-github" viewBox="0 0 16 16" version="1.1" width="32" aria-hidden="true"><path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0 0 16 8c0-4.42-3.58-8-8-8z"/></svg>GitHub / brics-db / AHEAD](https://github.com/brics-db/AHEAD)

Please feel free to fork on [github](https://github.com/brics-db/AHEAD), send pull requests, and file issues in the [issue tracker](https://github.com/brics-db/AHEAD/issues).

## Related Publications

+ <img alt="SIGMOD 2018" src="/assets/images/logo_SIGMOD_2018.png" />
  {:image}

  <a name="pub1" href="https://wwwdb.inf.tu-dresden.de/misc/brics/papers/2018%20-%20SIGMOD%20-%20AHEAD.pdf">AHEAD: Adaptable Data Hardening for On-the-Fly Hardware Error Detection during Database Query Processing.</a>
  {:title}

  Kolditz, T.; Habich, D.; Lehner, W.; Werner, M.; de Bruijn, S.T.J.
  {:authors}
{:pub}

## References

1.  <a name="ref1" href="https://doi.org/10.1007/978-3-642-10424-4_17">The Star Schema Benchmark and Augmented Fact Table Indexing</a>
    {:title}

    Patrick O’Neil, Elizabeth O’Neil, Xuedong Chen, Stephen Revilak
    {:authors}

    Nambiar R., Poess M. (eds) Performance Evaluation and Benchmarking. TPCTC 2009. Lecture Notes in Computer Science, vol 5895. Springer, Berlin, Heidelberg.
    {:series}
{:ref}

## Disclosure

The SVG image for the link to the GitHub page is taken from GitHub.
