# Objection

## Guía para proxear una app mobile

1. Instalar Objection: ```pip3 install objection```
2. Conectar mediante adb el teléfono: ```adb connect IP:5555```
3. Parchear la apk: ```objection patchapk -s name.apk```
4. Instalar la app patcheada en el teléfono: ```adb install -r name.apk```
5. Iniciar la app en el teléfono
6. Ejecutar en terminal: ```sudo objection explore```
7. En la terminal que inicia objection: ```android sslpinning disable```
