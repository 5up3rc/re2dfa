re2dfa [![License](http://img.shields.io/:license-gpl3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0.html) [![Build Status](https://travis-ci.org/opennota/re2dfa.png?branch=master)](https://travis-ci.org/opennota/re2dfa)
======

re2dfa transforms regular expressions into deterministic finite state machines and outputs Go source code containing the matching function.

# Installation

    go get github.com/opennota/re2dfa

# Usage

    re2dfa ^a+$ main.matchAPlus string

# Benchmarks

Regular expression:

    ^(?:
        <[A-Za-z][A-Za-z0-9\-]*(?:\s+[a-zA-Z_:][a-zA-Z0-9:._-]*(?:\s*=\s*(?:[^"'=<>`\x00-\x20]+|'[^']*'|"[^"]*"))?)*\s*\/?> |

        <\/[A-Za-z][A-Za-z0-9\-]*\s*> |

        <!----> |

        <!--(?:-?[^>-])(?:-?[^-])*--> |

        <[?].*?[?]> |

        <![A-Z]+\s+[^>]*> |

        <!\[CDATA\[[\s\S]*?\]\]>
    )

Benchmark results (Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz):

    BenchmarkFSM1          300000         4049 ns/op          0 B/op        0 allocs/op
    BenchmarkRegexp1        30000        48303 ns/op        112 B/op        7 allocs/op
