# Entidad débil
Una entidad débil es aquélla que no puede identificarse mediante sus propios atributos, de manera que una instancia de la misma se distingue gracias a su relación con otra entidad.

## Ejemplo

Veamos el típico ejemplo que se da en cualquier biblioteca, en la que para cada libro, existen un número de ejemplares del mismo.

### Diseño lógico

```
Libro(id, ...)  
  Clave Primaria: {id} 
Ejemplar(num, ..., libro_id)  
  Clave Primaria: {libro_id, num}  
  Clave Ajena: {libro_id} hace referencia a Libro
```

### Mapeo en Hibernate

```
@Entity
@Table (name="libro")
public class Libro implements Serializable {
  @Id
  @Column(name="id")
  private Long id;
  ...
  @ElementCollection
  @CollectionTable(
    name="ejemplar",
    joinColumns=@JoinColumn(name="libro_id")
  )
  private List<Ejemplar> ejemplares;
  ...
}
  
@Embeddable
public class Ejemplar {
  @Column(name="num")
  private Long num;
  ...
}
```
