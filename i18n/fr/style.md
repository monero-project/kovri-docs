# Style
1. Lisez le [Guide de Style C++ de Google](https://google.github.io/styleguide/cppguide.html) (particulièrement pour ce qui est du *non-formatting*)
   - Pour de la programmation bash, lisez le [Guide de Style Shell de Google](https://github.com/google/styleguide/blob/gh-pages/shell.xml)
2. Lancez [clang-format](http://clang.llvm.org/docs/ClangFormat.html) avec ```-style=file``` (ce qui utilise notre fichier format [.clang-format](https://github.com/monero-project/kovri/blob/master/.clang-format))
```bash
$ cd kovri/ && clang-format -i -style=file src/path/to/my/file
```
3. Lancez [cpplint](https://github.com/google/styleguide/tree/gh-pages/cpplint) (qui utilise notre fichier [CPPLINT.cfg](https://github.com/monero-project/kovri/blob/master/CPPLINT.cfg)) pour capturer tous les problèmes qui ont été manqués par *clang-format*
```bash
$ cd kovri/ && cpplint src/path/to/my/file && [éditez le fichier manuellement pour résoudre les problèmes détectés]
```

### Plugins

- Intégration Vim
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#vim-integration)
  - [clang-format avec solution de contournement pour ubuntu 16.04](http://stackoverflow.com/questions/39490082/clang-format-not-working-under-gvim)
  - [cpplint.vim](https://github.com/vim-syntastic/syntastic/blob/master/syntax_checkers/cpp/cpplint.vim)
- Intégration Emacs
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#emacs-integration) + [clang-format.el](https://llvm.org/svn/llvm-project/cfe/trunk/tools/clang-format/clang-format.el)
  - [flycheck-google-cpplint.el](https://github.com/flycheck/flycheck-google-cpplint)

## Voici ce qui n'est pour l'instant pas capturé par *clang-format* et qui diffère du style C++ proposé par Google

- Évitez le préfixe ```k``` et ```MACRO_TYPE``` pour les constantes
- Utilisez les 3 slashs ```/// C++ comments``` quand vous documentez pour Doxygen
- Essayez de documenter tout votre travail pour Doxygen au fur et à mesure
- Si l'anonymat est important pour vous, essayez de fondre votre style sur celui des autres contributeurs

## Vérifications facultatives
1. [cppdep](https://github.com/rakhimov/cppdep)
   pour la dépendance des composants, l'isolation et les *include*.
2. [cppcheck](https://github.com/danmar/cppcheck/) pour les analyses statiques
   (en complément à *Coverity*).
3. [lizard](https://github.com/terryyin/lizard) pour la complexité cyclomatique.
