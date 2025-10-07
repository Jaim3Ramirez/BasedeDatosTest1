#BasedeDatosTest1


## 📖 Descripción general
La base de datos **Biblio** está diseñada para la gestión de información relacionada con **libros, autores, editoriales, categorías y préstamos**.  
Permite registrar libros con sus respectivas características, asociarlos con sus autores, editoriales y categorías, además de gestionar el préstamo de ejemplares a usuarios.

---

## 🧩 Estructura general

La base de datos contiene las siguientes tablas principales:

- **Autor**
- **Editorial**
- **Libro**
- **Categoria**
- **Usuario**
- **Prestamo**
- **DetallePrestamo**

Cada tabla está relacionada mediante claves primarias y foráneas que permiten mantener la integridad referencial.

---

## 🗂️ Tablas y campos

### 1. `autor`
| Campo | Tipo | Descripción |
|-------|------|-------------|
| `idAutor` | INT | Identificador único del autor. |
| `nombreAutor` | VARCHAR | Nombre completo del autor. |
| `nacionalidadAutor` | VARCHAR | Nacionalidad del autor. |

---

### 2. `editorial`
| Campo | Tipo | Descripción |
|-------|------|-------------|
| `idEditorial` | INT | Identificador único de la editorial. |
| `nombreEditorial` | VARCHAR | Nombre de la editorial. |
| `direccionEditorial` | VARCHAR | Dirección o ubicación de la editorial. |

---

### 3. `categoria`
| Campo | Tipo | Descripción |
|-------|------|-------------|
| `idCategoria` | INT | Identificador único de la categoría. |
| `nombreCategoria` | VARCHAR | Nombre o tipo de la categoría (Ej. Ciencia, Novela, Historia). |

---

### 4. `libro`
| Campo | Tipo | Descripción |
|-------|------|-------------|
| `idLibro` | INT | Identificador único del libro. |
| `titulo` | VARCHAR | Título del libro. |
| `anioPublicacion` | INT | Año en que fue publicado. |
| `idAutor` | INT | Clave foránea que referencia a **Autor**. |
| `idEditorial` | INT | Clave foránea que referencia a **Editorial**. |
| `idCategoria` | INT | Clave foránea que referencia a **Categoria**. |

**Relaciones:**
- Un **autor** puede tener varios **libros**.
- Una **editorial** puede publicar varios **libros**.
- Una **categoría** puede agrupar varios **libros**.

---

### 5. `usuario`
| Campo | Tipo | Descripción |
|-------|------|-------------|
| `idUsuario` | INT | Identificador único del usuario. |
| `nombreUsuario` | VARCHAR | Nombre completo del usuario. |
| `telefonoUsuario` | VARCHAR | Teléfono de contacto. |
| `correoUsuario` | VARCHAR | Correo electrónico. |

---

### 6. `prestamo`
| Campo | Tipo | Descripción |
|-------|------|-------------|
| `idPrestamo` | INT | Identificador único del préstamo. |
| `fechaPrestamo` | DATE | Fecha en la que se realiza el préstamo. |
| `fechaDevolucion` | DATE | Fecha prevista para la devolución. |
| `idUsuario` | INT | Clave foránea que referencia a **Usuario**. |

**Relaciones:**
- Un **usuario** puede tener varios **préstamos**.
- Cada **préstamo** pertenece a un único usuario.

---

### 7. `detallePrestamo`
| Campo | Tipo | Descripción |
|-------|------|-------------|
| `idDetallePrestamo` | INT | Identificador único del detalle. |
| `idPrestamo` | INT | Clave foránea que referencia a **Prestamo**. |
| `idLibro` | INT | Clave foránea que referencia a **Libro**. |

**Relaciones:**
- Un **préstamo** puede incluir varios **libros**.
- Un **libro** puede estar incluido en varios **préstamos** (a lo largo del tiempo).

---

## 🔗 Relaciones principales

- **Autor (1) — (N) Libro**  
- **Editorial (1) — (N) Libro**  
- **Categoría (1) — (N) Libro**  
- **Usuario (1) — (N) Préstamo**  
- **Préstamo (1) — (N) DetallePréstamo — (N) Libro**

---

## 🧱 Diagrama conceptual (resumen en texto)


---

## 💾 Notas técnicas

- Todas las claves primarias (`idAutor`, `idLibro`, etc.) son autoincrementales.
- Se recomienda usar el motor **InnoDB** para soportar claves foráneas.
- Las relaciones están configuradas con integridad referencial (ON DELETE / ON UPDATE CASCADE).
- Las fechas deben almacenarse en formato `YYYY-MM-DD`.

---

## 👤 Autor del modelo

**Jaime Ramírez Jauregui**  
Proyecto académico de gestión bibliotecaria — 2025

---

## 🧾 Licencia

Uso educativo. Se permite la modificación y distribución con fines académicos.
