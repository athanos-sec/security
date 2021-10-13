# Guía para proxear una app mobile

## Certificado a nivel de sistema

1. Exportar certificado de burp en formato DER o descargarlo y modificarlo: ```mv cacert.crt cacert.der```
2. Convertirlo en PEM: ```openssl x509 -inform DER -in cacert.der -out cacert.pem```
3. Obtener el subject hash: ```openssl x509 -inform PEM -subject_hash_old -in cacert.pem | head -1```
4. Renombrar con el hash obtenido: ```mv cacert.pem <hash>.0```
5. Copiar el certificado al teléfono: ```adb push <cert>.0 /sdcard/```
6. Interfaz adb: ```adb shell```
7. Mover certificado: ```mv /sdcard/<cert>.0 /system/etc/security/cacerts/```
8. Dar permisos: ```chmod 644 /system/etc/security/cacerts/<cert>.0```
9. Reiniciar dispositivo
10. Ingresar a Settings -> Security -> Trusted Credentials deberiamos encontrar “Portswigger CA” como system trusted CA.

## Objection

1. Instalar Objection: ```pip3 install objection```
2. Conectar mediante adb el teléfono: ```adb connect IP:5555```
3. Parchear la apk: ```objection patchapk -s name.apk```
4. Instalar la app patcheada en el teléfono: ```adb install -r name.apk```
5. Iniciar la app en el teléfono
6. Ejecutar en terminal: ```sudo objection explore```
7. En la terminal que inicia objection: ```android sslpinning disable```
8. Para deshabilitar root detection: ```android root disable```

## Frida

1. Instalar Frida: ```pip install Frida``` ```pip install frida-tools```
2. Descargar script para frida, para root check y ssl-pinning se puede usar: [dsa.js](https://github.com/athanos-sec/security/blob/main/recon/dsa.js)
3. Controlar que el teléfono este en modo debug: Settings -> Developer options -> Habilitar USB debugging mode
4. Conectar mediante adb el teléfono: ```adb connect IP:5555```
5. Verificar arquitectura: ```adb shell getprop ro.product.cpu.abi```
6. Descargar [Frida](https://github.com/frida/frida/releases) según la arquitectura
7. Mover Frida: ```adb push frida-server /data/local/tmp/```
8. Mover certificado: ```adb push cacert.crt /data/local/tmp/cert-der.crt```
9. Dar permisos: ```adb shell chmod +x /data/local/tmp/frida-server```
10. Ejecutar Frida en una terminal: ```adb shell /data/local/tmp/frida-server```
11. Abrir aplicación y verificar el nombre: ```frida-ps -U```
12. Ejecutamos: ```frida -U -l frida-script.js --no-pause -f nomepaquete```

Algunos puntos que pueden ser necesarios:
* Instalar Open GApps, desde el dispositivo o [descargando](https://opengapps.org/) la versión Pico para android y arquitectura correspondiente.
* Instalar [ARM translation](https://github.com/m9rco/Genymotion_ARM_Translation)
