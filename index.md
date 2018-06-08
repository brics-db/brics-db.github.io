---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defs
layout: index
---

{:pub: .publist}
{:ref: .reflist}
{:image: .image}
{:title: .title}
{:authors: .authors}
{:series: .series}

## <center>Introduction</center>

The key objective of database systems is to reliably manage data, while high query throughput and low query latency are core requirements [[1](#ref1)]. To satisfy these requirements for a constantly increasing amount of data, database systems constantly adapt to new hardware features [[2](#ref2), [3](#ref3), [4](#ref4), [5](#ref5), [6](#ref6), [7](#ref7)], for instance: new instruction sets, increasing core counts, changing core/cache topologies, increasing DRAM bandwidths, or new persistence technologies (nvRAM) [[8](#ref8), [9](#ref9), [10](#ref10)]. These advances come with a backdraw, though: for a long time it has been known that hardware is subject to soft and hard errors [[11](#ref11), [12](#ref12), [13](#ref13)]. Soft errors are also called bit flips, which may occur due to cosmic rays, heat, hardware aging, or electrical crosstalk, which, in turn, is due to the ongoing miniaturization of integrated curcuits [[11](#ref11), [14](#ref14)]. Hardware aging even leads to increasing error rates during a system’s run-time. Despite increasing error rates, database research could focus on improving performance (higher throughput, lower latency) by leveraging hardware improvements, without considering any side effects.

So far, this was possible because soft errors were masked by hardware, i.e. either did not propagate to the software layer, or lead to process or system crashes. Server-grade hardware like ECC DRAM can correct single bit flips and detect double bit flips. However, the picture has already changed, as large-scale systems are yet suffering from the increasing error rates. Scaling up today’s hardware detection and correction capabilities is not always sensible and leads to high overheads in terms of additional code space (memory area) and coding coplexity and latency (multiple or more complex codes). Consequently, error resilience becomes a major challenge for both hardware and software system designers and in the last couple of years researchers gained the insight that a cross-layer approach is required for tackling hardware errors [[15](#ref15)]. You could say, that, this opens a very interesting and and challenging new research area.

The idea is that each layer in the hardware/software stack detects and corrects those errors, for which it is better suited than other layers. For the database domain, this requires novel approaches, as resilience was mainly left to the hardware and operating system layers. For instance, database systems could use context knowledge about data types, algorithms, internal data structures, and inherent redundancy to detect and correct hardware errors when and where it is sensible.

### AHEAD: Adaptable Data Hardening for On-the-Fly Hardware Error Detection during Database Query Processing

We created a main memory-centric column store prototype which does the detection of transient hardware errors (multi-bit flips) in software. Find the sources on [GitHub/brics-db/AHEAD](https://github.com/brics-db/AHEAD){:hreflang="en"}{:target="_blank"}. Other generic software approaches store and process all data twice or thrice (double or triple modular redundancy). In contrast to these application-oblivious techniques, we use a data encoding which is tailored to the actual data size and can be adapted to a desired error rate. More details on the techniques can be found under [AN Coding](/ANCoding){:hreflang="en"} and [Coding Reliability](/coding_reliability){:hreflang="en"} (see navigation bar at the top).

## Related Publications

+ <img alt="SIGMOD 2018" src="/assets/images/logo_SIGMOD_2018.png" />
  {:image}

  <a name="pub7" href="https://doi.org/10.1145/3183713.3183740" target="_blank">AHEAD: Adaptable Data Hardening for On-the-Fly Hardware Error Detection during Database Query Processing.</a>
  {:title}

  Kolditz, T.; Habich, D.; Lehner, W.; Werner, M.; de Bruijn, S.T.J.
  {:authors}

  In _SIGMOD/PODS ’18: 2018 International Conference on Management of Data_, June 10-15, 2018,
  {:series}
+ <img alt="FIBD 2018" src="/assets/images/logo_FIBD_2018.jpeg" />
  {:image}

  <a name="pub6" href="http://www.cambridgescholars.com/further-improvements-in-the-boolean-domain" target="_blank">Multi-GPU Approximation for Silent Data Corruption of AN Codes.</a>
  {:title}

  Werner, M.; Kolditz, T.; Karnagel, T.; Habich, D.; Lehner, W.
  {:authors}

  In _Further Improvements in the Boolean Domain_. Cambridge Scholars Publishing, 2018.
  {:series}
+ <img alt="IWSBP 2016" src="/assets/images/logo_IWSBP.png" />
  {:image}

  <a name="pub6" href="https://wwwdb.inf.tu-dresden.de/wp-content/uploads/2016-IWSBP-Multi-GPU-Approximation-Methods-for-Silent-Data-Corruption-of-AN-Codes.pdf" target="_blank">Multi-GPU Approximation Methods for Silent Data Corruption of AN-Coding.</a>
  {:title}

  Werner, M.; Kolditz, T.; Karnagel, T.; Habich, D.; Lehner, W.
  {:authors}

  In _12th International Workshop on Boolean Problems (IWSBP)_, Freiberg, Germany. 2016.
  {:series}
+ <img alt="image" src="/assets/images/logo_CCIS_2016.jpg" />
  {:image}

  <a name="pub5" href="https://doi.org/10.1007/978-3-319-30162-4_9" target="_blank">Needles in the haystack – Tackling Bit Flips in Lightweight Data Compression.</a>
  {:title}

  Kolditz, T.; Habich, D.; Kuvaiskii, D.; Lehner, W.; Fetzer, C.
  {:authors}

  In _Data Management Technologies and Applications_. Springer International Publishing, 135-153, 2016.
  {:series}
+ <img alt="image" src="/assets/images/logo_DATA_2015.png" />
  {:image}

  <a name="pub4" href="https://doi.org/10.1007/978-3-319-30162-4" target="_blank">Resiliency-aware Data Compression for In-memory Database Systems.</a>
  {:title}

  Kolditz, T.; Habich, D.; Damme, P.; Lehner, W.; Kuvaiskii, D.; Fetzer, C.
  {:authors}

  In _Proceedings of 4th International Conference on Data Management Technologies and Applications (DATA)_, 326-331, 2015.
  {:series}
+ <img alt="BTW 2015" src="/assets/images/logo_BTW_2015.png" />
  {:image}

  <a name="pub3" href="http://www.btw-2015.de/res/proceedings/Hauptband/Demo/Kolditz-Online_Bit_Flip_Detection.pdf" target="_blank">Online Bit Flip Detection for In-Memory B-Trees Live!.</a>
  {:title}

  Kolditz, T.; Schlegel, B.; Habich, D.; Lehner, W.
  {:authors}

  In _Datenbanksysteme für Business, Technologie und Web (BTW)_, 16. Fachtagung des GI-Fachbereichs Datenbanken und Informationssysteme (DBIS). 675-678, 2015.
  {:series}
+ <img alt="DaMoN 2014" src="/assets/images/logo_DAMON.png" />
  {:image}

  <a name="pub2" href="https://doi.org/10.1145/2619228.2619233" target="_blank">Online bit flip detection for in-memory B-trees on unreliable hardware.</a>
  {:title}

  Kolditz, T.; Kissinger, T.; Schlegel, B.; Habich, D.; Lehner, W.
  {:authors}

  In _Proceedings of the Tenth International Workshop on Data Management on New Hardware (DaMoN)_. ACM, 5:1-5:9, 2014.
  {:series}
+ <img alt="VLDB 2011" src="/assets/images/logo_VLDB_2011.png" />
  {:image}

  <a name="pub1" href="http://www.vldb.org/pvldb/vol4/p1462-boehm.pdf" target="_blank">Resiliency-Aware Data Management.</a>
  {:title}

  Lehner, W.; Böhm, M.; Fetzer, C.
  {:authors}

  In _Procecedings of the VLDB Endowment (PVLDB)_. 4:1462-4:1465, 2011.
  {:series}
{:pub}

## References

1.  <a name="ref1" href="https://doi.org/10.1145/2845915" target="_blank">The beckman report on database research</a>
    {:title}

    D. Abadi et al.
    {:authors}

    Commun. ACM, 59(2):92–99, 2016.
    {:series}
2.  <a name="ref2" href="https://doi.org/10.1145/1409360.1409380" target="_blank">Breaking the memory wall in MonetDB.</a>
    {:title}

    P. A. Boncz, M. L. Kersten, and S. Manegold.
    {:authors}

    In _Commun. ACM_, 51(12):77–85, 2008.
    {:series}
3.  <a name="ref3" href="https://doi.org/10.1145/2882903.2882936" target="_blank">Robust Query Processing in Co-Processor-Accelerated Databases.</a>
    {:title}

    S. Breß, H. Funke, and J. Teubner.
    {:authors}

    In _SIGMOD_, pages 1891–1906, 2016.
    {:series}
4.  <a name="ref4" href="https://doi.org/10.1145/2463676.2465295" target="_blank">Query processing on Smart SSDs: Opportunities and Challenges.</a>
    {:title}

    J. Do, Y. Kee, J. M. Patel, C. Park, K. Park, and D. J. DeWitt.
    {:authors}

    In _SIGMOD_, pages 1221–1230, 2013
    {:series}
5.  <a name="ref5" href="https://doi.org/10.14778/3067421.3067423" target="_blank">Adaptive work placement for query processing on heterogeneous computing resources.</a>
    {:title}

    T. Karnagel, D. Habich, and W. Lehner.
    {:authors}

    In _PVLDB_, 10(7):733–744, 2017.
    {:series}
6.  <a name="ref6" href="https://doi.org/10.1145/2882903.2882949" target="_blank">Accelerating relational databases by leveraging remote memory and RDMA.</a>
    {:title}

    F. Li, S. Das, M. Syamala, and V. R. Narasayya.
    {:authors}

    In _SIGMOD_, pages 355–370, 2016.
    {:series}
7.  <a name="ref7" href="https://doi.org/10.1145/2882903.2915251" target="_blank">FPTree: A hybrid SCM-DRAM persistent and concurrent b-tree for storage class memory.</a>
    {:title}

    I. Oukid, J. Lasperas, A. Nica, T. Willhalm, and W. Lehner.
    {:authors}

    In _SIGMOD_, pages 371–386, 2016.
    {:series}
8.  <a name="ref8" href="https://doi.org/10.1145/1941487.1941507" target="_blank">The future of microprocessors.</a>
    {:title}

    S. Borkar and A. A. Chien.
    {:authors}

    In _Commun. ACM_, 54(5):67–77, 2011.
    {:series}
9.  <a name="ref9" href="https://doi.org/10.1109/MDAT.2017.2695879" target="_blank">Emerging memory technologies.</a>
    {:title}

    J. Henkel.
    {:authors}

    In _IEEE Design & Test_, 34(3):4–5, 2017.
    {:series}
10. <a name="ref10" href="https://dl.acm.org/citation.cfm?id=320082" target="_blank">New microarchitecture challenges in the coming generations of CMOS process technologies.</a>
    {:title}

    F. J. Pollack.
    {:authors}

    In _Symposium on Microarchitecture_, page 2, 1999.
    {:series}
11. <a name="ref11" href="https://doi.org/10.1109/MM.2005.110" target="_blank">Designing reliable systems from unreliable components: The challenges of transistor variability and degradation.</a>
    {:title}

    S. Y. Borkar.
    {:authors}

    In _IEEE Micro_, 25(6):10–16, 2005.
    {:series}
12. <a name="ref12" href="https://doi.org/10.1145/2463209.2488857" target="_blank">Reliable on-chip systems in the nano-era: lessons learnt and future trends.</a>
    {:title}

    J. Henkel, L. Bauer, N. Dutt, P. Gupta, S. R. Nassif, M. Shafique, M. B. Tahoori, and N. Wehn.
    {:authors}

    In _DAC_, pages 99:1–99:10, 2013.
    {:series}
13. <a name="ref13" href="https://doi.org/10.1109/MTDT.2004.1327993" target="_blank">Do we need anything more than single bit error correction (ecc)?</a>
    {:title}

    M. Spica and T. M. Mak.
    {:authors}

    In _MTDT_, pages 111–116, 2004.
    {:series}
14. <a name="ref14" href="https://doi.org/10.1145/2150976.2150989" target="_blank">Cosmic rays don’t strike twice: understanding the nature of DRAM errors and the implications for system design.</a>
    {:title}

    A. A. Hwang, I. A. Stefanovici, and B. Schroeder.
    {:authors}

    In _ASPLOS_, pages 111–122, 2012.
    {:series}
15. <a name="ref15" href="https://doi.org/10.1007/978-3-319-25772-3" target="_blank">Reliable Software for Unreliable Hardware – A Cross Layer Perspective.</a>
    {:title}

    S. Rehman, M. Shafique, and J. Henkel.
    {:authors}

    In _Springer_, 2016.
    {:series}
{:ref}
