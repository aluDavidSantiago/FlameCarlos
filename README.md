
# Práctica Firewall con UFW – Activitats II (Parte 2)

## Descripción

Este repositorio contiene la práctica correspondiente a **Activitats II – Parte 2**, cuyo objetivo es **configurar y comprobar un firewall en un sistema Linux utilizando UFW (Uncomplicated Firewall)**, aplicando políticas por defecto, reglas específicas de entrada y salida, bloqueo de dominios y control de acceso a servicios.

Todas las configuraciones han sido **verificadas mediante pruebas reales** (ping, acceso web, etc.), siguiendo un enfoque paso a paso.

***

## Entorno de trabajo

*   **Sistema operativo**: Ubuntu Server
*   **Firewall**: UFW
*   **Servicio web**: nginx
*   **Hipervisor**: VirtualBox (o equivalente)

### Adaptadores de red

El servidor dispone de dos adaptadores de red:

*   **NAT (`enp0s3`)**
    *   Usado para salida a Internet
    *   IP asignada: `10.0.2.15`

*   **Host-only (`enp0s8`)**
    *   Usado para pruebas de tráfico entrante
    *   IP del servidor: `192.168.56.146`
    *   IP del anfitrión: `192.168.56.1`

***

## Objetivos de la práctica

*   Comprobar el estado inicial del firewall
*   Aplicar políticas por defecto de entrada y salida
*   Validar el bloqueo y permisos de tráfico mediante pruebas reales
*   Bloquear el acceso a un dominio concreto
*   Permitir el acceso a un servicio web solo desde una IP específica
*   Mostrar la configuración final del firewall

***

## Configuración realizada

### Estado inicial del firewall

*   UFW se encontraba desactivado al inicio.

### Políticas por defecto

*   **Entrada**: denegada por defecto
*   **Salida**: permitida por defecto (tras pruebas con deny/allow)

### Reglas específicas

*   Bloqueo de tráfico de salida hacia el dominio:
    *   `capgros.elnacional.cat`
    *   IPs bloqueadas:
        *   `104.18.9.104`
        *   `104.18.8.104`
*   Permitir tráfico HTTP (puerto 80) **únicamente desde**:
    *   `192.168.56.1` (anfitrión)

***

## Comprobaciones realizadas

Las siguientes pruebas se han realizado para validar la configuración:

*   Ping desde el host al servidor con entrada bloqueada (fallo esperado)
*   Ping a Internet con salida denegada (fallo esperado)
*   Ping a Internet tras permitir salida (éxito)
*   Ping al dominio bloqueado (fallo esperado)
*   Acceso web a nginx desde el anfitrión (éxito)

Todas las pruebas confirman el correcto funcionamiento del firewall según los requisitos.

***

## Estado final del firewall

Al finalizar la práctica, la configuración activa del firewall es la siguiente:

```bash
sudo ufw status numbered
```

Resultado:

    [ 1] 104.18.9.104 DENY OUT Anywhere
    [ 2] 104.18.8.104 DENY OUT Anywhere
    [ 3] 80 ALLOW IN 192.168.56.1

*   Firewall activo
*   Políticas por defecto aplicadas correctamente
*   Reglas específicas funcionando según lo esperado

***

## Conclusión

La práctica se ha completado correctamente, cumpliendo todos los puntos establecidos en el enunciado.  
Se ha configurado un firewall funcional y seguro, aplicando políticas por defecto y reglas específicas, y verificando cada paso mediante pruebas prácticas.

***

## Autor

*   **Nombre**: Santiago Hernandez
*   **Curso / Módulo**: (añadir si procede)
*   **Fecha**: Mayo 2026

***
