# SIDH-RS

The **SIDH-RS** library is an efficient supersingular isogeny-based cryptography library written in Rust language. The library includes the ephemeral Diffie-Hellman key exchange (SIDH) as described in [1,2]. This scheme is conjectured to be secure against quantum computer attacks.

The implementation is intended for use on the `amd64` architecture only -- no
generic field arithmetic implementation is provided. Significant portions of this code are ported from the [Cloudflare's SIDH library](https://github.com/cloudflare/p751sidh). Also portions of the field arithmetic are ported from the [Microsoft Research implementation](https://github.com/Microsoft/PQCrypto-SIDH). This library follows their naming convention, writing "Alice" for the party
using 2^e-isogenies and "Bob" for the party using 3^e-isogenies.

This package does **not** implement SIDH key validation, so it should only be
used for ephemeral Diffie-Hellman, i.e. each keypair should be used at most once.

## Main Features

- Supports ephemeral Diffie-Hellman key exchange.
- Support for Windows OS and Linux OS.      
- Provides optimized implementations of the underlying arithmetic functions for x64 platforms using assembly for Windows and Linux. 
- Includes testing and benchmarking code.

## Warning

This code has **not** yet received sufficient peer review by other qualified
cryptographers to be considered in any way, shape, or form, safe. The library was developed for experimentation purposes.

**USE AT YOUR OWN RISK**

# Installation

To install, add the following to the dependencies section of your project's `Cargo.toml`:

```toml
sidh = "^0.1"
```

Then, in your library or executable source, add:

    extern crate sidh;

By default, the benchmarks are not compiled without the `nightly` and `bench` features. To run the benchmarks, do:

```sh
cargo bench --features="nightly bench"
```

## Documentation

Extensive documentation is available [here](https://docs.rs/sidh).

## License

**SIDH-RS** is licensed under the MIT License; see [`LICENSE`](LICENSE) for details.

Portions of the library are derived from [Cloudflare's Go SIDH imlementation](https://github.com/cloudflare/p751sidh). The x64 field arithmetic implementation is derived from the [Microsoft Research SIDH implementation](https://github.com/Microsoft/PQCrypto-SIDH).

## TODO

We intend to work on the following items:

* Add support for x86 and ARM.
* Improve the documentation.


# References

[1]  Craig Costello, Patrick Longa, and Michael Naehrig, "Efficient algorithms for supersingular isogeny Diffie-Hellman". Advances in Cryptology - CRYPTO 2016, LNCS 9814, pp. 572-601, 2016. 
The extended version is available [here](http://eprint.iacr.org/2016/413). 

[2]  David Jao and Luca DeFeo, "Towards quantum-resistant cryptosystems from supersingular elliptic curve isogenies". PQCrypto 2011, LNCS 7071, pp. 19-34, 2011. 

[3]  Craig Costello, David Jao, Patrick Longa, Michael Naehrig, Joost Renes, and David Urbanik, "Efficient compression of SIDH public keys". Advances in Cryptology - EUROCRYPT 2017, LNCS 10210, pp. 679-706, 2017. 
The preprint version is available [here](http://eprint.iacr.org/2016/963).

[4]   Reza Azarderakhsh, Matthew Campagna, Craig Costello, Luca De Feo, Basil Hess, Amir Jalali, David Jao, Brian Koziel, Brian LaMacchia, Patrick Longa, Michael Naehrig, Joost Renes, Vladimir Soukharev, and David Urbanik, "Supersingular Isogeny Key Encapsulation". Submission to the NIST Post-Quantum Standardization project (to appear soon), 2017.  

[5]  Craig Costello, and Huseyin Hisil, "A simple and compact algorithm for SIDH with arbitrary degree isogenies". Advances in Cryptology - ASIACRYPT 2017 (to appear), 2017. 
The preprint version is available [here](https://eprint.iacr.org/2017/504). 

[6]  Armando Faz-Hernández, Julio López, Eduardo Ochoa-Jiménez, and Francisco Rodríguez-Henríquez, "A faster software implementation of the supersingular isogeny Diffie-Hellman key exchange protocol". Cryptology ePrint Archive: Report 2017/1015, 2017. 
The preprint version is available [here](https://eprint.iacr.org/2017/1015). 

# Contributing

This project has adopted the [Rust Code of Conduct](http://www.rust-lang.org/conduct.html),
with the following additional clauses:

* We respect the rights to privacy and anonymity for contributors and people in
  the community.  If someone wishes to contribute under a pseudonym different to
  their primary identity, that wish is to be respected by all contributors. 


If you have questions or comments, please feel free to email the author. For feature requests, suggestions, and bug reports, please open an issue on this Github repository (or, send an email to the author). Patches are also welcomed as pull requests on this repository, as well as by
email.
