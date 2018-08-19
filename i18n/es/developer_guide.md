# Pautas
- Nuestro objetivo es el cumplimiento completo de C++ 11/14; por favor use esto para su ventaja
- Utilice la biblioteca estándar y las bibliotecas de dependencia siempre que sea posible

## Respuesta de vulnerabilidad
- Nuestro [Proceso de Respuesta de Vulnerabilidad](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md) fomenta la divulgación responsable
- También estamos disponibles a través de [HackerOne](https://hackerone.com/monero)

## Estilo
1. Lea [Guía de estilo de C ++ de Google](https://google.github.io/styleguide/cppguide.html) (particularmente para referencia de estilo sin formato)
   - Si se trata de programación bash, lea [Guía de estilo de shell de Google](https://github.com/google/styleguide/blob/gh-pages/shell.xml)
2. Para los archivos que solo contengan trabajo nuevo, ejecute [clang-format](http://clang.llvm.org/docs/ClangFormat.html) con ```-style = file``` (que usa nuestro [.clang-format](https://github.com/monero-project/kovri/blob/master/.clang-format) proporcionado)
```bash
$ cd kovri / && clang-format -i -style=file /ruta/a/mi/archivo
```
3. Para archivos con trabajo mixto (existente + nuevo), ejecute [clang-format](http://clang.llvm.org/docs/ClangFormat.html) selectivamente solo sobre las líneas directamente relacionadas con el nuevo trabajo.
   - Ver la documentacion de [vim](http://clang.llvm.org/docs/ClangFormat.html#vim-integration) y [emacs](http://clang.llvm.org/docs/ClangFormat.html#emacs-integration ) para ejemplos de configuración de combinaciones de teclas para complementos `clang-format`.
4. Ejecute [cpplint](https://github.com/google/styleguide/tree/gh-pages/cpplint) (que utiliza nuestro [CPPLINT.cfg](https://github.com/monero-project/kovri/blob/master/CPPLINT.cfg)) para detectar cualquier problema que se haya perdido por el formato clang
```bash
$ cd kovri / && cpplint src/ruta/a/mi/archivo && [edita el archivo manualmente para aplicar los cambios]
```

### Plugins

- Integrcion con VIM
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#vim-integration)
  - [clang-format ubuntu 16.04 vim](http://stackoverflow.com/questions/39490082/clang-format-not-working-under-gvim)
  - [cpplint.vim](https://github.com/vim-syntastic/syntastic/blob/master/syntax_checkers/cpp/cpplint.vim)
- Integracion a Emacs
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#emacs-integration) + [clang-format.el](https://llvm.org/svn/llvm-project/cfe/trunk/tools/clang-format/clang-format.el)
  - [flycheck-google-cpplint.el](https://github.com/flycheck/flycheck-google-cpplint)

### Enmiendas al estilo de C ++ propuesto por Google

- Evite el caso mixto ```k``` y el MACRO_TYPE antes de la mezcla para todas las constantes
- Utilice Doxygen three-slash ```/// C ++ comments``` al documentar para Doxygen
- Trate de documentar todo su trabajo para Doxygen a medida que progresa
- Si el anonimato es una preocupación, intente mezclarse con el estilo de un colaborador actual

### Verificaciones opcionales
1. [cppdep](https://github.com/rakhimov/cppdep)
    para la dependencia de los componentes, el aislamiento físico e incluir controles.
2. [cppcheck](https://github.com/danmar/cppcheck/) para el análisis estático
    (complementario a Coverity).
3. [lizard](https://github.com/terryyin/lizard) para verificar la complejidad del código.

## Envío de tu trabajo
Para contribuir con su trabajo, proceda con lo siguiente:

1. Haz un [Fork](https://help.github.com/articles/fork-a-repo/) de Kovri
2. Revisa la sección de estilo de este documento
3. Cree una [rama](https://git-scm.com/book/es/v2/Git-Branching-Basic-Branching-and-Merging)
   - Actualmente no tenemos ningún tag por estar en Alpha. Por ahora, puedes basar tu trabajo desde la rama master.
4. Haz cambios
   - En general, los commits deben ser [atomicos](https://en.wikipedia.org/wiki/Atomic_commit#Atomic_commit_convention) y los diffs deben ser fáciles de leer.
   - Intente no mezclar correcciones de formato con confirmaciones sin formato
5. Sé cortés con el registro de git
   - El título de commit debe preponer class u otro aspecto del proyecto. Por ejemplo, "HTTPProxy: implementado depurador de User-Agent. Arregla #193." o "Garlic: arregla padding no inicializado en ElGamalBlock".
   - Los mensajes del Commit deben ser una frase descriptiva por defecto, considerando una línea de asunto de (50 caracteres máximo), una línea en blanco y una explicación detallada por párrafo(s) separado(s) - a menos que el título se auto-explique.
   - Si un commit en particular hace referencia otro issue, pon una referencia. Por ejemplo, *Leer #123*, o *Arregla #123*. Esto ayudará a resolver issues cuando se mezclen con `master`.
   - Si un commit en particular se vuelve a establecer después de la colaboración dentro de un pull request, consulte el número de pull request dentro del mensaje del commit. Por ejemplo; *Referencia #123*
6. [**Firma**](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work) tu(s) commit(s), y si eres un colaborador nuevo, haz un pull request para agregar tu clave PGP a nuestro repositorio. (ver contribuir)
7. Envía tu pull-request a la branch ```master```
   - El cuerpo de los pull requests deben contener una descripción adecuada de lo que hace el parche, y proveer una justificación o razonamiento para el parche (cuando sea apropiado). Debes incluir referencias a cualquier discusión como issues, chats, o IRC.

## Propuestas
Para contribuir una propuesta, por favor lee nuestros [issues abiertos](https://github.com/monero-project/kovri/issues) para ver los ya existentes. Si lo que quieres proponer no está ahí, entonces [abre un nuevo issue](https://github.com/monero-project/kovri/issues/new).

A pesar de que nuestro C4 dicta, que nosotros mezclamos todo, pedimos abrir una propuesta por las siguientes razones:

1. Una propuesta abre la comunicación
2. Una propuesta muestra que el colaborador respeta la opinión de todos los colaboradores del proyecto
3. Una propuesta permite a los colaboradores opinar en un foro abierto
4. Una propuesta ahorra tiempo si un colaborador ya está trabajando en algo similar
5. Una propuesta previene catástrofes, y errores, o permite a los colaboradores prepararse para catástrofes, o errores

*No* abrir una nueva propuesta *no* va a prevenirte de colaborar; nosotros mezclaremos tu PR - pero una propuesta es altamente recomendada.

## TODO
- Haz una búsqueda rápida en el código base por ```TODO(sin asignar):``` y/o elige un issue y ¡comienza a trabajar!
- Si creas un TODO, asígnatelo a ti mismo o escribe ```TODO(sin asignar):```

## Fuzz testing

Para [referencia](http://llvm.org/docs/LibFuzzer.html) : "LibFuzzer esta bajo desarrollo activo caso que necesitaras la versión actual (o la mas reciente) del compilador Clang"

Obtén una versión reciente de Clang:

```bash
$ cd ~/ && mkdir TMP_CLANG && git clone https://chromium.googlesource.com/chromium/src/tools/clang TMP_CLANG/clang
$ ./TMP_CLANG/clang/scripts/update.py
$ cd --
```

Obtén libFuzzer:

```bash
$ git clone https://chromium.googlesource.com/chromium/llvm-project/llvm/lib/Fuzzer contrib/Fuzzer
```

Compila kovri con fuzz testing habilitado:

```bash
$ PATH="~/third_party/llvm-build/Release+Asserts/bin:$PATH" CC=clang CXX=clang++ make fuzz-tests
```

Uso (Ejemplo de RouterInfo):

```bash
mkdir RI_CORPUS MIN_RI_CORPUS
find ~/.kovri/core/network_database/ -name "router_info*" -exec cp {} RI_CORPUS \;
./build/kovri-util fuzz --target=routerinfo -merge=1 MIN_RI_CORPUS RI_CORPUS
./build/kovri-util fuzz --target=routerinfo -jobs=2 -workers=2 MIN_RI_CORPUS
```

# Seguros de calidad

El siguiente modelo es el propuesto para el trabajo de QA. Mientras se tiene una naturaleza linear, cualquier fase puede ser trabajada individualmente si se necesita - mientras que todas las fases eventualmente son revisadas.

## Fase 1: Revisión básica

- Revisa nuestros issues abiertos en nuestro [Issue Tracker](https://github.com/monero-project/kovri/issues/)
- Revisa nuestro [Proceso de respuesta de vulnerabilidades](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md)
- Todo el código debe adherirse a nuestras guías de contribución
- Anotar todas las áreas que necesitan ser mejoradas (mentalmente o en el código)
- Crear TODOs y asignarse de ser posible

## Fase 2: Revisión de especificaciones /  Implementación / Documentación de código

- Completa las revisiones de especificaciones por módulos; ejemplo: Streaming, I2PControl, etc.
  - El código debe estar en-linea con las partes esenciales de las especificaciones que se mantendrán iguales (o en mejores) niveles de anonimato que provee java I2P
  - Refactorizar/implementar/parchear donde/cuando se necesite.
- Asegurarse de cumplir con la implementación en C++11/14
  - realizar la Fase 2 si se necesita
- Resolver todo lo relacionado a los TODOs
- Documentar el código tanto como sea posible con comentarios en-linea y Doxygens
  - El código debe ser entendible desde programadores novatos a experimentados
  - El código debe guiar al lector a un mejor entendimiento de I2P
    - I2P es un código muy largo y complejo, así que el nuestro debe ser un reemplazo de documentación y no simplemente un suplemento (esto puede ser un objetivo tedioso pero muy beneficioso en términos de mantenimiento y vida del software)

## Fase 3: Revisión criptográfica / auditoria de seguridad

- Asegurarse que la criptografía este al día y correctamente implementada
- Establecer cada vector para explotaciones conocidas
  - Mantener esos vectores en mente cuando se escriban pruebas
- Romper Kovri en cada forma posible
  - Arreglar lo que rompes
- Siempre usa librerías de confianza, y bien escritas cuando sea posible
  - Evita código hecho-en-casa, ad-hoc, *Yo se mas que la comunidad, por eso mi código es mejor*
- Busca una segunda, tercera y mas opiniones, antes de proceder a la siguiente fase

## Fase 4: Arreglar bugs / Pruebas / Profiling

- Resolver los bugs/issues de prioridad
- Escribir pruebas de unit-test para cada modulo
  - Correr pruebas, y correrlas de nuevo
  - Revisa los resultados por completo. Parchea si se necesita, refactoriza si es necesario
- Asegúrate que la automatización este corriendo a intervalos regulares
  - valgrind, doxygen, clang-format
  - Parchea si es necesario, refactoriza si es necesario

## Fase 5: Conferir

- Conferir con colegas y la comunidad
  - Conferir debe ser públicamente via issues, reuniones, y/o IRC
- Aceptar toda retroalimentación y, en respuesta, producir resultados tangibles
- Si se satisface, proceder con la siguiente fase, si no repetir esta fase, (o comenzar de una fase previa)

## Fase 6: Repetir todo desde el inicio

# [Código de conducta (22/C4.1)](http://rfc.zeromq.org/spec:22)

## Licencia

Copyright (c) 2009-2015 Pieter Hintjens.

This Specification is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This Specification is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, see <http://www.gnu.org/licenses>.

## Lenguaje

Las palabras "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", y "OPTIONAL" en este documento, deben ser interpretadas como esta descrito en el RFC 2119.

## Metas

C4 está hecho para ser un modelo óptimo de colaboración para proyectos de software de código abierto. Y se especifican los siguientes objetivos:

- Maximizar la escala y la diversidad de la comunidad en torno a un proyecto, reduciendo la fricción para los nuevos colaboradores y creando un modelo de participación escalado con fuertes retroalimentaciones positivas;
- Para aliviar las dependencias de individuos clave, separando diferentes conjuntos de habilidades para que haya un mayor grupo de competencia en cualquier dominio requerido;
- Permitir que el proyecto se desarrolle de forma más rápida y precisa, aumentando la diversidad del proceso de toma de decisiones;
- Apoyar el ciclo de vida natural de las versiones del proyecto, desde el experimental hasta el estable, permitiendo la experimentación segura, el fracaso rápido y el aislamiento del código estable;
- Reducir la complejidad interna de los repositorios de proyectos, facilitando así la participación de los contribuyentes y reduciendo el margen de error;
- Reforzar la propiedad colectiva del proyecto, lo que aumenta el incentivo económico a los contribuyentes y reduce el riesgo de secuestro por entidades hostiles.

## Diseño

### Preliminares

- El proyecto USARÁ el sistema de control de revisión distribuido git.
- El proyecto ESTARÁ alojado en github.com o equivalente, llamado "Plataforma".
- El proyecto USARÁ la plataforma de Tracker de issues.
- El proyecto DEBERÁ tener directrices claramente documentadas para el estilo de código.
- Un "Colaborador" es una persona que desea proporcionar un parche, siendo un conjunto de commits que resuelven algún problema claramente identificado.
- Un "Mantenedor" es una persona que fusiona parches al proyecto. Los mantenedores no son desarrolladores; su trabajo es hacer cumplir el proceso.
- Los colaboradores NO TENDRÁN acceso commit del repositorio a menos que sean Mantenedores
- Los mantenedores TENDRÁN acceso de commit al repositorio.
- Todos, sin distinción ni discriminación, TENDRÁN el mismo derecho de convertirse en un Colaborador en los términos de este contrato.

### Licencia y propiedad

- El proyecto DEBE utilizar una licencia compartida, como la GPLv3 o una variante de la misma (LGPL, AGPL), o la MPLv2.
- Todas las contribuciones al código fuente del proyecto ("parches") DEBERÁN utilizar la misma licencia que el proyecto.
- Todos los parches son propiedad de sus autores. No habrá ningún proceso de asignación de derechos de autor.
- Los derechos de autor del proyecto serán de propiedad colectiva de todos sus colaboradores.
- Cada Contribuyente DEBERÁN ser responsable de identificarse en la lista de Colaboradores del proyecto.

### Requisitos del parche

- Los Mantenedores y los colaboradores DEBEN tener una cuenta en la plataforma y DEBERÁN usar sus nombres verdaderos o un alias conocido.
- Un parche DEBE ser una respuesta mínima y precisa a exactamente un problema identificado y acordado.
- Un parche DEBE adherirse a las directrices de estilo de código del proyecto si se definen.
- Un parche DEBE adherirse a la "Evolución de los contratos públicos" directrices definidas a continuación.
- Un parche NO incluirá código no trivial de otros proyectos a menos que el Colaborador sea el autor original de ese código.
- Un parche DEBE compilar de forma limpia y pasar las auto pruebas del proyecto en al menos la plataforma objetivo principal.
- Un mensaje de commit de parche DEBERÍA consistir en una sola línea corta (menos de 50 caracteres) que resume el cambio, seguido opcionalmente por una línea en blanco y luego una descripción más completa.
- Un "Patch Correcto" es aquel que satisface los requisitos anteriores.

### Proceso de desarrollo

- El cambio en el proyecto deberá ser gobernado por el patrón de identificar con precisión los issues y aplicar soluciones mínimas y precisas a estos issues.
- Para solicitar cambios, un usuario DEBE registrar un issue en el Tracker de issues de plataforma del proyecto.
- El usuario o el colaborador DEBE escribir el issue describiendo el issue que enfrentan u observan.
- El usuario o colaborador DEBE buscar un consenso sobre la exactitud de su observación, y el valor de resolver el issue.
- Los usuarios NO deben registrar solicitudes de información, ideas, sugerencias o soluciones a issues que no estén explícitamente documentados y probables.
- Así, el historial de lanzamiento del proyecto SERÁ una lista de asuntos significativos registrados y resueltos.
- Para trabajar en un issue, un colaborador DEBE hacer un fork del repositorio del proyecto y luego trabajar en su repositorio forkeado.
- Para enviar un parche, un colaborador DEBERÁ crear un pull request al proyecto.
- Un colaborador NO DEBE hacer commits directamente al proyecto.
- Si la Plataforma implementa pull request directo a issues, un Contribuyente PUEDE enviar directamente un pull request sin registrar un issue separado.
- Para discutir un parche, la gente PUEDE comentar en el pull request, en el commit, o en cualquier otro lugar.
- Para aceptar o rechazar un parche, un mantenedor DEBE utilizar la interfaz de la plataforma.
- Los mantenedores NO DEBEN fusionar sus propios parches excepto en casos excepcionales, como la falta de respuesta de otros Mantenedores durante un período prolongado (más de 1-2 días).
- Los mantenedores NO HARÁN juicios de valoración sobre los parches correctos.
- Los mantenedores deben fusionar los parches correctos de otros Colaboradores rápidamente.
- El colaborador PUEDE marcar un issue como "Listo" después de realizar un pull request del issue.
- El usuario que creó un issue DEBE cerrar el issue después de comprobar el parche es un éxito.
- Los mantenedores DEBEN pedir mejoras a los parches incorrectos y DEBEN rechazar los parches incorrectos si el Colaborador no responde de manera constructiva.
- Cualquier Contribuyente que tenga juicios de valoración en un parche correcto DEBERÍA expresarlos a través de sus propios parches.
- Los mantenedores PUEDEN realizar cambios en la documentación que no sea de origen directamente al proyecto.

### Creación de versiones estables

- El proyecto DEBE tener una rama ("master") que siempre tiene la última versión en curso y siempre debe compilar.
- El proyecto NO UTILIZARÁ ramas temáticas por ningún motivo. Los fork personales PUEDEN utilizar ramas temáticas.
- Para hacer una versión estable, alguien debe hacer un FORK del repositorio copiándolo y así convertirse en mantenedor de este repositorio.
- El fork de un proyecto para estabilización PUEDE hacerse unilateralmente y sin el acuerdo de los mantenedores del proyecto.
- Un proyecto de estabilización DEBE ser mantenido por el mismo proceso que el proyecto principal.
- Un parche de un proyecto de estabilización declarado "estable" deberá ir acompañado de un caso de prueba reproducible.

### Evolución de los contratos públicos

- Todos los contratos públicos (APIs o protocolos) DEBEN ser documentados.
- Todos los contratos públicos DEBEN tener espacio para la extensibilidad y la experimentación.
- Un parche que modifica un contrato público estable NO DEBE romper las aplicaciones existentes a menos que haya un consenso sobre el valor de hacer esto.
- Un parche que introduce las nuevas características a un contrato público DEBE hacerlo utilizando nuevos nombres.
- Los nombres antiguos DEBEN ser obsoletos de una manera sistemática marcando nuevos nombres como "experimentales" hasta que sean estables, después marcando los viejos nombres como "inutilizados".
- Cuando haya pasado el tiempo suficiente, los viejos nombres obsoletos DEBERÍAN ser marcados como "heredados" y eventualmente eliminados.
- Los nombres antiguos NO SERÁN reutilizados por las nuevas funciones.
- Cuando se quitan los nombres antiguos, sus implementaciones DEBEN provocar una excepción (aserción) si son utilizadas por las aplicaciones.

### Administración del proyecto

- Los fundadores del proyecto DEBERÁ actuar como Administradores para administrar el conjunto de los Mantenedores del Proyecto.
- Los Administradores DEBEN asegurar su propia sucesión a cierto tiempo promoviendo a los Mantenedores más efectivos.
- Un nuevo colaborador que hace un parche correcto se invitará a convertirse en un mantenedor.
- Los Administradores PUEDEN quitar a los Mantenedores que permanezcan inactivos por un periodo de tiempo prolongado, o que repetidamente no apliquen este proceso con exactitud.
- Los administradores DEBEN bloquear o prohibir a los "malos actores" que causan estrés y dolor a los demás en el proyecto. Esto debe hacerse después de una discusión pública, con la posibilidad de que todas las partes hablen. Un mal actor es alguien que ignora repetidamente las reglas y la cultura del proyecto, que es innecesariamente argumentativo u hostil, o que es ofensivo, y que es incapaz de auto-corregir su comportamiento cuando se le pide que lo haga por otros.

# Proceso de gobernanza

![Proceso de gobernanza](https://getmonero.org/blog/assets/2015-year-in-review/governance-process.jpg)
