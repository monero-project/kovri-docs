1. Leggi la [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
2. Usa [cpplint](https://pypi.python.org/pypi/cpplint/)
```bash
$ cpplint src/path/to/my/file
```
3. Usa [clang-format](http://llvm.org/releases/3.8.0/tools/clang/docs/ClangFormat.html) con ```-style=file``` usando il [.clang-format](https://github.com/monero-project/kovri/blob/master/.clang-format) provvisto
```bash
$ cd kovri/ && clang-format -i -style=file src/path/to/my/file
```

## Qui c'è cos'è correntemente non preso da clang-format e differisce dallo style C++ di Google

- continua ad utilizzare lo stile della code-base presente (verticale) per consistenza
- Newline rompe tutti i parametri della funzione su tutto il database per consistenza
- Quando la funzione args newline rompe, assicurati che ogni indentazione arg sia 4 spazi

```cpp
  /// @brief Constructs SSU header with pre-determined payload type
  explicit SSUHeader(
      SSUPayloadType type);

  /// @brief Constructs SSU header with pre-determined payload type and content
  /// @note Assumes content is valid
  /// @param SSUPayloadType SSU payload type
  /// @param mac Pointer to header's MAC material
  /// @param iv Pointer to header's IV material
  /// @param time Header's timestamp
  SSUHeader(
      SSUPayloadType type,
      std::uint8_t* mac,
      std::uint8_t* iv,
      std::uint32_t time);

  /// @brief Sets MAC from appointed position within header
  /// @note Assumes content is valid (based on position)
  void SetMAC(
      std::uint8_t* mac);

  /// @brief Gets acquired MAC after it has been set when parsed
  /// @return Pointer to MAC material
  std::uint8_t* GetMAC() const;
```

- Le espressioini possono essere rote prima degli operatori se:
  - La linea è più grande di 80 colonne
  - facendolo migliori la documentazione

```cpp
if (this is a very long expr1
    && this is a very long expr2
    && this is also a very long expr3)
  DoSomeThing();
```

```cpp
return SSUPacket::GetSize()
       + static_cast<std::size_t>(SSUSize::DHPublic)  // Y to complete the DH agreement
       + 1 + m_AddressSize  // 1 byte address size, address size,
       + 2 + 4 + 4          // Port size (2 bytes), relay tag size, time size
       + m_SignatureSize;   // Signature size
```

- Le variabili class member dovrebbero essere prefissate con ```m_```
- Non usare nomi "cheap function"; usa sempre MixedCaseFunctions()
- Evita prefissati mixed-case ```k``` e MACRO_TYPE per tutte le costanti
- Usa il Doxygen three-slash ```/// C++ comments``` quando documenti per Doxygen
- Documenta tutto il tuo lavoro per Doxygen mentre procedi
- Se l'anonimità è una preoccupazione, prova a fonderti con lo stile di un altro contributore
