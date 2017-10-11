# Stile
1. Leggi la [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html) (in particolare riguardo allo stile non formattato)
   - Se stai programmando in bash, leggi la [Google's Shell Style Guide](https://github.com/google/styleguide/blob/gh-pages/shell.xml)
2. Usa [clang-format](http://llvm.org/releases/3.8.0/tools/clang/docs/ClangFormat.html) con ```-style=file``` usando il [.clang-format](https://github.com/monero-project/kovri/blob/master/.clang-format) provvisto
```bash
$ cd kovri/ && clang-format -i -style=file src/path/to/my/file
```
3. Usa [cpplint](https://pypi.python.org/pypi/cpplint/) (che usa il nostro [CPPLINT.cfg](https://github.com/monero-project/kovri/blob/master/CPPLINT.cfg)) per trovare eventuali problemi non trovati da clang-format
```bash
$ cd kovri/ && cpplint src/path/to/my/file && [modifica il file manualmente per applicare le modifiche]
```

### Plugins

- Integrazione di Vim
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#vim-integration)
  - [clang-format ubuntu 16.04 vim workaround](http://stackoverflow.com/questions/39490082/clang-format-not-working-under-gvim)
  - [cpplint.vim](https://github.com/vim-syntastic/syntastic/blob/master/syntax_checkers/cpp/cpplint.vim)
- Integrazione Emacs
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#emacs-integration) + [clang-format.el](https://llvm.org/svn/llvm-project/cfe/trunk/tools/clang-format/clang-format.el)
  - [flycheck-google-cpplint.el](https://github.com/flycheck/flycheck-google-cpplint)

## Qui c'è cos'è correntemente non catturato da clang-format e differisce dallo style C++ di Google

- Evitare anteposti mixed-case ```k``` e MACRO_TYPE per tutte le costanti
- Usa i tre slash di Doxygen ```/// C++ comments``` quando crei documentazione per Doxygen
- Prova a documentare tutto il tuo lavoro per Doxygen mentre progredisci
- Se l'anonimato è una preoccupazione, prova a fondere il tuo stile con quello di un contributore corrente

## Controlli Opzionali
1. [cppdep](https://github.com/rakhimov/cppdep)
   per le dipendenze dei componenti, isolamento fisico, e includere controlli.
2. [cppcheck](https://github.com/danmar/cppcheck/) per analisi statica
   (complementare a Coverity).
3. [lizard](https://github.com/terryyin/lizard) per controlli sulla complessità del codice.
