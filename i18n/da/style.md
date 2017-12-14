# Stil
1. Læs [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html) (særligt for ikke-formaterede stil reference)
   - Hvis du programmerer i bash, læs [Google's Shell Style Guide](https://github.com/google/styleguide/blob/gh-pages/shell.xml)
2. Kør [clang-format](http://clang.llvm.org/docs/ClangFormat.html) med ```-style=file``` (som bruger den vi har udleveret [.clang-format](https://github.com/monero-project/kovri/blob/master/.clang-format))
```bash
$ cd kovri/ && clang-format -i -style=file src/path/to/my/file
   ```
3. Kør [cpplint](https://github.com/google/styleguide/tree/gh-pages/cpplint) (som bruger den vi har udleveret [CPPLINT.cfg](https://github.com/monero-project/kovri/blob/master/CPPLINT.cfg)) til at fange nogle problemer der slap igennem clang-format
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
  
  ## Her er hvad der ikke bliver fanget af clang-format på nuværende tidspunkt og adskiller sig fra Google's foreslået C++ style
  
  - Undgå at blande små og store bogstaver  ```k``` og MACRO_TYPE for alle konstanter
  - Brug doxygen Tre-slash ```/// C++ kommentarer``` når du dokumenterer Doxygen
  - Prøv at dokumentere alt dit arbejde Doxygen 
  - Hvis anonymitet er et problem, prøv at snige dig ind med en nuværende bidragyderes stil

## Valgfri kontrol
1. [cppdep](https://github.com/rakhimov/cppdep)
   for komponentafhængighed, fysisk isolering og inkludere kontrol.
2. [cppcheck](https://github.com/danmar/cppcheck/) for statisk analyse
   (komplementær til Coverity).
3. [lizard](https://github.com/terryyin/lizard) for kodekompleksitetskontrol.
