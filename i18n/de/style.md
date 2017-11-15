# Style
1. Read [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html) (particularly for non-formatting style reference)
   - If bash programming, read [Google's Shell Style Guide](https://github.com/google/styleguide/blob/gh-pages/shell.xml)
2. Run [clang-format](http://clang.llvm.org/docs/ClangFormat.html) with ```-style=file``` (which uses our provided [.clang-format](https://github.com/monero-project/kovri/blob/master/.clang-format))
```bash
$ cd kovri/ && clang-format -i -style=file src/path/to/my/file
```
3. Run [cpplint](https://github.com/google/styleguide/tree/gh-pages/cpplint) (which uses our provided [CPPLINT.cfg](https://github.com/monero-project/kovri/blob/master/CPPLINT.cfg)) to catch any issues that were missed by clang-format
```bash
$ cd kovri/ && cpplint src/path/to/my/file && [edit file manually to apply fixes]
```

### Plugins

- Vim integration
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#vim-integration)
  - [clang-format ubuntu 16.04 vim workaround](http://stackoverflow.com/questions/39490082/clang-format-not-working-under-gvim)
  - [cpplint.vim](https://github.com/vim-syntastic/syntastic/blob/master/syntax_checkers/cpp/cpplint.vim)
- Emacs integration
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#emacs-integration) + [clang-format.el](https://llvm.org/svn/llvm-project/cfe/trunk/tools/clang-format/clang-format.el)
  - [flycheck-google-cpplint.el](https://github.com/flycheck/flycheck-google-cpplint)

## Here's what's currently not caught by clang-format and differs from Google's proposed C++ style

- Avoid prepended mixed-case ```k``` and MACRO_TYPE for all constants
- Use Doxygen three-slash ```/// C++ comments``` when documenting for Doxygen
- Try to document all your work for Doxygen as you progress
- If anonymity is a concern, try to blend in with a present contributor's style

## Optional Checks
1. [cppdep](https://github.com/rakhimov/cppdep)
   for component dependency, physical insulation, and include checks.
2. [cppcheck](https://github.com/danmar/cppcheck/) for static analysis
   (complementary to Coverity).
3. [lizard](https://github.com/terryyin/lizard) for code complexity checks.
