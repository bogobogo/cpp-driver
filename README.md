# c++-driver  ![Driver Status](https://img.shields.io/badge/status-pre--alpha-d6ae86.svg) [![Build Status](https://travis-ci.org/bblfsh/cpp-driver.svg?branch=master)](https://travis-ci.org/bblfsh/java-driver) ![C++ Version](https://img.shields.io/badge/c++%20version-14-0--aa93ea.svg) ![Java Version](https://img.shields.io/badge/java%20version-8.121.13--r0-aa93ea.svg) ![Go Version](https://img.shields.io/badge/go%20version-1.8-63afbf.svg)

Current status: pre-alpha
------------------------

- [X] Experimentation for finding the best plan of attack against this beast (result: org.eclipse.cdt + some adaptation for dealing with the preproccesor).
- [X] Extraction of the AST including unknown or syntactically incorrect symbols.
- [X] Extraction of leading and trailing line or block comments as node properties (note: the comments are parsed but not currently included in the JSON output)
- [X] Request and Response cycle including the reading and writing of the JSON messages.
- [ ] Unrolling of constant-style and function-style preprocessor macros (estimated 2 days, I found some code from Google also using CDT that does basically the same, trough it would have to be adapted to my data and class structure).
- [ ] Generate code paths for all the possibilities caused by all existing #if or #ifdef macros and incorporate them into a branch (estimated 4-5 days).
- [ ] Code documentation and decent unit and integration tests.
- [ ] Adapt/update the existing SDK infrastructure inherited from the Java one.
- [ ] UAST translator.

Bonus:
- [ ] Extraction of whitespace.
- [ ] Re-factorization of the preprocessor branches of the tree to reduce huge splits that could be reworked as a small "normal if" style branches.


Development Environment
-----------------------

Requirements:
- `docker`
- [`bblfsh-sdk`](https://github.com/bblfsh/sdk) _(go get -u github.com/bblfsh/sdk/...)_

To initialize the build system execute: `bblfsh-sdk prepare-build`, at the root of the project. This will install the SDK at `.sdk` for this driver.

To execute the tests just execute `make test`, this will execute the test over the native and the go components of the driver. Use `make test-native` to run the test only over the native component or `make test-driver` to run the test just over the go component.

The build is done executing `make build`. To evaluate the result, a docker container, execute:
`docker run -it bblfsh/cpp-driver:dev-<commit[:6]>`


License
-------

The driver and all the code under the native/ directory is MIT licensed except the
org.cdt jar that is Eclipse 2.0 licensed.

Everything else is GPLv3, see [LICENSE](LICENSE)
