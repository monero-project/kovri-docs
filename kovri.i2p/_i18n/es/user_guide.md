# Ya instalaste Kovri, ¿ahora qué?

## Paso 1. Abre tu NAT/Firewall
1. Elige un puerto entre ```9111``` y ```30777```
2. **Guarda este puerto en tu archivo de configuración** (`kovri.conf`)
3. Haz un agujero en tu NAT/Firewall para permitir conexiones entrantes TCP/UDP a ese puerto (Ve las notas de abajo si no tienes acceso)

Notas:

- **No compartas con nadie tu puerto, porque puede comprometer tu anonimato!!**
- Si no guardas el puerto, Kovri va a generar uno de forma aleatorio cada vez que se inicie (también puedes elegir pasar el puerto con el parámetro `--port` en cada inicio).
- Si no tienes acceso a tu NAT, mira las instrucciones en [Compilando](https://github.com/monero-project/kovri/blob/master/doc/BUILDING.md) para tu OS. 

## Paso 2. Configurar Kovri

Para una lista completa de opciones:

```bash
$ ./kovri --help
```

Para una lista completa detallada:

- `kovri.conf` archivo de configuración del router y cliente
- `tunnels.conf` archivo de configuración para cliente/servidor de túneles

## Paso 3. Iniciar Kovri
```bash
$ cd build/ && ./kovri
```

- Espera 5 minutos o algo más para que quedes inicializado en la red antes de intentar usar los servicios.

## Paso 4. Únete a nuestro IRC
1. Inicia tu [cliente IRC](https://en.wikipedia.org/wiki/List_of_IRC_clients)
2. Configura tu cliente para conectarse al puerto IRC de Kovri (default 6669). Esto te conectara a la red Irc2p (I2P's IRC network)
3. Únete a  `#kovri` y `#kovri-dev`

## Paso 5. Navega una web I2P (garlic-site/eepsite)
1. Inicia el navegador de tu preferencia (preferiblemente uno dedicado al uso de Kovri)
2. Configura tu navegador leyendo [estas instrucciones](https://geti2p.net/en/about/browser-config) **pero en vez del puerto 4444 y 4445** cambia el proxy HTTP al puerto **4446** y puerto SSL *también* a **4446**
3. Visita el [sitio de chequeo](http://check.kovri.i2p) para verificar si funciona

Notas:

- **Así como en TOR, no necesitas SSL para navegar de forma segura la red**
- Soporte de SSL en sitios y proxies de salida aun no está implementado
- Si alguien te da una dirección .i2p que no está en tu cartera de direcciones, usa el servicio de `Jump` en este [sitio](http://stats.i2p/i2p/lookup.html)
- Mira a través de hosts.txt en tu directorio de datos para ver una lista de sitios por defecto que puedes visitar fácilmente
- En general, la implementación del proxy HTTP y cartera de direcciones aun están desarrollo y aun no están completos

## Paso 6. Hostea tu propio servicio-garlic (garlic-site/eepsite)
- Lee `tunnels.conf` para aprender como colocar un servicio túnel que apunte a un servicio que estés hosteando

## Paso 7. ¡Disfruta!
- Lee más de Kovri en la [Moneropedia](https://getmonero.org/resources/moneropedia/kovri.html).
- Abre una petición de nueva característica, o reporta bugs en nuestro [issues tracker](https://github.com/monero-project/kovri/issues)
- Aprende más de la red I2P en el [sitio de java I2P](https://geti2p.net/en/docs)

# Alternativamente, Docker

## Paso 1. Instalar Docker
Instalar Docker está fuera del propósito de este documento, por favor lee la [documentación de docker](https://docs.docker.com/engine/installation/)

## Paso 2. Configurar / Abrir Firewall

La imagen de docker ya viene con la configuración por default de Kovri, pero puedes configurarlo como se explica en secciones anteriores

Deberías escoger un puerto aleatorio y abrir ese puerto

## Paso 3. Iniciar

### Configuración por defecto
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT geti2p/kovri
```

### Configuración personalizada
Donde `./kovri-settings/` contiene `kovri.conf` y `tunnels.conf`.
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT -v kovri-settings:/home/kovri/.kovri/config:ro geti2p/kovri
```
