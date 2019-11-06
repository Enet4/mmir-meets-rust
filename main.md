# Medical Imaging Informatics meets Rust

## An introduction to the Rust programming language and the DICOM-rs project

<div style="font-size: 24pt; text-align: left; margin-top: 96px; margin-bottom: 24px;">Eduardo Pinho</div>
<br>

<div style="font-size: 12pt; text-align: right; margin: 1cm;">9th November 2019</div>
<div class="foot" style="margin-left: 0pt; margin-right: 0pt; margin-bottom: 0pt; background-color: white;">
</div>

---

## Table of Contents

<br/>

1. The Rust programming language
2. DICOM-rs project

---

## Medical Imaging Informatics

<!-- 
Digital medical imaging in healthcare institutions plays a valuable role in medical diagnosis, decision support, and treatment procedures. As the requirements and expectations of these systems increase, so do the concerns for fast, safe, and usable tools for the retrieval and manipulation of medical imaging data.
-->

<div class="container">
<ul>
  <li>Plays an important role.</li>
  <li>Evolving quickly.</li>
  <li>Increasing requirements.</li>
  <ul>
    <li>More data, larger studies</li>
    <li>Demands for fast visualization & better decision support</li>
  </ul>
  <li class="fragment" data-fragment-index="0">Dependent on the DICOM standard.</li>
  <ul>
    <li class="fragment" data-fragment-index="0">Value in good implementations.</li>
    <li class="fragment" data-fragment-index="1"><b>DICOM-rs</b>: an implementation in Rust</li>
  </ul>
<ul>
</div>

.

# <img src="img/rust-logo-blk.svg" style="display:inline" /> What is Rust?

- Multi-paradigm programming language
- Started by Graydon Hoare, intern at Mozilla.
  - Later on deferred to specialized teams.
- 1.0 released in May 2015.
  - New releases every 6 weeks. (current: 1.38.0)
  - First major release: Rust 2018 edition 

<img class="fragment" data-fragment-index="0" src="img/fearless-concurrency-with-rust.png" />

.

![](img/triangle.svg)

.

#### Performance

- Compiled (LLVM)
- Minimal runtime
- Predictive, no garbage collector
- Abstraction without overhead

```rust
let new_services: BTreeMap<_, _> = services.into_iter()
   .filter(|(name, _)| name.ends_with("_1"))
   .collect();
```

.

So I heard you like Python.

```python
def is_blank(s):
    return not s or s.isspace()
```

<span class="fragment" data-fragment-index="0">400MB text file: 2.08s</span>

.

Or maybe you like the speed of C++?

```c++
#include <string>
#include "utf8.h"

bool is_blank(const std::string& line) {
    auto it = line.begin();
    auto end = line.end();
    while (it != end) {
        auto c = utf8::next(it, end);
        if (!std::iswspace(c)) return false;
    }
    return true;
}
```

- Faster: 1.45s
- Without string checking (`utf8::is_valid`): 0.30s
- But more unwieldy

.

Rust 

<img width="200px" src="img/rustacean-flat-happy.svg" />

```rs
fn is_blank(s: &str) -> bool {
    s.chars().all(|c| c.is_whitespace())
}
```

- Nice one-liner
- Very fast! (0.45s)
- UTF-8 checked

.

### Memory safety

C and C++

<ul>
<li>use after free</li>
<li>double pointer</li>
<li>memory leaks</li>
<li>buffer overreads</li>
<li>data races</li>
<li class="fragment" data-fragment-index="0"> a single breach is dangerous</li>
</ul>

.

![](img/ms-vulnerability-graph.png)

~70% of the vulnerabilities Microsoft assigns a CVE each year continue to be memory safety issues

.

#### Memory safety without garbage collector

<div class="container">
<div class="column column-one">
<ul>
<li>Ownership & borrowing mechanism</li>
<ul>
  <li>Restricted aliasing</li>
  <li>Moving, Copying, Borrowing</li>
  <li>Lifetime-aware type system</li>
</ul>
<li class="fragment" data-fragment-index="0">Prevent memory conflicts</li>
</div>
<div class="column column-two">
<img src="img/rust_ownership_53.gif" />
</div>
</div>

.

<img width="400px" src="img/rust-move-copy-borrow.png" />

<small>https://rufflewind.com/img/rust-move-copy-borrow.png</small>

.

#### Concurrency

- Restricted aliasing prevents data races.

```rust
use rayon::prelude::*;

fn mandelbrot() -> Vec<u32> {
    (-10..=10).flat_map(|i| (-20..=5).map(move |j| (i, j)))
        .par_iter() // <-- parallel computation
        .map(|(re, im)| mandel(Complex64::new(rs as f64, im as f64)))
        .collect()
}
```

.


#### Productivity

- Powerful type system
- Official package manager: **Cargo**
- Public registry: [crates.io](https://crates.io)
- Stability concerns.
   - Edition mechanism (Rust 2018)
   - No Rust 2.0

.

### Other worthy mentions

- Amazon: Firecracker microVM
- Google: Fuchsia project
- Facebook: Libra (Blockchain)
- Mozilla: Firefox Quantum
- npm: package registry backend


In bioinformatics:

- https://rust-bio.github.io

---

# DICOM-rs

.


---

# Conclusion

<span class="fragment" data-fragment-index="0">Want to learn Rust? → https://www.rust-lang.org ←</span>

<span class="fragment" data-fragment-index="1">Contribute to DICOM-rs: <img style="vertical-align: bottom" height="32" src="img/github.png" /> https://github.com/Enet4/dicom-rs</span>

.

<h3 style="margin-top: 4cm">Thank you!</h3>

![](https://rustacean.net/more-crabby-things/dancing-ferris.gif)

<div style="font-size">
</div>
<div class="foot" style="font-size: 18pt; margin-top: 6cm; margin-left: 0pt; margin-right: 0pt; margin-bottom: 0pt;">
   <a href="https://github.com/Enet4"><img style="vertical-align: bottom" height="46" src="img/github.png" /> Enet4</a>
   <br>
   <a href="https://www.twitter.com/E_net4"><img style="vertical-align: bottom" height="46" src="img/twitter.png" />@E_net4</a>
</div>

Note: This concludes my presentation. You may find me on Twitter or GitHub. Thank you!

---

