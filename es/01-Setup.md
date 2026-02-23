# Configuración Inicial: OS, NVMe y Firewall

## 1. Elección del Sistema Operativo

Mi idea inicial era instalar Debian por ser el estándar en servidores y la base de distros como Kali, Ubuntu, etc. Sin embargo, tras mirar las particularidades de la Raspberry Pi 5, decidí montar Raspberry Pi OS (basado en Debian 13). 
El motivo principal es la compatibilidad de hardware. Me asegura que el Active Cooler y el bus PCIe funcionen sin tener que hacer configuraciones extrañas. De esta forma sigo teniendo el mismo ecosistema apt y la estabilidad de Debian con drivers optimizados para aarch64.

<img width="430" height="210" alt="image" src="https://github.com/user-attachments/assets/fe530458-24af-4f5f-a4d2-387d847aa218" />

## 2. Almacenamiento: Salto al NVMe

Arrancar una Raspberry desde una MicroSD para un lab de hacking es un cuello de botella. Las lecturas/escrituras masivas son lentas y el uso intensivo de logs acaba corrompiendo las tarjetas.
La solución ha sido instalar un HAT PCIe y migrar el sistema a un SSD NVMe Crucial P3 Plus de 500GB. Esto me da velocidades de lectura/escritura reales y permite aprovechar mejor los 16GB de RAM de la placa.

<img width="475" height="137" alt="image" src="https://github.com/user-attachments/assets/dcd952ef-32df-4986-845e-8aa664195c5a" />

## 3. Seguridad Base: Firewall (UFW)
Antes de exponer la máquina o levantar servicios, he configurado UFW (Uncomplicated Firewall) para asegurar el servidor. 
La política es denegar todo el tráfico entrante por defecto y abrir solo SSH para la administración remota.

<img width="577" height="202" alt="image" src="https://github.com/user-attachments/assets/13e12783-033e-4df4-bd15-62cdc45d493c" />
