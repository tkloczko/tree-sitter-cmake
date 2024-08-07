# tree-sitter-cmake

CMake project for building [Tree-sitter](http://tree-sitter.github.io/tree-sitter/).

## About

Tree-sitter is an excellent project. It provides a reusable interface for parsing many different programming languages.
But because it's aimed primarily for consumption in Node.js, it uses GYP as the build system.
GYP is terrible for modern-day developers needs.

This project aims to provide an integrated way to use Tree-sitter in CMake projects.
Just use this to build and install Tree-sitter, as well as the CMake config files.

As a bonus, it even includes several Tree-sitter languages in library form.

I originally wrote this to make importing Tree-sitter into a project I am
working on. I decided to release this separate in case anyone finds it useful.

## Getting Started

This project includes Tree-sitter and sub-projects as Git Submodules, so make
sure you add the submodules when you checkout the source.

```bash
$ git clone --recurse-submodules https://gtilab.inria.fr/dtk/tree-sitter-cmake.git
$ mkdir tree-sitter-cmake/build
$ cd tree-sitter-cmake/build
$ cmake .. -DCMAKE_INSTALL_PREFIX=$CONDA_PREFIX -DCMAKE_BUILD_TYPE=Release ..
$ cmake --build .
$ cmake --build . --target install
```

The above commands should check out the git submodules this project pulls in.
Otherwise, CMake will check out the git submodules when run.

## Using

```cmake
find_package(Tree-Sitter CONFIG)
# Gives Tree-Sitter::Tree-Sitter

find_package(Tree-Sitter CONFIG REQUIRED CPP Rust)
# Gives Tree-Sitter::Tree-Sitter, Tree-Sitter::Tree-Sitter-CPP, Tree-Sitter::Tree-Sitter-Rust
```

The complete list of targets is:

* `Tree-Sitter::Tree-Sitter`
* `Tree-Sitter::Tree-Sitter-C`
* `Tree-Sitter::Tree-Sitter-CPP`
* `Tree-Sitter::Tree-Sitter-C-Sharp`
* `Tree-Sitter::Tree-Sitter-Go`
* `Tree-Sitter::Tree-Sitter-Java`
* `Tree-Sitter::Tree-Sitter-JavaScript`
* `Tree-Sitter::Tree-Sitter-Python`
* `Tree-Sitter::Tree-Sitter-Rust`
* `Tree-Sitter::Tree-Sitter-TypeScript`

I will probably add more language parsers later.

Also provided is a new header file (`tree_sitter/langs.h`), that contains the
definitions for all the language parsers included.

```c
const TSLanguage *tree_sitter_c();
const TSLanguage *tree_sitter_cpp();
const TSLanguage *tree_sitter_c_sharp();
const TSLanguage *tree_sitter_go();
const TSLanguage *tree_sitter_java();
const TSLanguage *tree_sitter_javascript();
const TSLanguage *tree_sitter_python();
const TSLanguage *tree_sitter_rust();
const TSLanguage *tree_sitter_typescript();
```

## License

This is nothing more than a simple CMake script and some supporting files.
It is released as Public Domain.

This is not endorsed by the Tree-sitter developers. If they contact me and ask
me to remove this I will.
