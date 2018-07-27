# Comenzar con la testnet de Kovri

## Preámbulo

La testnet de Kovri actualmente reside dentro de una serie de contenedores Docker e imágenes que se comunican a través de una sola red Docker.
Esto permite realizar pruebas y monitoreos en redes privadas sin la necesidad de conectarse a la red pública de kovri.

## Prerrequisitos

- Entorno de desarrollo Linux (actualmente, Linux es compatible)
   - Consulte el [README](https://github.com/monero-project/kovri#building) de kovri para obtener una lista de las dependencias de compilación.
- [Docker](https://www.docker.com/)
   - El usuario de compilación debe tener permisos para usar Docker (agregado al grupo de Docker, por ejemplo)
- Clonar el repositorio
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

## Paso 1: Crea el testnet

Para obtener una lista completa de opciones, ejecute la opción `help`:
```bash
$ ./kovri/contrib/testnet/testnet.sh ayuda
```
Puede exportar las variables de entorno enumeradas desde su shell o configurarlas manualmente durante la instalación.

Crea el entorno y establece los valores correctamente:
```bash
$ ./kovri/contrib/testnet/testnet.sh create
```
- Para los nuevos desarrolladores, se aconseja utilizar los valores predeterminados con la excepción de la ubicación de su repositorio
- Consulte el directorio Dockerfiles para ver los archivos Docker disponibles para compilar durante la configuración
- Para mantener el repositorio Kovri limpio, elija un directorio fuera del repositorio

## Paso 2a: inicia el testnet

```bash
$ ./kovri/contrib/testnet/testnet.sh start
```
Para las opciones de monitoreo, ejecute `help` para obtener detalles sobre cómo monitorear.

## Paso 2b: ejecutar comandos personalizados

**TODO (sin asignar): mejore esta sección**

Para ejecutar comandos desde un contenedor, consulte la documentación de Docker.

También puedes probar:
```bash
$ ./contrib/testnet/testnet.sh exec "bash"
```

## Paso 3: detener el testnet

```bash
$ ./kovri/contrib/testnet/testnet.sh stop
```
- Debería aparecer un intervalo de tiempo de espera del contenedor (si env no está configurado)
   - Esto es útil en el caso de enrutadores congelados (que no responden)

## Paso 4: destruir el testnet

```bash
$ ./kovri/contrib/testnet/testnet.sh destroy
```
- Debería pedírsele que configure el directorio testnet para que se destruya (si env no se configuró)