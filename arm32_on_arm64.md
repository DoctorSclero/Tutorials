# Compilare e eseguire assembly ARM32 su ARM64

## Installazione Prerequisiti
Per compilare codice ARM32 dobbiamo innanzitutto scaricare i cross-compiler necessari: 

```
sudo apt update \
sudo apt install gcc-arm-none-eabi -y
sudo apt install gcc-arm-linux-gnueabihf -y
sudo apt install gcc-aarch64-linux-gnu -y
```

## Compilazione
Per compilare scrivete il seguente comando:

```
arm-linux-gnueabihf-gcc <nome_sorgente> -o <nome_eseguibile>
```

## Approfondimenti
I cross-compiler forniti dalla Gnu Compiler Collection (GCC) seguono
questa naming convention:

**gcc**-<architecture>-<vendor>-(<os>-)abi

nel nostro caso quello che useremo in particolare sara'

**gcc**-arm-linux-gnueabihf

gcc compilera' per architettura arm per eseguire su linux con l'abi (application binary interface:
lo standard di organizzazione del binario per essere correttamente eseguito dal sistema) gnueabihf.

