# Modelo Entidad/Relación - Tajinaste S.A.

Este proyecto documenta el modelo entidad/relación para **Tajinaste S.A.**, una empresa dedicada a la venta de plantas, productos de jardinería y decoración a través de su red de viveros. El objetivo principal es llevar un control del stock, empleados, clientes y pedidos en los viveros.

## Entidades

### 1. Vivero
- **Descripción**: Representa un vivero de la empresa.
- **Atributos**:
  - `ID_Vivero` (PK): Identificador único del vivero.
  - `Nombre`: Nombre del vivero (e.g., "Vivero Norte").
  - `Latitud`, `Longitud`: Coordenadas geográficas del vivero.

**Ejemplo**:
```json
{
  "ID_Vivero": 1,
  "Nombre": "Vivero Norte",
  "Latitud": 28.1234,
  "Longitud": -15.4321
}

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
