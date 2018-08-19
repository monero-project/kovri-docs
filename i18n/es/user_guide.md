# Ya instalaste Kovri, ¿ahora qué?

## Paso 1. Abre tu NAT/Firewall
1. Elige un puerto entre ```9111``` y ```30777```
2. **Guarda este puerto en tu archivo de configuración** (`kovri.conf`)
3. Haz un agujero en tu NAT/Firewall para permitir conexiones entrantes TCP/UDP a ese puerto (Ve las notas de abajo si no tienes acceso)

Notas:

- Si no guardas el puerto, Kovri va a generar uno de forma aleatorio cada vez que se inicie (también puedes elegir pasar el puerto con el parámetro `--port` en cada inicio).
- Si no tienes acceso a tu NAT, mira las instrucciones en [Compilando](https://github.com/monero-project/kovri-docs/blob/master/i18n/es/building.md) para tu OS.
- **No compartas con nadie tu puerto, porque puede comprometer tu anonimato!!**


## Paso 2. (Recomendado) Seguridad Operacional

- Considere crear un usuario designado `kovri` y ejecute kovri solo usando ese usuario
- Si usa Linux, considere usar un kernel reforzado (como [grsec](https://en.wikibooks.org/wiki/Grsecurity) con RBAC)
- Después de instalar los recursos apropiados en su ruta de datos kovri, considerando que establecio el control de acceso apropiado con [setfacl](https://linux.die.net/man/1/setfacl), [umask](https://en.wikipedia.org/wiki/Umask), o lo que sea que su sistema operativo use para ACL
- Nunca compartas tu número de puerto con nadie, ya que afectará tu anonimato.

**Nota: vea kovri.conf para encontrar su ruta de datos para Linux/OSX/Windows**

## Paso 3. Configurar Kovri, configurar tuneles

Para una lista completa de opciones:

```bash
# Linux / macOS / *BSD
$ cd ~/bin && ./kovri --help
```

```bash
# Windows (PowerShell / MSYS2)
$ cd "C:\Program Files\Kovri" ; ./kovri.exe --help
```

Para una lista completa detallada:

- `kovri.conf` archivo de configuración del router y cliente
- `tunnels.conf` archivo de configuración para cliente/servidor de túneles

## Paso 4. (Opcional) Configurar tuneles

En resumen, *túneles de cliente* son túneles que usted usa para conectarse a otros servicios y *túneles de servidor* se utilizan para cuando usted aloja servicios (y otras personas se conectan a su servicio).

De forma predeterminada, tendrá túneles de cliente configurados para IRC (Irc2P) y correo electrónico (i2pmail). Para agregar/eliminar túneles de clientes, consulte `tunnels.conf`.

Al crear túneles de servidor, deberá crear *claves privadas persistentes*. Para hacerlo, descomente o cree `keys = your-keys.dat` y reemplace`your-keys` con un nombre apropiado. **No comparta su archivo `.dat` privado con nadie, ¡y asegúrese de hacer una copia de seguridad!**

Una vez configurada, su [dirección Base32](https://getmonero.org/resources/moneropedia/base32-address) se mostrará en su registro después de iniciar kovri. También puede encontrar la dirección en un archivo de texto junto con el archivo de claves privadas en su ruta de datos kovri en el directorio `client/keys`. La dirección dentro de este archivo de texto `.txt` es segura de distribuir para que otras personas puedan conectarse a su servicio.

Ejemplo:

- Archivo de claves privadas: `client/keys/your-keys.dat`
- Dirección pública [Base32](https://getmonero.org/resources/moneropedia/base32direction)/[Base64](https://getmonero.org/resources/moneropedia/base64-address): `client/keys/your-keys.dat.txt`

**Nota: vea kovri.conf para encontrar su ruta de datos para Linux / OSX / Windows**

## Paso 5. (Opcional) Registre su nuevo [eepsite](https://getmonero.org/resources/moneropedia/eepsite)

**ALTO! Hasta que [#498](https://github.com/monero-project/kovri/issues/498) se resuelva, solo considere registrar su servicio con Kovri y *not* stats.i2p!**

- Abra una solicitud con `[Solicitud de suscripción] your-host.i2p` (reemplace su-host.i2p con su nombre de host deseado) en el [issue tracker de Kovri](https://github.com/monero-project/kovri/issues)
- En el cuerpo de la solicitud, pegue los contenidos de su archivo público `.txt` que se mencionó en el paso anterior
- Después de la revisión, agregaremos su host y firmaremos la suscripción
- ¡Hecho!

## Paso 6. Ejecutar Kovri
```bash
$ cd build/ && ./kovri
```
- Espere 5 minutos o más esperar el bootstrap en la red antes de intentar usar los servicios

## Paso 7. Únete a nosotros en IRC
1. Inicie su [Cliente de IRC](https://en.wikipedia.org/wiki/List_of_IRC_clients)
2. Configure su cliente para conectarse al puerto IRC de kovri (predeterminado 6669). Esto lo conectará a la red Irc2P (red IRC de I2P)
3. Únete a `# kovri` y` # kovri-dev`

## Paso 8. Navega por un sitio web I2P (garlic-site / eepsite)
1. Inicie un navegador de su elección (preferiblemente un navegador dedicado al uso de kovri)
2. Configure su navegador leyendo [estas instrucciones](https://geti2p.net/en/about/browser-config) **pero en lugar del puerto 4444 y 4445** cambie el puerto proxy HTTP a **4446** y Puerto proxy SSL *también* a **4446**
3. Visite http: //check.kovri.i2p

Notas:

- **Al igual que con Tor, no se necesita SSL para usar la red de manera segura.**
- El soporte de sitio SSL y el servicio externo no se implementan actualmente
- Si alguien te da una dirección .i2p que no está en tu libreta de direcciones, utiliza el servicio `Jump` en http: //stats.i2p/i2p/lookup.html
- Busque en hosts.txt en su directorio de datos para ver una lista de sitios predeterminados que puede visitar fácilmente
- En general, la implementación del proxy HTTP y la libreta de direcciones están en desarrollo y aún no cuentan con funciones completas.

## Paso 9. ¡Disfruta!
- Lea más sobre Kovri en la [Moneropedia](https://getmonero.org/resources/moneropedia/kovri).
- Abra sus solicitudes de funciones o informe de errores en nuestro [issue tracker](https://github.com/monero-project/kovri/issues)
- Obtenga más información sobre la red I2P en el [sitio web java I2P](https://geti2p.net/en/docs)

# Opciones de contenedor

## Snapcraft

En sistemas Linux, use snapcraft para una fácil implementación.

### Paso 1. Obtenga el repositorio del codigo de Kovri

```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

### Paso 2. Instalar snapcraft

- Consulte el administrador de paquetes de su distribución para snapcraft y [snapd](https://snapcraft.io/docs/core/install)

En Ubuntu, simplemente ejecute:
```bash
$ sudo apt-get install snapcraft
```

### Paso 3. Crea el snap

```bash
$ cd kovri / && snapcraft && sudo snap install * .snap --dangerous
```
Nota: la bandera --dangerous es necesaria solo porque el snap no ha sido firmado (sin embargo, tú mismo lo construiste, así que esto no debería ser un problema)

### Paso 4. Ejecuta Kovri con snapcraft

```bash
$ snap run kovri
```

## Docker

### Paso 1. Instalar Docker
La instalación de Docker está fuera del alcance de este documento, consulte la [documentación de docker](https://docs.docker.com/engine/installation/)

### Paso 2. Configurar / Abrir el Firewall (contrafuegos)

La imagen de docker viene con los valores predeterminados de kovri, pero se puede configurar como se explicó en secciones anteriores.

Debe elegir un puerto aleatorio y abrir ese puerto (ver secciones anteriores).

### Paso 3. Ejecutar

#### Configuración por defecto
```bash
KOVRI_PORT = 42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $ KOVRI_PORT --env KOVRI_PORT = $ KOVRI_PORT geti2p / kovri
```

#### Ajustes personalizados
Donde `. / Kovri-settings /` contiene `kovri.conf` y` tunnels.conf`.
```bash
KOVRI_PORT = 42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $ KOVRI_PORT --env KOVRI_PORT = $ KOVRI_PORT -v kovri-settings: /home/kovri/.kovri/ config: ro geti2p / kovri
```