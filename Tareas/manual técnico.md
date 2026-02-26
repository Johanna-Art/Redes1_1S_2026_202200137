# Tarea 3 Configuración de VLANs y VTP

* Nombre: Johanna Alexandra Pérez Enriquez 
* carné 202200137
* Redes de Computadoras 1  
* Cesar Sazo
* Fecha: 27 de febrero 2026


# Topología de la red

# Scritp de los comandos
## central
```text
enable
configure terminal
hostname Switch0
vtp mode server
vtp domain USAC
vtp password cisco123
vlan 10
 name ADMIN
vlan 20
 name MERCA
vlan 30
 name VENTAS
interface fastEthernet 0/1
 switchport mode trunk
interface fastEthernet 0/2
 switchport mode trunk
interface fastEthernet 0/3
 switchport mode trunk
end
write memory
```
## Admin vtp client
```text
enable
configure terminal
hostname ADMIN
vtp mode client
vtp domain USAC
vtp password cisco123
interface fastEthernet 0/2
 switchport mode trunk
interface fastEthernet 0/1
 switchport mode access
 switchport access vlan 10
end
write memory
```
## MERCA vtp client
```text
enable
configure terminal
hostname MERCA
vtp mode client
vtp domain USAC
vtp password cisco123
interface fastEthernet 0/1
 switchport mode trunk
interface fastEthernet 0/2
 switchport mode access
 switchport access vlan 20
interface fastEthernet 0/3
 switchport mode access
 switchport access vlan 20
end
write memory
```
## Ventas vtp transparent
```text
enable
configure terminal
hostname VENTAS
vtp mode transparent
vtp domain USAC
vtp password cisco123
vlan 30
 name VENTAS
interface fastEthernet 0/1
 switchport mode trunk
interface fastEthernet 0/2
 switchport mode access
 switchport access vlan 30
interface fastEthernet 0/3
 switchport mode access
 switchport access vlan 30
interface fastEthernet 0/4
 switchport mode access
 switchport access vlan 30
end
write memory
```  

# Pins a los dispositivos
![pc0](./img/pc0.png)
![pc4](./img/pc1.png)
![pc5](./img/pc2.png)
![pc1](./img/pc3.png)
![pc2](./img/pc4.png)
![pc3](./img/pc5.png)

# Configuración de VTP y VLANs
## Switch0
Configuración del Switch0 el central para que se pueda conectar las demas vtp
![Swtich0](./img/c0.png)
![Switch0](./img/c0.1.png)

## ADMIN
![Switch0](./img/c1.png)

## MERCA
![Switch0](./img/c2.png)

## VENTAS
![Switch0](./img/c3.png)



# Asignación de puertos

# Pruebas de conectividad
## Correctas
La pc4 funciona con el apartamento de merca
![ping](./img/ping1.png)

La pc1 funciona con el apartamento de ventas
![ping](./img/ping2.png)


La pc0 funciona

![ping](./img/6.png)

## Fallidas
* La pc0 de ADMIN se hizo los pines de ventas y merca, pero salieron fallidasa
![ping](./img/ping3.png)

* La pc5 de merca fallo en ventas y admin
![ping](./img/ping4.png)

* La pc3 de ventas fallo en admin y merca
![ping](./img/ping5.png)

# Capturas de show vtp status y show vlan brief
## Central
![Show](./img/s1.png)

## Admin
![Show](./img/s2.png)

## Merca
![Show](./img/s3.png)

## Ventas
![Show](./img/s4.png)

# Conclusión 
* Se comprobo que el VTP permite centralizar la administación de VLANs. Al configurar un switch como server, las VLANs creadas se propagan automáticamente a los switches clientes, reduciendo la configuración manual y minimizando errores. El modo transparent permite crear VLANs locales sin afectar el dominio VTP, útil para segmentos aislados.

* Segmentación con VLANs
La creación de las VLANs ADMIN (10), MERCA (20) Y VENTAS (30) se demostró cómo segmentar una red física en múltiples redes lógicas. Esto mejor la seguridad, el rendimiento y la administración del tráfico, ya que los dispositivos de diferentes Vlans no pueden comunicarse directamente sin enrutamiento.

* Se verificó que los puertos Trunk transportan tráfico de múltiples VLANs entre switches, mientras que los puertos Access conectan dispositivos finales a una sola VLAN. La configuración correcta de estos puertos es esencial para que VTP y las VLANs funcionen adecuadamente.