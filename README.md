# Modelo Entidad/Relación Viveros

## Entidades Definidas

1. **Vivero**

    **Descripción**: Representa cada uno de los viveros que posee la empresa.

    **Atributos**:
    - `ID_Vivero (PK)`: Identificador único de cada vivero.
    - `Nombre`: Nombre del vivero (ej. "Vivero Norte").
    - `Latitud` y `Longitud`: Coordenadas geográficas para su georreferenciación.
    
    **Ejemplo**:
    ```json
    {
      "ID_Vivero": 1,
      "Nombre": "Vivero Norte",
      "Latitud": 28.1234,
      "Longitud": -15.4321
    }
    ```

2. **Zona**

    **Descripción**: Representa las diferentes zonas dentro de un vivero, como almacén, zona exterior, etc.

    **Atributos**:
    - `ID_Zona (PK)`: Identificador único de la zona.
    - `Nombre`: Nombre de la zona (ej. "Exterior").
    - `Latitud` y `Longitud`: Coordenadas específicas de la zona dentro del vivero.

    **Ejemplo**:

    ```json
    {
      "ID_Zona": 101,
      "Nombre": "Almacén",
      "Latitud": 28.1236,
      "Longitud": -15.4325
    }
    ```

3. **Producto**

    **Descripción**: Productos que se venden en los viveros.

    **Atributos**:
    - `ID_Producto (PK)`: Identificador único del producto.
    - `Nombre`: Nombre del producto (ej. "Maceta grande").

    **Ejemplo**:
    ```json
    {
      "ID_Producto": 2001,
      "Nombre": "Maceta grande"
    }
    ```

4. **Empleado**

    **Descripción**: Representa a los empleados de Tajinaste S.A.

    **Atributos**:
    - `ID_Empleado (PK)`: Identificador único del empleado.
    - `Nombre`: Nombre del empleado (ej. "Juan Pérez").
    **Ejemplo**:
    ```json
    {
      "ID_Empleado": 301,
      "Nombre": "Juan Pérez",
    }
    ```

5. **Cliente**

    **Descripción**: Representa a los clientes de la empresa

    **Atributos**:
    - `ID_Cliente (PK)`: Identificador único del cliente.
    - `Nombre`: Nombre del cliente.
    - `Tajinaste_Plus`: Si es beneficiario del programa Tajinaste Plus. Su valor es Sí o No.
    - `Volumen_de_compras_mensual` y `Volumen_de_compras_desde_Tajinaste_Plus`: El primero se refiere al volumen de compras hechas ese mes y el segundo al volumen total de compras hechas desde la integración en el programa Tajinaste Plus. Los dos atributos son calculados, ya que pueden ser calculados a través de la relación con la entidad Pedido.

    **Ejemplo**:
    ```json
    {
      "ID_Cliente": 5001,
      "Nombre": "Ana González",
      "Tajinaste_Plus": "Sí",
      "Volumen_de_compras_mensual": 30,
      "Volumen_de_compras_desde_Tajinaste_Plus": 45
    }
    ```

6. **Pedido**

    **Descripción**: Representa los pedidos realizados por los clientes, y gestionados por los empleados.

    **Atributos**:
    - `ID_Pedido (PK)`: Identificador único del pedido.
    - `Fecha_Pedido`: Fecha en la que se realizó el pedido.
    **Ejemplo**:
    ```json
    {
      "ID_Pedido": 7001,
      "Fecha_Pedido": "2024-10-01",
    }
    ```

    ## Relaciones Definidas

### 1. Vivero - Zona
- *Descripción*: Un vivero puede tener múltiples zonas, pero cada zona pertenece a un único vivero.
- *Cardinalidad: Relación **1:N* (Un vivero puede tener varias zonas).
- *Ejemplo*: El Vivero Central (ID_Vivero: 001) tiene las zonas "Zona Exterior" y "Almacén", pero estas zonas solo pertenecen al Vivero Central.

### 2. Zona - Producto (Stock)
- *Descripción*: Una zona puede contener varios productos y un producto puede estar disponible en varias zonas. Se controla la cantidad disponible de cada producto por zona.
- *Cardinalidad: Relación **N:M* (Un producto puede estar en varias zonas y una zona puede contener varios productos).
- *Ejemplo*: La "Palmera Canariense" (ID_Producto: P001) puede estar en la "Zona Exterior" del Vivero Central con 150 unidades y en el "Almacén" del Vivero Norte con 50 unidades.

### 3. Vivero - Empleado (Historial_Puesto)
- *Descripción*: Un empleado solo puede trabajar en un vivero a la vez, pero el historial de sus asignaciones se mantiene a lo largo del tiempo.
- *Cardinalidad: Relación **1:N* (Un vivero puede tener varios empleados, pero un empleado solo trabaja en un vivero a la vez).
- *Ejemplo*: Juan (ID_Empleado: E001) trabaja en el Vivero Central durante enero a marzo de 2023, pero solo en ese vivero.

### 4. Empleado - Zona (Historial_Puesto)
- *Descripción*: Un empleado está asignado a una zona específica dentro de un vivero. La productividad del empleado en esa zona también se registra.
- *Cardinalidad: Relación **1:N* (Un empleado trabaja en una zona a la vez, pero una zona puede tener varios empleados a lo largo del tiempo).
- *Ejemplo*: Juan (ID_Empleado: E001) trabaja en la "Zona Exterior" del Vivero Central durante enero de 2023, pero la zona ha tenido otros empleados en diferentes periodos.

### 5. Cliente - Pedido
- *Descripción*: Un cliente puede realizar varios pedidos, pero un pedido es realizado por un único cliente.
- *Cardinalidad: Relación **1:N* (Un cliente puede tener múltiples pedidos).
- *Ejemplo*: Ana (ID_Cliente: C001) realizó dos pedidos en marzo y abril de 2023.

### 6. Empleado - Pedido
- *Descripción*: Un empleado puede gestionar varios pedidos, pero cada pedido es gestionado por un único empleado.
- *Cardinalidad: Relación **1:N* (Un empleado puede gestionar varios pedidos).
- *Ejemplo*: Juan (ID_Empleado: E001) gestionó los pedidos de marzo de varios clientes.