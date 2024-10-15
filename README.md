# Modelo Entidad/Relación Viveros

## Entidades Definidas

### Vivero

    Descripción: Representa cada uno de los viveros que posee la empresa.
    Atributos:
        `ID_Vivero (PK)`: Identificador único de cada vivero.
        `Nombre`: Nombre del vivero (ej. "Vivero Norte").
        `Latitud` y `Longitud`: Coordenadas geográficas para su georreferenciación.
    Ejemplo:

    ```json

    {
      "ID_Vivero": 1,
      "Nombre": "Vivero Norte",
      "Latitud": 28.1234,
      "Longitud": -15.4321
    }
    ```

### 2. Zona

    Descripción: Representa las diferentes zonas dentro de un vivero, como almacén, zona exterior, etc.
    Atributos:
        ID_Zona (PK): Identificador único de la zona.
        Nombre: Nombre de la zona (ej. "Exterior").
        Latitud y Longitud: Coordenadas específicas de la zona dentro del vivero.
    Ejemplo:

    json

    {
      "ID_Zona": 101,
      "Nombre": "Almacén",
      "Latitud": 28.1236,
      "Longitud": -15.4325
    }

3. Producto

    Descripción: Productos que se venden en los viveros.
    Atributos:
        ID_Producto (PK): Identificador único del producto.
        Nombre: Nombre del producto (ej. "Maceta grande").
        Stock: Cantidad disponible en stock.
    Ejemplo:

    json

    {
      "ID_Producto": 2001,
      "Nombre": "Maceta grande",
      "Stock": 50
    }

4. Empleado

    Descripción: Representa a los empleados de Tajinaste S.A.
    Atributos:
        ID_Empleado (PK): Identificador único del empleado.
        Nombre: Nombre del empleado (ej. "Juan Pérez").
        Fecha_Contratación: Fecha en la que fue contratado.
    Ejemplo:

    json

    {
      "ID_Empleado": 301,
      "Nombre": "Juan Pérez",
      "Fecha_Contratación": "2020-01-15"
    }

5. Cliente

    Descripción: Representa a los clientes de la empresa que participan en el programa de fidelización Tajinaste Plus.
    Atributos:
        ID_Cliente (PK): Identificador único del cliente.
        Nombre: Nombre del cliente.
        Fecha_Ingreso: Fecha en la que ingresó al programa de fidelización.
    Ejemplo:

    json

    {
      "ID_Cliente": 5001,
      "Nombre": "Ana González",
      "Fecha_Ingreso": "2022-05-10"
    }

6. Pedido

    Descripción: Representa los pedidos realizados por los clientes, y gestionados por los empleados.
    Atributos:
        ID_Pedido (PK): Identificador único del pedido.
        Fecha_Pedido: Fecha en la que se realizó el pedido.
        ID_Cliente (FK): Identificador del cliente que realizó el pedido.
        ID_Empleado (FK): Identificador del empleado responsable de gestionar el pedido.
    Ejemplo:

    json

{
  "ID_Pedido": 7001,
  "Fecha_Pedido": "2024-10-01",
  "ID_Cliente": 5001,
  "ID_Empleado": 301
}