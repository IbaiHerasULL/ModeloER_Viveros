# ModeloER_Viveros

## Entidades y Relaciones

### Vivero
- **Atributos**: `ID_Vivero`, `Nombre`, `Latitud`, `Longitud`
- Relación **1:N** con **Zona**

### Zona
- **Atributos**: `ID_Zona`, `Nombre`, `Latitud`, `Longitud`
- Relación **N:M** con **Producto** a través de **Stock** (`Cantidad_Disponible`)
- Relación **1:N** con **Empleado** a través de **Historial_Puesto**

### Producto
- **Atributos**: `ID_Producto`, `Nombre`, `Descripción`

### Stock
- **Atributos**: `Cantidad_Disponible`

### Empleado
- **Atributos**: `ID_Empleado`, `Nombre`, `Apellido`, `Fecha_Ingreso`, `Rol`
- Relación **1:N** con **Vivero** a través de **Historial_Puesto**
- Relación **1:N** con **Pedido**

### Historial_Puesto
- **Atributos**: `Fecha_Inicio`, `Fecha_Fin`, `Productividad`

### Cliente
- **Atributos**: `ID_Cliente`, `Nombre`, `Apellido`, `Fecha_Ingreso_Tajinaste_Plus`, `Volumen_Compras_Mensual`
- Relación **1:N** con **Pedido**

### Pedido
- **Atributos**: `ID_Pedido`, `Fecha_Pedido`, `Total`


El siguiente diagrama muestra la representación visual del modelo entidad/relación (E/R). (Incluir el diagrama generado en Draw.io aquí).
