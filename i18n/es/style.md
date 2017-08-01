1. Lee [La guía de estilo de C++ de Google](https://google.github.io/styleguide/cppguide.html)
2. Inicia [cpplint](https://pypi.python.org/pypi/cpplint/)
```bash
$ cpplint src/path/to/my/file
```
3. Inicia [clang-format](http://llvm.org/releases/3.8.0/tools/clang/docs/ClangFormat.html) con ```-style=file``` usando el [.clang-format](https://github.com/monero-project/kovri/blob/master/.clang-format)
```bash
$ cd kovri/ && clang-format -i -style=file src/path/to/my/file
```

## Aquí esta lo que no se acomoda por clang-format y difiera de lo propuesto por el estilo C++ de Google

- Mantente con la base del código (verticalmente) para tener consistencia
- Las funciones siempre comienzan con una nueva línea para tener consistencia en el código
- Las nuevas líneas en los argumentos de las funciones, deben tener 4 espacios en *todos* los argumentos

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

- Las expresiones pueden ser rotas antes de los operadores si:
  - La línea es mayor a 80 columnas
  - Hacerlo mejora la documentación

```cpp
if (esta es una expresión muy larga expr1
    && esta es una expresión muy larga expr2
    && esta también es una expresión muy larga expr3)
  HazAlgo();
```

```cpp
return SSUPacket::GetSize()
       + static_cast<std::size_t>(SSUSize::DHPublic)  // Y to complete the DH agreement
       + 1 + m_AddressSize  // 1 byte address size, address size,
       + 2 + 4 + 4          // Port size (2 bytes), relay tag size, time size
       + m_SignatureSize;   // Signature size
```

- Las variables miembro de una clases deben iniciar con ```m_```
- No uses nombres "baratos" en funciones; siempre usa FuncionesConMayusculas()
- No prepongas ```k```  o MACRO_TYPE para todas las constantes
- Usa triple-barra Doxygen ```/// Comentario en C++``` cuando documentes Doxygens
- Documenta todo tu trabajo para Doxygen mientras progresas
- Si el anonimato es una preocupación, mézclalo con la presente guía de contribuidores