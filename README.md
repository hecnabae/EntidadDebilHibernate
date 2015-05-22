# Entidad débil
Una entidad débil es aquélla que no puede identificarse mediante sus propios atributos, de manera que una instancia de la misma se distingue gracias a su relación con otra entidad.

## Ejemplo

### Diseño lógico

```
B(b0: dom_b0, ..., bn: dom_bn)  
  Clave Primaria: {b0} 
A(a0: dom_a0, ..., an: dom_an, b0: dom_b0, {r0: dom_r0})  
  Clave Primaria: {b0, a0}  
  Clave Ajena: {b0} hace referencia a B
```
