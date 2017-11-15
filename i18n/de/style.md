# Stil
1. Lesen Sie [Googles C++-Stilleitfaden](https://google.github.io/styleguide/cppguide.html) (insbesondere für Referenzen zu formatfreiem Stil)
   - Falls Sie in der Bash programmieren, lesen Sie [Googles Shell-Stilleitfaden](https://github.com/google/styleguide/blob/gh-pages/shell.xml)
2. Führen Sie [clang-format](http://clang.llvm.org/docs/ClangFormat.html) mit ```-style=file``` (das unser bereitgestelltes [.clang-format](https://github.com/monero-project/kovri/blob/master/.clang-format) nutzt) aus
```bash
$ cd kovri/ && clang-format -i -style=file src/path/to/my/file
```
3. Führen Sie [cpplint](https://github.com/google/styleguide/tree/gh-pages/cpplint) (das unser bereitgestelltes [CPPLINT.cfg](https://github.com/monero-project/kovri/blob/master/CPPLINT.cfg) nutzt) aus, um alle Probleme zu erfassen, die vom clang-format verpasst wurden
```bash
$ cd kovri/ && cpplint src/path/to/my/file && [edit file manually to apply fixes]
```

### Plugins

- Vim-Integration
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#vim-integration)
  - [clang-format ubuntu 16.04 vim Workaround](http://stackoverflow.com/questions/39490082/clang-format-not-working-under-gvim)
  - [cpplint.vim](https://github.com/vim-syntastic/syntastic/blob/master/syntax_checkers/cpp/cpplint.vim)
- Emacs-Integration
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#emacs-integration) + [clang-format.el](https://llvm.org/svn/llvm-project/cfe/trunk/tools/clang-format/clang-format.el)
  - [flycheck-google-cpplint.el](https://github.com/flycheck/flycheck-google-cpplint)

## Folgendes wird derzeit von clang-format nicht erfasst und unterscheidet sich von Googles vorgeschlagenem C++-Stil

- Vermeiden Sie ein vorangestelltes *mixed-case* ```k``` und MACRO_TYPE für alle Konstanten
- Verwenden Sie Doxygens drei Slashes ```/// C++ comments```, wenn Sie für Doxygen kommentieren
- Versuchen Sie, all Ihre Arbeit für Doxygen zu dokumentieren, während Sie Fortschritte machen
- Falls Ihnen Anonymität ein Anliegen ist, versuchen Sie sich dem Stil eines anderen Mitwirkenden anzugleichen

## Optionale Checks
1. [cppdep](https://github.com/rakhimov/cppdep)
   für Komponentenabhängigkeit, physische Isolierung und *include*-Checks.
2. [cppcheck](https://github.com/danmar/cppcheck/) zur statischen Analyse
   (Ergänzung zu Coverity).
3. [lizard](https://github.com/terryyin/lizard) für Code-Komplexitäts-Checks.
