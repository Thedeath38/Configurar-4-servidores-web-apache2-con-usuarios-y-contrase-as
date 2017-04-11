[]()

# <center>**CONFIGURACION DE 4 SERVIDORES WEB CON APACHE 2 Y USUARIOS**</center>
## **<span style="color:#68BCFF;">INDICE</span>**
* **[1. Configurar Tarjeta de red Estatica](#1.-Configurar-Tarjeta-de-red-Estatica)**  
* **[2. Instalar y Configurar Servidor Dns](#2.-Instalar-y-Configurar-Servidor-Dns)**
* **[3. Instalar y Configurar Apache2](#3.-Instalar-y-Configurar-Apache2)**

## **1. Configurar Tarjeta de red Estatica**  
  1. configuramos la Tarjeta de red estaticamente, por si reinicias que el servidor,el dhcp del router no te de otra ip  
`sudo nano /etc/network/interfaces`
  ~~~
  # This file describes the network interfaces available on your system
  # and how to activate them. For more information, see interfaces(5).

  #source /etc/network/interfaces.d/*

  # The loopback network interface
  auto lo
  iface lo inet loopback

  # The primary network interface
  auto enp0s3
  #iface enp0s3 inet dhcp
  iface enp0s3 inet static
        address 192.168.1.210
        netmask 255.255.255.0
        gateway 192.168.1.254
        dns-nameservers 192.168.1.210
  ~~~
  **address** = ip que quiere asignarle  
  **netmask** = mascara de red, por defecto `255.255.255.0`  
  **gateway** = La ip re tu router  
  **dns-nameservers** = ip del servidor de DNS. En mi caso le pongo la misma que address porque este pc va a actuar de servidor de DNS.

  2. Reiniciamos la tarjeta de red con uno de estos comandos  
  `sudo service networking restart`
  `sudo /etc/init.d/networking restart`  
  Si no le a funcionado los anteriores reinicia el pc  
  `sudo reboot`  

## **2. Instalar y Configurar Servidor Dns**  

### **2.1. Instalar Servidor Dns**
  1. Para instalar el servidor de DNS usamos el siguiente comando:  
    `sudo apt-get install bind9`

### **2.2. Configurar Servidor Dns**

## **3. Instalar y Configurar Apache2**
