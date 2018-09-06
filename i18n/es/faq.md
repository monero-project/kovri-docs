# Preguntas frecuentes (y sus respuestas)

## ¿Que es Kovri?
Kovri es una implementación del router [I2P](https://geti2p.net) en C++, segura, privada, no rastreable y anónima. Lo que una vez fue un fork de i2pd, Kovri se ha convertido en una implementación única y activamente desarrollada implementación en C++ de I2P implementación llevada por la comunidad con muchas mejoras de seguridad, y nuevas características por sobre su predecesor.

Lee más de Kovri en la [Moneropedia](https://getmonero.org/resources/moneropedia/kovri.html).

## ¿Cuál es el estado actual de Kovri?
Kovri está en desarrollo activo y actualmente en fase Alpha. Kovri aun *no* está integrada con Monero pero, en adición a algunas funciones principales estamos desarrollando un [cliente](https://github.com/monero-project/kovri/issues/351) y [una API](https://github.com/monero-project/kovri/issues/350) principal para Monero y otras App.

Actualmente, puedes conectarte y (formar parte de) la red I2P: navegar eepsites, conectarte a IRC y correr túneles cliente y servidor.

## ¿Cuándo será su primer lanzamiento?
Una versión alpha será lanzada al principio del 2017. Una vez que se tengan todos los seguros de calidad y se haya resuelto e implementado una API funcional, iremos a la versión beta.

## ¿Porque mi log muestra una fecha/hora diferente a mi zona?
Los logs son guardados en UTC para proteger tu privacidad, usando UTC estas en una mejor posición de subir logs y compartirlos con los desarrolladores o la comunidad sin comprometer su anonimato.

## ¿En que se está enfocando el equipo de desarrollo?
Actualmente, nos estamos enfocando en todo lo que se encuentra en nuestro [issues tracker](https://github.com/monero-project/kovri/issues/). Ellos cubren un montón de cosas que necesitamos finalizar antes de lanzar una versión oficial (alpha, beta, o mayor).

## ¿Es Kovri usable, parcialmente usable, o recomendado no usarlo actualmente?
Kovri es usable al punto de lo que ```./kovri --help``` tiene para ofrecer. Kovri aún no tiene interacción con Monero. Con respecto a la privacidad hemos arreglado muchos agujeros de seguridad desde los inicios, pero aún estamos en Alpha.

Aún hay mucho código que cubrir así que no esperamos un anonimato fuerte asegurado como en Tor, o incluso java I2P. Esos proyectos tienen más de 10 años de experiencia en investigación e implementación - nosotros apenas estamos comenzando.

Siéntete libre de jugar el rol de desarrollador y experimentar/jugar con Kovri, pero solo si **no** ser totalmente anónimo no te coloca en peligro - porque siempre hay riesgo de una posible des- anonimización dado a que aún se está en Alpha, esto no es único de Kovri.

## ¿Información de contacto de Kovri?
Lee nuestro [README](https://github.com/monero-project/kovri/blob/master/README.md).

## ¿Porque debería usar Kovri en vez de I2P?

- Seguridad: nuestro enfoque es en la seguridad de nuestro software; no [apurarnos a tener todo listo](https://github.com/monero-project/kovri/issues/65) por el hecho de tener las cosas listas
- Calidad: estas apoyando esfuerzos para ayudar a tener un código base de calidad que perdurara en el tiempo. Esto incluye todos los aspectos del mantenimiento del código
- Monero: estarás apoyando una cripto-moneda que su orgullo principal es la preservación de la privacidad y anonimato mientras incrementa ambos tu privacidad y anonimato

## ¿Cuáles son las principales diferencias entre Kovri y i2pd?

- Proveemos un [Forum Funding System](https://forum.getmonero.org/8/funding-required) (sistema de recaudación de fondos) para desarrollo/características.
- Nos enfocamos en crear una ["seguridad por defecto"](http://www.openbsd.org/security.html), fácilmente mantenible, un router I2P mas-probable-de-ser-revisado. Esto viene con el costo de bajar las características menos usadas por usuarios en otros routers, pero con la funcionalidad principal de que una API estará completamente intacta. Creando un router esqueleto, más pequeño y eficiente, hemos provisto a investigadores y desarrolladores más tiempo para auditorias de seguridad y más tiempo para analizar el diseño y especificaciones de I2P.
- Nos enfocamos en implementar una API intuitiva y amigable para que cualquier aplicación se conecte y use la red I2P; incluyendo Monero
- Hemos otorgado a ambos, usuarios finales y desarrolladores un [seguro de calidad](https://github.com/monero-project/kovri/issues/58) y [modelos de desarrollo](https://github.com/monero-project/kovri-docs/blob/master/i18n/es/contributing.md) para proveer un mejor software para todos.
- Hemos implementado una opción de re-plantar como alternativa para que los usuarios puedan usar [Transportes Pluggables](https://www.torproject.org/docs/pluggable-transports.html.en) en vez de HTTPS para re-plantar.
- Hemos implementado una extensa funcionalidad *(modo escondido + inbound deshabilitado)* para proveer anonimato a los que viven en países con condiciones extremas o con firewall de NAT o DS-Lite.
- Siempre creamos un entorno amigable para la colaboración.
- Siempre escuchamos la retroalimentación de las personas y hacemos nuestro mayor esfuerzo para mejorar Kovri!

## ¿Porque un fork de i2pd?

Copiamos por algunas razones:
- Queríamos una implementación robusta, segura y viable en C++ de la red I2P; y i2pd no lo ofrecía
- Queríamos una comunidad positiva que alentara la colaboración para mejorar el software; no negativa, o de gloria narcisista
- Queríamos un desarrollador líder que pudiera liderar; no alguien que ignora las peticiones de liberación de información responsable o se fuera con la cola entre las piernas cuando había problemas entre colaboradores

## ¿Cuáles son los puntos que llevaron copiarse de i2pd (y porque hay dos repos de i2pd, uno en Bitbucket y otro en GitHub)?

*comienza el drama de i2pd*.

Comenzando/Mediados en el 2015 uno de los desarrolladores con privilegios de Push en GitHub, subió un commit que el primer autor no le gusto. En vez de trabajar juntos para resolver el problema, dicho autor se llevó i2pd a Bitbucket, y borro **TODA** historial de git, y se hizo único contribuidor del software. El entonces juro que nunca regresaría a Irc2P.

Esas acciones ofendieron a muchos en la comunidad I2P, incluyendo desarrolladores, y casi termino el proyecto C++.

A finales del 2015, llega anonimal, quien, no queriendo ver que el trabajo de todos se perdiera, revivió el proyecto bajo contribuciones de su autoría, y reiniciando el desarrollo. Una invitación abierta a todos los demás desarrolladores activos a una reunión sobre el futuro de i2pd. El primer autor de i2pd nunca se apareció, pero la reunión resulto en tal punto, que él se [retractó](https://github.com/PurpleI2P/i2pd/issues/279), y comenzó a trabajar en GitHub de nuevo - pero esta vez con un branch ```openssl``` en que resultó ser el repositorio de Bitbucket en vez de la rama ```master``` de la comunidad.

Ver que este comportamiento errático, solamente hería la red I2P y el proyecto como un todo, los demás desarrolladores continuaron en [varias reuniones importantes](https://github.com/monero-project/kovri/issues/47) y asentaron los fundamentos de lo que ahora es Kovri.

## ¡Encontré una vulnerabilidad! ¿Qué hago?
- Vulnerabilidades: leer nuestro [README](https://github.com/monero-project/kovri/blob/master/README.md)
- Bugs: leer nuestra [Guía de desarrolladores](https://github.com/monero-project/kovri-docs/blob/master/i18n/es/developer_guide.md)
