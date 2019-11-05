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

## Medical Imaging Informatics ; Systems Development

<!-- 
Digital medical imaging in healthcare institutions plays a valuable role in medical diagnosis, decision support, and treatment procedures. As the requirements and expectations of these systems increase, so do the concerns for fast, safe, and usable tools for the retrieval and manipulation of medical imaging data.
-->

<div class="container">
<b>Medical Imaging</b>
<ul>
  <li>Plays an important role.</li>
  <li>Evolving quickly.</li>
  <li>Increasing reuirements.</li>
  <ul>
    <li>More data, larger studies</li>
    <li>Demands for fast visualization \& decision support</li>
  </ul>
  <li class="fragment" data-fragment-index="0">Dependent on the DICOM standard.</li>
<ul>
</div>

.

# <img src="img/rust-logo-blk.svg" style="display:inline" /> What is Rust?

- Multi-paradigm programming language
- Started by Graydon Hoare, intern at Mozilla.
  - Later on deferred to a development team.
- 1.0 released in May 2015.
  - New releases every 6 weeks. (current: 1.38.0)
  - First major release: Rust 2018 edition 

<img class="fragment" data-fragment-index="0" src="img/fearless-concurrency-with-rust.png" />

.

#### Performance

- Abstraction without overhead

```rust
let new_services: BTreeMap<_, _> = services.into_iter()
   .filter(|(name, _)| name.ends_with("_1"))
   .collect();
```

.

#### Memory safety without garbage collector

<div class="container">
<div class="column column-one">
<ul>
<li>Performance with less risks</li>
<li>Ownership & borrowing mechanism</li>
<ul>
  <li>Automatic resource management</li>
  <li>Prevent memory conflicts</li>
</ul>
</div>
<div class="column column-two">
<img src="img/rust_ownership_53.gif" />
</div>
</div>

.

### Concurrency


- No data races.


```rust

```

.

## Use cases


.


## Ecosystem \& Community

- Official package manager: **Cargo**
- Public registry: <crates.io>


.

### Other worthy mentions

- Amazon: Firecracker
- Google: Fuchsia project
- Facebook: Libra


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

