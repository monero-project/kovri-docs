## Seguros de calidad
- Mira nuestros [Seguros de calidad](https://github.com/monero-project/kovri-docs/blob/master/i18n/es/quality.md) para tener una idea de nuestro flujo de trabajo

## Conformidad
- Nosotros apuntamos a usar las conformidades de C++11/14; siéntete libre de usar esto para mejorar tu trabajo
- También es altamente recomendable usar las librerías y dependencias estándar cuando sea posible

## Enviando tú trabajo
Para contribuir tu trabajo, por favor procede con lo siguiente:

1. Forkea Kovri
2. Lee nuestra [guía de estilo](https://github.com/monero-project/kovri-docs/blob/master/i18n/es/style.md)
3. Crea una [branch](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) para trabajar
4. [**Firma**](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work) tu(s) commit(s)
5. envía tu pull-request a la branch ```master```
   - Actualmente no tenemos ningún tag por estar en pre-alpha. Por ahora, puedes basar tu trabajo desde la rama master.
   - Los mensajes del Commit deben ser verbose por default, considerando una línea de asunto de (50 caracteres máximo), una línea en blanco y una explicación detallada como párrafo(s) separado(s) - a menos que el titulo se auto-explique.
   - El título de commit debe preponer class u otro aspecto del proyecto. Por ejemplo, "HTTPProxy: implementado depurador de User-Agent. Arregla #193." o "Garlic: arregla padding no inicializado en ElGamalBlock".
   - Si un commit en particular referencia otro issue, por favor agrega una referencia. Por ejemplo, "Leer #123", o "Arregla #123". Esto ayudara a resolver tickets cuando se mezclen con ```master```.
   - En general, los commits deben ser [atomicos](https://en.wikipedia.org/wiki/Atomic_commit#Atomic_commit_convention) y los diffs deben ser fáciles de leer. Por esta razón, por favor intenta no mezclar arreglos de formato con commits de sin formato.
   - El cuerpo de los pull requests deben contener una descripción adecuada de lo que hace el parche, y proveer una justificación o razonamiento para el parche (cuando sea apropiado). Debes incluir referencias a cualquier discusión como tickets, chats, o IRC.

## Propuestas
Para contribuir una propuesta, por favor lee nuestros [issues abiertos](https://github.com/monero-project/kovri/issues) para ver los ya existentes. Si lo que quieres proponer no está ahí, entonces [abre un nuevo issue](https://github.com/monero-project/kovri/issues/new).

A pesa r de que nuestro C4 dicta, que nosotros mezclamos todo, pedimos abrir una propuesta por las siguientes razones:

1. Una propuesta abre la comunicación
2. Una propuesta muestra que el colaborador respeta la opinión de todos los colaboradores del proyecto
3. Una propuesta permite a los colaboradores opinar en un foro abierto
4. Una propuesta ahorra tiempo si un colaborador ya está trabajando en algo similar
5. Una propuesta previene catástrofes, y errores, o permite a los colaboradores prepararse para catástrofes, o errores

*No* abrir una nueva propuesta *no* va a prevenirte de colaborar; nosotros mezclaremos tu PR - pero una propuesta es altamente recomendada.

## TODO
- Haz una búsqueda rápida en el código base por ```TODO(sin asignar):``` y/o elige un ticket y ¡comienza a trabajar!
- Si creas un TODO, asígnatelo a ti mismo o escribe ```TODO(sin asignar):```

# [Código de conducta (22/C4.1)](http://rfc.zeromq.org/spec:22)

## Licencia

Copyright (c) 2009-2015 Pieter Hintjens.

This Specification is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This Specification is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, see <http://www.gnu.org/licenses>.

## Lenguaje

Las palabras "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", y "OPTIONAL" en este documento, no deben ser interpretadas como esta descrito en el RFC 2119.

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
- El proyecto DEBE utilizar el sistema de control de revisión distribuido git.
- El proyecto ESTARÁ alojado en github.com o equivalente, llamado "Plataforma".
- El proyecto DEBE utilizar la plataforma de Tracker de issues.
- El proyecto DEBE tener directrices claramente documentadas para el estilo de código.
- Un "Colaborador" es una persona que desea proporcionar un parche, siendo un conjunto de compromisos que resuelven algún problema claramente identificado.
- Un "Mantenedor" es una persona que fusiona parches al proyecto. Los mantenedores no son desarrolladores; Su trabajo es hacer cumplir el proceso.
- Los colaboradores NO tendrán acceso de commit al repositorio a menos que sean también Mantenedores.
- Los mantenedores DEBEN tener acceso de commit al repositorio.
- Todos, sin distinción ni discriminación, tendrán el mismo derecho de convertirse en un Colaborador en los términos de este contrato.

### Licencia y propiedad

- El proyecto DEBE utilizar una licencia compartida, como la GPLv3 o una variante de la misma (LGPL, AGPL), o la MPLv2.
- Todas las contribuciones al código fuente del proyecto ("parches") DEBERÁ utilizar la misma licencia que el proyecto.
- Todos los parches son propiedad de sus autores. No habrá ningún proceso de asignación de derechos de autor.
- Los derechos de autor del proyecto serán de propiedad colectiva de todos sus colaboradores.
- Cada Contribuyente DEBERÁ ser responsable de identificarse en la lista de Colaboradores del proyecto.

### Requisitos del parche

- Mantenedores y contribuyentes DEBEN tener una cuenta de la plataforma y DEBERÍAN utilizar sus nombres verdaderos o un alias conocido.
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
- Para hacer una liberación estable, alguien FORK el repositorio copiándolo y así convertirse en mantenedor de este repositorio.
- El fork de un proyecto para estabilización PUEDE hacerse unilateralmente y sin el acuerdo de los mantenedores del proyecto.
- Un proyecto de estabilización DEBE ser mantenido por el mismo proceso que el proyecto principal.
- Un parche de un proyecto de estabilización declarado "estable" deberá ir acompañado de un caso de prueba reproducible.

### Evolución de los contratos públicos

- Todos los contratos públicos (APIs o protocolos) DEBEN ser documentados.
- Todos los contratos públicos DEBEN tener espacio para la extensibilidad y la experimentación.
- Un parche que modifica un contrato público estable NO DEBE romper las aplicaciones existentes a menos que haya un consenso sobre el valor de hacer esto.
- Un parche que introduce las nuevas características de un contrato público DEBE hacerlo utilizando nuevos nombres.
- Los nombres antiguos DEBEN ser obsoletos de una manera sistemática marcando nuevos nombres como "experimentales" hasta que sean estables, después marcando los viejos nombres como "inutilizados".
- Cuando haya pasado el tiempo suficiente, los viejos nombres obsoletos DEBERÍAN ser marcados como "heredados" y eventualmente eliminados.
- Los nombres antiguos NO SERAN reutilizados por las nuevas funciones.
- Cuando se quitan los nombres antiguos, sus implementaciones DEBEN provocar una excepción (aserción) si son utilizadas por las aplicaciones.

### Administración del proyecto

- Los fundadores del proyecto DEBERÁ actuar como Administradores para administrar el conjunto de los Mantenedores del Proyecto.
- Los Administradores DEBEN asegurar su propia sucesión a cierto tiempo promoviendo a los Mantenedores más efectivos.
- Un nuevo colaborador que hace un parche correcto se invitará a convertirse en un mantenedor.
- Los Administradores PUEDEN quitar a los Mantenedores que permanezcan inactivos por un periodo de tiempo prolongado, o que repetidamente no apliquen este proceso con exactitud.
- Los administradores DEBEN bloquear o prohibir a los "malos actores" que causan estrés y dolor a los demás en el proyecto. Esto debe hacerse después de una discusión pública, con la posibilidad de que todas las partes hablen. Un mal actor es alguien que ignora repetidamente las reglas y la cultura del proyecto, que es innecesariamente argumentativo u hostil, o que es ofensivo, y que es incapaz de auto-corregir su comportamiento cuando se le pide que lo haga por otros.

# Proceso de gobernanza

![Proceso de gobernanza](https://getmonero.org/blog/assets/2015-year-in-review/governance-process.jpg)
