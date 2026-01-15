# GUÍA COMPLETA DEL TALLER DE AUDITORÍA WEB CON IA
## OWASP Juice Shop · Pentesting Web Moderno (2026)

---

## 1. SQL INJECTION

## 2. BURP SUITE: CONCEPTOS FUNDAMENTALES

Burp Suite es un **proxy de interceptación**.  
Se sitúa entre el navegador y la aplicación web, permitiendo **ver, modificar y reenviar tráfico HTTP/HTTPS**.

Flujo básico:

Navegador → Burp Suite → Aplicación web  
Aplicación web → Burp Suite → Navegador

Nada ocurre sin que Burp lo vea.

---

## 4. INTERFAZ DE BURP SUITE Y COMPONENTES

### 4.1 Proxy

Función:
- Interceptar peticiones y respuestas
- Analizar tráfico en tiempo real

Elementos clave:
- Intercept ON/OFF: detener peticiones
- HTTP history: historial completo del tráfico
- WebSockets history: tráfico en tiempo real

Uso en el taller:
- Detectar parámetros vulnerables
- Identificar endpoints y APIs ocultas

![Interfaz de Burp Suite](../SQL_INJECTION/img/Paso1.PNG)


---

### 4.2 Repeater

Función:
- Repetir y modificar peticiones manualmente

Para qué sirve:
- Probar payloads con control total
- Confirmar vulnerabilidades
- Comparar respuestas

Regla:
> **Todo hallazgo serio pasa por Repeater**

![Interfaz de Burp Suite](../SQL_INJECTION/img/Paso3.PNG)
---

### 4.3 Intruder

Función:
- Automatizar ataques controlados

Usos típicos:
- Fuerza bruta
- Fuzzing de parámetros
- Enumeración de valores

Nota:
En versión Community es lento, pero suficiente para aprendizaje.

![Interfaz de Burp Suite](../SQL_INJECTION/img/Paso2.PNG)
---

### 4.4 Decoder

Función:
- Codificar y decodificar datos

Usos:
- URL Encoding
- Base64
- Hexadecimal

Muy útil para:
- Poison Null Byte
- Bypass de validaciones

![Interfaz de Burp Suite](../SQL_INJECTION/img/Paso4.PNG)

---

### 4.5 Comparer

Función:
- Comparar respuestas HTTP

Útil para:
- Ver diferencias sutiles
- Detectar cambios de comportamiento

![Interfaz de Burp Suite](../SQL_INJECTION/img/Paso5.PNG)
---

## 5. METODOLOGÍA DE AUDITORÍA

1. Definir alcance
2. Discovery y enumeración
3. Análisis técnico
4. Evaluación de riesgo
5. Mitigación
6. Reporte

---

## 6. CASO PRÁCTICO 1: SQL INJECTION

### 6.1 Objetivo

Detectar una SQL Injection en el buscador de productos y explotarla de forma controlada.

---

### 6.2 Pasos guiados

1. Abrir Burp Suite → Proxy → Open Browser
2. Acceder a Juice Shop
3. Usar el buscador con un término normal
4. En Proxy → HTTP history localizar:
   GET /rest/products/search?q=apple
5. Enviar la petición a Repeater
6. Modificar el parámetro q por:
   '
7. Enviar la petición

Resultado esperado:
- Error SQL  o satisfactorio→ vulnerabilidad confirmada

---

### 6.3 Explotación

Pista:
- La consulta devuelve 9 columnas
- Existe una tabla Users



