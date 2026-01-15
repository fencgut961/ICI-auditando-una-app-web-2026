## Soluciones

- `%25` representa el carácter `%`
- `%2500` se decodifica finalmente como `%00`, que es el **Null Byte**

El resultado es que:

- La aplicación ve un archivo que termina en `.md` (y lo permite)
- El sistema de archivos corta el nombre en el Null Byte y abre el archivo real, ignorando la extensión falsa

De esta forma, la validación se cumple, pero el archivo que se descarga **no es realmente un `.md`**, lo que nos permite acceder a archivos que deberían estar bloqueados.

---

## Retos que se pueden completar con este método

Gracias a este tipo de ataque, es posible completar los siguientes retos:

- Access a developer’s forgotten backup file  
- Access a salesman’s forgotten backup file  
- Access a misplaced SIEM signature file  
- Find the hidden easter egg  