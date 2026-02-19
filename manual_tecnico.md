# Manual Técnico - Diseño e implementación de red LAN

* Nombre: Johanna Alexandra Pérez Enriquez
* Carné: 202200137
* curso: Redes de computadoras 1
* Catedrátrico: Cesar Sazo

# Descripción del problema
La empresa Constructiva, dedicada al diseño arquitectónico y gestión de proyectos que ha inaugurado un edificio de 3 niveles, el objetivo es centralizar las operaciones, conexiones y diseño de una red LAN confiable para la empresa, que sea funcional y organizado.

# Distribución de dispositivos
## nivel 1
```text

┌──────────────────────────────────────────────────────────────┐
│  PISO 1 — RECEPCIÓN Y ADMINISTRACIÓN GENERAL                 │
├──────────────┬──────────────┬──────────────┬─────────────────┤
│  RECEPCIÓN   │ CONTABILIDAD │    LEGAL     │ SALA REUNIONES  │
│              │              │              │                 │
│  11 PCs      │   8 PCs      │   5 PCs      │   5 PCs + 1 SRV │
│  ┌─┬─┬─┐     │  ┌─┬─┬─┐     │  ┌─┬─┐       │  ┌─┬─┬─┐        │
│  │ │ │ │     │  │ │ │ │     │  │ │ │       │  │ │ │ │        │
│  └─┴─┴─┘     │  └─┴─┴─┘     │  └─┴─┘       │  └─┴─┴─┘        │
└──────────────┴──────────────┴──────────────┴─────────────────┘
                         ▲
                         │ (Cable Crossover)
                    [SW_L1] ← Switch principal piso 1

```
## nivel 2
```text

┌──────────────────────────────────────────────────────────────┐
│  PISO 2 — DISEÑO ARQUITECTÓNICO Y URBANISMO                  │
├──────────────┬──────────────┬────────────────────────────────┤
│ ARQUITECTURA │  URBANISMO   │   SALA REVISIÓN DE PLANOS      │
│              │              │                                │
│   6 PCs      │ 5 PCs + 1 SRV│          5 PCs                 │
│  ┌─┬─┬─┐     │  ┌─┬─┬─┐     │         ┌─┬─┬─┐                │
│  │ │ │ │     │  │ │ │ │     │         │ │ │ │                │
│  └─┴─┴─┘     │  └─┴─┴─┘     │         └─┴─┴─┘                │
└──────────────┴──────────────┴────────────────────────────────┘
                         ▲
                         │ (Cable Crossover)
                    [SW_L2] ← Switch principal piso 2

```
## nivel 3
```text
┌──────────────────────────────────────────────────────────────┐
│  PISO 3 — INGENIERÍA Y DIRECCIÓN DE PROYECTOS                │
├──────────────┬──────────────┬────────────────────────────────┤
│ DIRECCIÓN    │ INGENIERÍA   │    SERVIDORES PRINCIPALES      │
│  GENERAL     │   CIVIL      │                                │
│              │              │                                │
│   4 PCs      │5 PCs + 1 SRV │          3 SRV                 │
│  ┌─┬─┬─┐     │  ┌─┬─┬─┐     │         ┌───┬───┬───┐          │
│  │ │ │ │     │  │ │ │ │     │         │SRV│SRV│SRV│          │
│  └─┴─┴─┘     │  └─┴─┴─┘     │         └───┴───┴───┘          │
└──────────────┴──────────────┴────────────────────────────────┘
                         ▲
                         │ 
                    [SW_L3] ← Switch principal piso 3

```

# Tabla de direcciones IP

| Nivel |1|
|-------|-|
| Departamentos |4|
| Computadoras |29|
| Switch|4|
| Servidor|1|


- Departamento 1: Recepción

||Dispositivo|Display Name|IP|
|-|-|-------|-|
|01|PC|N1D1_PC0|192.178.37.1 /24|
|02|Laptop|N1D1_Laptop0|192.178.37.2 /24|
|03|PC|N1D1_PC1|192.178.37.3 /24|
|04|Laptop|N1D1_Laptop1|192.178.37.4 /24|
|05|PC|N1D1_PC2|192.178.37.5 /24|
|06|Laptop|N1D1_Laptop2|192.178.37.6 /24|
|07|PC|N1D1_PC3|192.178.37.7 /24|
|08|Laptop|N1D1_Laptop3|192.178.37.8 /24|
|09|PC|N1D1_PC4|192.178.37.9 /24|
|10|Laptop|N1D1_Laptop4|192.178.37.10 /24|
|11|PC|N1D1_PC5|192.178.37.11 /24|
|12|Server|N3D10_Server5 |192.168.29.60 /24|


|


- Departamento 2: contabilidad

||Dispositivo|Display Name|IP|
|-|-|-------|-|
|13|Laptop|N1D2_Laptop5|192.178.37.12 /24|
|14|Laptop|N1D2_Laptop6|192.178.37.13 /24|
|15|Laptop|N1D2_Laptop7|192.178.37.14 /24|
|16|Laptop|N1D2_Laptop8|192.178.37.15 /24|
|17|PC|N1D2_PC6 |192.178.37.16 /24|
|18|PC|N1D2_PC7 |192.178.37.17 /24|
|19|PC|N1D2_PC8 |192.178.37.18 /24|
|20|PC|N1D2_PC9|192.178.37.19 /24|


- Departamento 3:  Legal

||Dispositivo|Display Name|IP|
|-|-|-------|-|
|21|PC|N1D3_PC10 |192.178.37.20 /24|
|22|PC|N1D3_PC10 |192.178.37.21 /24|
|23|Laptop|N1D3_Laptop9 |192.178.37.22 /24|
|24|Laptop|N1D3_Laptop10|192.178.37.23 /24|
|25|Laptop|N1D3_Laptop11|192.178.37.24 /24|

- Departamento 4:  Sala de reuniones

||Dispositivo|Display Name|IP|
|-|-|-------|-|
|26|PC|N1D4_PC12 |192.178.37.25 /24|
|27|PC|N1D4_PC13 |192.178.37.26 /24|
|28|PC|N1D4_PC14 |192.178.37.27 /24|
|29|Laptop|N1D4_Laptop12 |192.178.37.28 /24|
|30|Laptop|N1D4_Laptop13 |192.178.37.29 /24|

---

| Nivel |2|
|-------|-|
| Departamentos |3|
| Computadoras |16|
| Switch|4|
| Servidores|1|

- Departamento 5:  Arquitectura

||Dispositivo|Display Name|IP|
|-|-|-------|-|
|31|Laptop|N2D5_Laptop14 |192.178.37.30/24|
|32|Laptop|N2D5_Laptop15 |192.178.37.31 /24|
|33|Laptop|N2D5_Laptop16 |192.178.37.32 /24|
|34|PC|N2D5_PC15 |192.178.37.35 /24|
|35|PC|N2D5_PC16 |192.178.37.34 /24|
|36|PC|N2D5_PC17 |192.178.37.33 /24|


- Departamento 6:  Urbanismo

||Dispositivo|Display Name|IP|
|-|-|-------|-|
|37|PC|N2D6_PC20 |192.178.37.39 /24|
|38|PC|N2D6_PC21 |192.178.37.38 /24|
|39|PC|N2D6_PC22 |192.178.37.37 /24|
|40|PC|N2D6_PC23 |192.178.37.36 /24|
|41|PC|N2D6_PC18 |192.178.37.40 /24|
|42|Server|N3D10_Server0 |192.168.29.41/24|


- Departamento 7:  sala de revisión  de planos

||Dispositivo|Display Name|IP|
|-|-|-------|-|
|43|Laptop|N2D5_PC36 |192.178.37.41 /24|
|44|PC|N2D7_PC24 |192.178.37.44 /24|
|45|PC|N2D7_PC25 |192.178.37.43 /24|
|46|PC|N2D7_PC26 |192.178.37.42 /24|
|47|PC|N2D7_PC19 |192.178.37.61 /24|


---

| **Nivel** |**3**|
|-------|-|
| Departamentos |3|
| Computadoras |9|
| Switch|4|
| Servidores|4|

- Departamento 8: dirección general

||Dispositivo|Display Name|IP|
|-|-|-------|-|
|48|PC|N3D8_PC27 |192.178.29.48 /24|
|49|PC|N3D8_PC28 |192.178.29.45 /24|
|50|PC|N3D8_PC29 |192.178.29.47 /24|
|51|PC|N3D8_PC30 |192.178.29.46 /24|

- Departamento 9:  Ingenieria civil

||Dispositivo|Display Name|IP|
|-|-|-------|-|
|52|PC|N3D9_PC31 |192.178.29.53 /24|
|53|PC|N3D9_PC32 |192.178.29.54 /24|
|54|PC|N3D9_PC33 |192.178.29.58 /24|
|55|PC|N3D9_PC34 |192.178.29.50 /24|
|56|PC|N3D9_PC35 |192.178.29.51 /24|
|57|Server|N3D10_Server1 |192.178.29.52 /24|

- Departamento 10:  Servidores principales

||Dispositivo|Display Name|IP|
|-|-|-------|-|
|58|Server|N3D10_Server2 |192.178.29.55 /24|
|59|Server|N3D10_Server3 |192.178.29.56 /24|
|60|Server|N3D10_Server4|192.178.29.57 /24|

---
## Configuración CLI en Switches

* Paso 1: Acceder al modo privilegiado
```text
enable
```

* Paso 2: Entrar al modo de configuración global, permite modificar la configuración del dispositivo.
```text
configure terminal
```


* Paso 3: Configurar el nombre del switch 
```text
hostname <NOMBRE>
```
* Paso 4: Configurar la contraseña de acceso
```text
enable secret 202200137
```

* Paso 5: Salir del modo de configuración
```text
end
```

* Paso 6: Guardar la configuración 
```text
copy running-config startup-config
```

## Capturas de la configuración de las VPCs
* Departamento 1

![D1](./img/VPCs/1.png)

* Departamento 2

![D2](./img/VPCs/2.png)

* Departamento 3

![D3](./img/VPCs/3.png)

* Departamento 4

![D4](./img/VPCs/4.png)

* Departamento 5

![D5](./img/VPCs/5.png)

* Departamento 6

![D6](./img/VPCs/6.png)

* Departamento 7

![D7](./img/VPCs/7.png)

* Departamento 8

![D8](./img/VPCs/8.png)

* Departamento 9

![D9](./img/VPCs/9.png)

* Departamento 10

![D1](./img/VPCs/10.png)


---
## Capturas de la configuración de los pings 

### 10 pings exitosos realizados:

| # | Origen | Destino | Piso Origen | Piso Destino | Departamento Origen | Departamento Destino |
|---|--------|---------|-------------|--------------|---------------------|----------------------|
| 1 | PC Recepción (192.178.37.2) | PC Contabilidad (192.178.37.14) | 1 | 1 | Recepción | Contabilidad |
| 2 | PC Recepción (192.178.37.4) | PC Arquitectura (192.178.37.32) | 1 | 2 | Recepción | Arquitectura |
| 3 | PC Legal (192.178.37.22) | Servidor Urbanismo (192.178.37.44) | 1 | 2 | Legal | Urbanismo |
| 4 | PC Ingeniería (192.178.37.53) | PC Dirección (192.178.37.46) | 3 | 3 | Ingeniería | Dirección |
| 5 | Laptop Sala Reuniones (192.178.37.29) | Servidor (192.178.37.56) | 1 | 3 | Sala Reuniones | Servidores |
| 6 | PC Planos (192.178.37.42) | PC Contabilidad (192.178.37.15) | 2 | 1 | Planos | Contabilidad |
| 7 | PC Recepción (192.178.37.11) | Laptop Urba (192.178.37.39) | 1 | 2 | Recepción | Urbanismo |
| 8 | PC Dirección (192.178.37.45) | Laptop Arqui (192.178.37.32) | 3 | 2 | Dirección | Arquitectura |
| 9 | Servidor Ingeniería (192.178.37.55) | PC Legal (192.178.37.20) | 3 | 1 | Ingeniería | Legal |
| 10 | Servidores (192.178.37.57) | PC Reuniones (192.178.37.12) | 3 | 1 | Servidores | Sala Reuniones |

* ping 1

![D1](./img/pings/1.png)

* ping 2

![D2](./img/pings/2.png)

* ping 3

![D3](./img/pings/3.png)

* ping 4

![D4](./img/pings/4.png)

* ping 5

![D5](./img/pings/5.png)

* ping 6

![D6](./img/pings/6.png)

* ping 7

![D7](./img/pings/7.png)

* ping 8

![D8](./img/pings/8.png)

* ping 9

![D9](./img/pings/9.png)

* ping 10

![D1](./img/pings/10.png)



---

### *Capturas de pantalla de los switchs*

* Recepcion

![sw](./img/switchs/s1.png)

* Contabilidad

![sw](./img/switchs/s2.png)

* Legal

![sw](./img/switchs/s3.png)

* Reuniones

![sw](./img/switchs/s4.png)

* SWL1

![sw](./img/switchs/s5.png)

* Arquitectura

![sw](./img/switchs/s6.png)

* Urbanismo

![sw](./img/switchs/s7.png)

* SWL2

![sw](./img/switchs/s8.png)

* Departamento de planos

![sw](./img/switchs/s9.png)

* Dirección

![sw](./img/switchs/s10.png)

* Ingenieria

![sw](./img/switchs/s11.png)

* Servidores

![sw](./img/switchs/s12.png)

* SWLL3

![sw](./img/switchs/s13.png)


---

### *Paquete ARP y ICMP en el modo simulación*

* ICMP de 192.178.37.120 a 192.178.37.50

![icmp1](./img/capa/icmp.png)

* modelo osi, capa 2

![osi1](./img/capa/os1.png)

* ARP de de 192.178.37.120 a 192.178.37.50

![ARP1](./img/capa/arp.png)

* modelo osi, capas2

![osi2](./img/capa/osi2.png)
