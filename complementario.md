# 📘 Glosario de Virtualización de Entornos GNU/Linux

## 🧩 Conceptos Fundamentales

### 🖥️ Virtualización

Proceso que permite ejecutar varios sistemas operativos o entornos
aislados sobre una misma máquina física, mediante un software llamado
**hipervisor**.

### 🧠 Hipervisor

Programa o capa de software que gestiona las máquinas virtuales (VM).\
Existen dos tipos principales: - **Tipo 1 (bare-metal):** se ejecuta
directamente sobre el hardware. Ej: KVM, Proxmox, Hyper-V.\
- **Tipo 2 (hosted):** se ejecuta sobre un sistema operativo anfitrión.
Ej: VirtualBox, VMware Workstation.

### 💾 Máquina Virtual (VM)

Es una representación virtual de un equipo físico. Tiene su propio
procesador, memoria, disco y sistema operativo, pero todos son simulados
por el hipervisor.

### ⚙️ VirtualBox

Software libre de virtualización tipo 2 desarrollado por Oracle. Permite
crear y gestionar máquinas virtuales en Windows, Linux y macOS.

### 🧰 KVM (Kernel-based Virtual Machine)

Tecnología de virtualización integrada en el kernel de Linux. Permite
convertir un sistema Linux en un hipervisor de tipo 1 de alto
rendimiento.

### 🪟 VMware

Familia de software de virtualización propietaria que incluye **VMware
Workstation**, **VMware Player** y **ESXi** (este último tipo 1).

### 🔒 Hyper-V

Hipervisor desarrollado por Microsoft, incluido en Windows Server y
Windows 10/11 Pro. Permite crear y administrar máquinas virtuales.

### 🧮 Proxmox VE

Plataforma de virtualización basada en Debian que combina **KVM** para
máquinas virtuales completas y **LXC** para contenedores ligeros.

------------------------------------------------------------------------

## 🧑‍💻 Componentes y Recursos

### 🧱 ISO

Archivo de imagen de disco que contiene una copia exacta del contenido
de un medio físico, como un DVD.\
Ejemplo: `debian-12.1.0-amd64-netinst.iso`

### 🗂️ VDI / VMDK / QCOW2

Formatos de disco duro virtual utilizados por los hipervisores: -
**VDI:** usado por VirtualBox.\
- **VMDK:** usado por VMware.\
- **QCOW2:** usado por QEMU/KVM.

### 💡 Snapshot

Punto de restauración del estado actual de una máquina virtual (incluye
RAM, disco y configuración).\
Permite regresar a un momento previo, útil en pruebas o auditorías.

### 🌐 NAT

Modo de red que permite a la máquina virtual acceder a Internet a través
del anfitrión, sin ser visible para otros equipos en la red.

### 🔗 Bridge (Puente)

Modo de red que conecta directamente la VM con la red física del host,
otorgándole una IP del mismo rango.

### 🧩 Red Interna

Configuración de red que permite la comunicación entre VMs dentro del
mismo hipervisor, sin acceso externo.

### 🧭 BIOS / UEFI

Sistemas de arranque del hardware. Algunos hipervisores requieren
habilitar la opción **VT-x / AMD-V** en BIOS/UEFI para permitir la
virtualización.

------------------------------------------------------------------------

## 🐧 Sistemas Operativos

### 🐧 Debian GNU/Linux

Distribución estable de Linux ampliamente usada en entornos de
servidores y virtualización. Es base de otras como Ubuntu o Proxmox.

### 🧑‍🔧 Sistema Anfitrión (Host)

Equipo físico que ejecuta el software de virtualización.

### 🧍‍♂️ Sistema Invitado (Guest)

Sistema operativo que corre dentro de la máquina virtual.

------------------------------------------------------------------------

## ⚙️ Comandos útiles de administración en Debian

``` bash
# Actualizar repositorios e instalar actualizaciones
sudo apt update && sudo apt upgrade -y

# Instalar herramientas básicas de red
sudo apt install net-tools curl vim git -y

# Instalar servicios para pruebas
sudo apt install openssh-server apache2 -y
```

------------------------------------------------------------------------

## 🚨 Troubleshooting Común

  -----------------------------------------------------------------------
  Problema             Posible causa                 Solución
  -------------------- ----------------------------- --------------------
  No hay Internet      Configuración NAT incorrecta  Revisar adaptador de
                                                     red

  VM no arranca        ISO corrupta o mal montada    Reasignar la imagen
                                                     ISO

  Error VT-x/AMD-V     Virtualización deshabilitada  Activar VT-x/AMD-V
                       en BIOS                       

  Máquina lenta        Falta de RAM o CPU asignada   Aumentar recursos en
                                                     la configuración
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 🔐 Conceptos Relacionados

### 🧩 Contenedores

Forma ligera de virtualización a nivel de sistema operativo (como
**Docker** o **LXC**).\
Los contenedores comparten el kernel del host, a diferencia de las VMs
que emulan un sistema completo.

### 🧠 Hyperthreading / Virtualización asistida por hardware

Tecnologías del procesador que mejoran el rendimiento en entornos
virtualizados.

### 🗄️ Backup / Exportación OVA

Exportar una VM como archivo `.ova` permite compartirla o restaurarla en
otro equipo.\
El formato OVA incluye el disco, configuración y hardware virtual.

------------------------------------------------------------------------

## 📚 Recursos Recomendados

-   [Documentación oficial de
    VirtualBox](https://www.virtualbox.org/manual/UserManual.html)\
-   [Manual del administrador de
    Debian](https://www.debian.org/doc/manuals/debian-handbook/)\
-   [Wiki de Libvirt / KVM](https://wiki.libvirt.org/page/Main_Page)\
-   [Proxmox VE Documentation](https://pve.proxmox.com/wiki/Main_Page)

------------------------------------------------------------------------
