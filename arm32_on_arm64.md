# Compilare e eseguire assembly ARM32 su ARM64

## Installazione Prerequisiti
Per compilare codice ARM32 dobbiamo innanzitutto scaricare i cross-compiler necessari: 

```
sudo apt update
sudo apt install gcc-arm-none-eabi -y
sudo apt install gcc-arm-linux-gnueabihf -y
sudo apt install gcc-aarch64-linux-gnu -y
```

## Compilazione e Esecuzione
Per compilare scrivete il seguente comando:

```
arm-linux-gnueabihf-gcc <nome_sorgente> -o <nome_eseguibile> -ggdb
```

Avremo ora un'eseguibile a cui pero' servono delle librerie di sistema
per essere eseguito per esempio sul nostro Raspberry Pi 4:

- libc6:armhf 
- libstdc++6:armhf

Prima dobbiamo pero' abilitare l'architettura:

```
sudo dpkg --add-architecture armhf
sudo apt update
sudo apt install libc6:armhf libstdc++6:armhf
```

Potrebbe essere necessario per alcuni programmi create un symlink alla libreria a 32 bit:

```
cd /lib
ln -s arm-linux-gnueabihf/ld-2.23.so ld-linux.so.3
```

## Approfondimenti
I cross-compiler forniti dalla Gnu Compiler Collection (GCC) seguono
questa naming convention:

**gcc**-\<architecture\>-\<vendor\>-(\<os\>-)abi

nel nostro caso quello che useremo in particolare sara'

**gcc**-arm-linux-gnueabihf

gcc compilera' per architettura arm per eseguire su linux con l'abi (application binary interface:
lo standard di organizzazione del binario per essere correttamente eseguito dal sistema) gnueabihf.

