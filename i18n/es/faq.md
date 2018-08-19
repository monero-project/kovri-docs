# Preguntas frecuentes

## Tabla de contenido
- Preguntas generales
   - ¿Qué es Kovri?
   - ¿Quién está desarrollando Kovri?
   - ¿Cómo ayudará Kovri a Monero?
   - ¿Por qué debería obtener Kovri en lugar de I2P?
   - ¿Qué hace / no hace Kovri por ti?
   - ¿Cuál es el estado actual de Kovri?
   - Cuando es el alfa?
   - ¿En qué se está centrando actualmente el equipo de desarrollo?
   - ¿Cuál es la usabilidad actual de Kovri y la privacidad que ofrece?
   - ¿Cómo puedo contactar a los desarrolladores de Kovri?
- Kovri vs i2pd
   - ¿Por qué debería usar Kovri en lugar de i2pd?
   - ¿Cuáles son las principales diferencias entre Kovri e i2pd?
   - ¿Por qué te burlaste de i2pd?
   - ¿Cuáles fueron los puntos de inflexión que llevaron a la bifurcación de i2pd (y por qué hay dos repositorios de i2pd: uno en Bitbucket y otro en GitHub)?
- Usando Kovri
   - ¡Encontré una vulnerabilidad! Encontré un error! ¿Qué debo hacer?
   - ¿Por qué mi registro muestra una fecha / hora diferente de mi zona horaria?
# Preguntas frecuentes (y sus respuestas)

## Preguntas Generales

### ¿Que es Kovri?

[Kovri](https://getmonero.org/resources/moneropedia/kovri.html) es una tecnología gratuita, descentralizada y anónima desarrollada por [Monero](https://getmonero.org).

Actualmente basado en las especificaciones abiertas de [I2P](https://getmonero.org/resources/moneropedia/i2p.html), Kovri usa ambos [encriptación de ajo (Garlic)](https://getmonero.org/resources/moneropedia/garlic-encryption.html) y [routing de ajo (Garlic)](https://getmonero.org/resources/moneropedia/garlic-routing.html) para crear una red privada superpuesta protegida a través de Internet. Esta superposición de red proporciona a los usuarios la capacidad de *ocultar* de manera efectiva su ubicación geográfica y su dirección IP de Internet.

Esencialmente, Kovri *cubre* el tráfico de Internet de una aplicación para que sea anónimo dentro de la red.

Un enrutador ligero y centrado en la seguridad, Kovri es totalmente compatible con la red I2P. Una versión alfa de Kovri está en proceso.

### ¿Quién está desarrollando Kovri?
Kovri es un proyecto de código abierto, lo que significa que depende de la comunidad para las contribuciones. El desarrollador principal del proyecto es [anonimal](https://github.com/anonimal), a quien puede contactar con preguntas en los canales IRC de Kovri [#kovri](irc://chat.freenode.net/#kovri ), [# kovri-dev](irc://chat.freenode.net/#kovri-dev), y su [cuenta de Twitter](https://twitter.com/whoisanonimal).

Kovri se está desarrollando bajo el cobijo de [The Monero Project](https://github.com/monero-project), que es otro proyecto de código abierto que desarrolla la [Moneda Monero](https://getmonero.org) y [Open Alias](https://openalias.org). La relación entre The Monero Project y Kovri es mutuamente beneficiosa, con Kovri buscando integrarse en la red de Monero, y Monero brindando un flujo de desarrolladores y recursos para el desarrollo de Kovri.

### ¿Cómo ayudará Kovri a Monero?
Monero es una criptomoneda segura, privada, imposible de rastrear y fungible que tiene privacidad de forma predeterminada y utiliza tecnologías tales como stealth addresses, RingCT y firmas de anillo para ocultar el receptor, los importes y el remitente, respectivamente. Algunas debilidades potenciales en Monero están filtrando la dirección IP que transmite una transacción y los ataques de correlación.

Entra en Kovri. Kovri se implementará en la billetera Monero oficial, por lo que todas las transacciones se enrutarán a través de la red anónima Kovri, ocultando la dirección IP desde la cual se originó la transacción. En el futuro, todas las transacciones se enrutarán a través de Kovri de forma predeterminada, aunque descargar el blockchain seguirá siendo a través de la red transparente para mayor eficiencia.

### ¿Por qué debería usar Kovri en lugar de I2P?
[I2P](https://geti2p.net) es un gran proyecto, pero había algunas cosas que sentimos que era necesario ajustar para integrar la tecnología en Monero. Primero, I2P está desarrollado en Java, y pensamos que desarrollar un enrutador en C++ ayudaría a que el código sea rápido y liviano.

En segundo lugar, aunque la implementación de I2P en Java es excelente, viene con muchas características adicionales que no creemos que sean necesarias para que la use Monero. Entonces, decidimos comenzar desde cero y crear un enrutador que sea JUSTO el enrutador. Este enfoque básico es perfecto para Monero, y también es una buena noticia para otros que quieren hacer aplicaciones I2P. Tienen la opción de usar un enrutador ligero sin todo el exceso, mientras que otros usuarios que tienen un uso para esas características adicionales podrán usar la implementación de Java. Es una situacion de ganar-ganar para todos.

### ¿Qué hace Kovri ahora?
- Te permite convertirte en un nodo en la red I2P
- Oculta su ubicación física de los sitios que visita
- Anonimiza en IRC y permite el correo electrónico anónimo
- Te permite alojar sitios web o servicios anónimos
- Proporciona fondos a desarrolladores, hackers e investigadores a través de FFS y HackerOne.
- Busca estándares rigurosos de calidad de código y desarrollo

### ¿Qué novedades tendra Kovri en el futuro?
- Confirmar las transacciones de Monero sobre I2P
- GUI para una mejor configuración y usabilidad
- API de biblioteca y enlaces para aplicaciones / librerías externas
- Extensión de Firefox para acceder fácilmente a eepsites
- Desarrollo de sitios web (getkovri.org / kovri.i2p)
- Amplia documentación de ELI5 para desarrolladores

### ¿Qué no hará Kovri por ti?
- Sacrificar tu seguridad por motivos ocultos
- Proporcionar una interfaz de usuario web complicada y dolorosa
- Requerir autoridades para consenso de red
- Acceso a sitios web de Internet a través de un "outproxy"
- Requiere una VM Java asesina de rendimiento
- Caminar a tu perro o mascota favorita, pagar tus impuestos

### ¿Cuál es el estado actual de Kovri?
Kovri está en desarrollo activo y actualmente se encuentra en una fase Alfa. *No* aún está integrado con Monero, pero, además de varias funciones principales, estamos desarrollando un [cliente](https://github.com/monero-project/kovri/issues/351) y [core](https://github.com/monero-project/kovri/issues/350) API para monero y otras aplicaciones para usar.

Pero solo porque estamos en Alpha no significa que no puedas usar Kovri. Actualmente, puede usar Kovri para conectarse (y participar) en la red I2P, explorar eepsites, conectarse a IRC y ejecutar túneles de clientes y servidores.

### ¿Cuándo es el alfa?
Está en preparación una versión alfa para lanzarse (¡esperamos!) Antes de finales de 2017. Una vez que estamos en alfa, inmediatamente comienza el trabajo sobre la versión beta, que requerirá: una API completamente implementada, resolución a calidad esencial problemas de seguridad y varias correcciones de errores.

### ¿En qué se está centrando actualmente el equipo de desarrollo?
Actualmente, nos estamos centrando en todo lo que se detalla en nuestro [issue tracker](https://github.com/monero-project/kovri/issues/). Cubren la mayor parte de lo que necesitamos para terminar antes del lanzamiento alfa oficial.

### ¿Cuál es la usabilidad actual de Kovri y el nivel de privacidad que ofrece?
Kovri es utilizable en la medida de lo que `./kovri --help` tiene para ofrecer. Kovri actualmente no tiene interacción con Monero. Con respecto a la privacidad, hemos solucionado muchos problemas de seguridad desde el inicio, pero le pedimos que tenga en cuenta que todavía estamos en Alpha.

Todavía hay mucho código por cubrir, así que no esperes una garantía sólida de anonimato como con Tor, o incluso Java I2P. Esos proyectos tienen más de 10 años de experiencia en investigación e implementación, y recién estamos comenzando.

Siéntete libre de jugar el rol de desarrollador y experimentar con Kovri, pero solo si **no** el no ser anónimo no te pone en peligro, ya que siempre existe el riesgo de una posible de-anonimización debido a estar en Alpha (esto es no exclusivo de Kovri).

### ¿Cómo puedo contactar a los desarrolladores de Kovri?
Vea nuestro [README](https://github.com/monero-project/kovri/blob/master/README.md).

## Kovri vs i2pd

### ¿Por qué debería usar Kovri en lugar de i2pd?

- Seguridad: nuestro enfoque es asegurar nuestro software; no [apurarnos en hacer las cosas](https://github.com/monero-project/kovri/issues/65) por el bien de tener un lanzamiento
- Calidad: estás apoyando los esfuerzos para garantizar una base de código de calidad que resista la prueba del tiempo. Esto incluye todos los aspectos de la mantenibilidad del código
- Monero: apoyará una moneda criptográfica que se enorgullece de la preservación de la privacidad y el anonimato, al tiempo que aumenta su privacidad y su anonimato.

### ¿Cuáles son las principales diferencias entre Kovri e i2pd?

- Brindamos un [Foro con un Sistema de Financiamiento (FFS)](https://forum.getmonero.org/8/funding-required) para funciones / desarrollo.
- Nos centramos en crear un enrutador I2P ["seguro por defecto"](http://www.openbsd.org/security.html), de fácil mantenimiento y con más posibilidades de ser revisado. Esto vendrá con el costo de eliminar las características de menor uso que se encuentran en los otros enrutadores, pero la funcionalidad central y una API estarán completamente intactas. Al crear un enrutador más pequeño, eficiente y "básico", brindaremos a los desarrolladores e investigadores más tiempo para la auditoría de seguridad y más tiempo para cuestionar el diseño y las especificaciones de I2P.
- Nos enfocamos en implementar una API intuitiva y amigable para el desarrollador para que cualquier aplicación se conecte y use la red I2P; esto incluye a Monero.
- Brindamos a los usuarios finales y a los desarrolladores una [garantía de calidad](https://github.com/monero-project/kovri/issues/58) y [modelo de desarrollo](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/contributing.md) para proporcionar un mejor software para todos.
- Implementaremos opciones alternativas de reseed para que los usuarios puedan usar [Transportes conectables](https://www.torproject.org/docs/pluggable-transports.html.en) en lugar de HTTPS para hacer reseed.
- Implementaremos una funcionalidad extendida *(hidden mode + disabled inbound)* para brindar anonimato a aquellos que viven en países con condiciones extremas o aquellos que cuentan con cortafuegos NAT o DS-Lite de grado operador.
- Siempre crearemos un ambiente de bienvenida para la colaboración.
- Siempre escucharemos tus comentarios y haremos nuestro mejor esfuerzo para mejorar Kovri.

### ¿Por qué te sales de i2pd?

Hicimos un fork por al menos varias razones:

- Queríamos una implementación C++ robusta, segura y viable de la red I2P; y i2pd no estaba listo para ello
- Queríamos una comunidad positiva que fomentara la colaboración para la mejora del software; no negativo, gloria narcisista
- Queríamos un desarrollador principal que pudiera liderar; no alguien que ignorara las solicitudes de revelación responsable o hacer un "esconder la colaand y correr" cuando se enfrenta con el conflicto del colaborador

### ¿Cuáles fueron los puntos de inflexión que llevaron al fork de i2pd (y por qué hay dos repositorios de i2pd: uno en Bitbucket y otro en GitHub)?

*Así comenzó el drama de i2pd*.

A principios / mediados de 2015, uno de los desarrolladores con privilegios de edicion en GitHub hizo uno(s) commit(s) que al primer autor de i2pd no le gustó. En lugar de trabajar juntos para resolver el problema, dicho autor se llevo i2pd a Bitbucket, y borró **todo** el historial de git existente y se convirtió en el único 'colaborador' del software. Luego juró nunca volver a Irc2P.

Estas acciones ofendieron a muchos en la comunidad I2P, incluidos los desarrolladores, y casi terminaron el proyecto C ++.

En el otoño de 2015, llegó un momento en el que, no queriendo que el trabajo de todos se desperdiciara, revivió el proyecto a través de contribuciones propias y por el desarrollo reinante. Luego se dio una invitación abierta para que todos los desarrolladores activos restantes se reunieran y discutieran el futuro de i2pd. El primer autor de i2pd nunca apareció, pero el acto de reunirse aparentemente hizo crujir las plumas de i2pd hasta el punto en que [tomó represalias](https://github.com/PurpleI2P/i2pd/issues/279) y comenzó a trabajar en GitHub nuevamente, pero esta vez dentro de una rama ```openssl``` (que resultó ser el repositorio Bitbucket) en lugar de la rama``` master``` impulsada por la comunidad.

Al ver que este tipo de comportamiento errático solo dañaría la red I2P y el proyecto en su conjunto, los desarrolladores restantes continuaron teniendo [varias reuniones importantes](https://github.com/monero-project/kovri/issues/47) y establecerieron las bases para lo que ahora es Kovri.

## Usando Kovri

### ¡Encontré una vulnerabilidad! Encontré un error! ¿Qué debo hacer?
- Vulnerabilidades: vea nuestro [README](https://github.com/monero-project/kovri/blob/master/README.md)
- Errores: vea nuestra [Guía del Desarrollador](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/developer_guide.md)

### ¿Por qué mi registro muestra una fecha / hora diferente a la de mi zona horaria?
Los registros se registran en UTC para proteger su privacidad. Al usar UTC, se encuentra en una mejor posición para cargar las contraseñas de registro para compartirlas con los desarrolladores o la comunidad sin afectar su anonimato.