# Gestion-Atenciones
### Primer enregable - Python for ETL
### Javier Aquino - javier.aquino@gmail.com
---

## Flujo de Proceso ETL
- El siguiente gráfico muestra el flujo de proceso de **ETL** para la **Gestión de Atenciones**
- Los procesos finales de escribir el **Consolidado En Curso** y **Consolidado Cerrado** no se solicita en el presente entregable, pero se ha desarrollado como un **Bonus Track** para poder completar el flujo

![Flujo del Proceso ETL](<Flujo del Proceso ETL.png>)

## TRANSFORMACIONES A REALIZAR
### BASE TICKETS
#### Tickets Históricos
- [x] Importe la base “Tickets Historico.txt”, indicando que solo se importen las columnas: Numero Ticket, Ubicacion, Service Desk, Estado, Fecha Creacion,
Fecha Termino y Fecha Cierre. Las columnas Fecha Creacion, Fecha Termino y Fecha Cierre deberán tener el tipo de dato fecha.
- [x] Renombre la columna “Numero Ticket” por “TicketID”.
#### Tickets Actuales
- [x] Importe la base “Tickets Actual.txt”, indicando que solo se importen las columnas: Numero Ticket, Ubicacion, Service Desk, Estado, Fecha Creacion, Fecha Termino y Fecha Cierre.
- [x] Renombre la columna “Numero Ticket” por “TicketID”.
- [x] Asigne el tipo de dato fecha a las columnas Fecha Creacion, Fecha Termino y Fecha Cierre.
- [x] Filtre la base actual de tal manera que solo se mantengan aquellos registros donde el TicketID inicia con WO.
- [x] Anexe o concatene la base histórica y la base actual con el fin de crear un dataframe único llamado Tickets.
- [x] En la base Tickets no deberían existir duplicados, usted deberá eliminar los duplicados basados en la base.
- [x] Elimine los duplicados de la base Tickets en base a la siguiente regla: Si existen dos registros cuyo TicketID es igual, debe mantenerse aquel registro donde la [Fecha Creacion] sea la más actual.
- [x] Divida la columna [Ubicación], en las columnas [Agencia] y [AgenciaID], use como delimitador “ - “.
- [x] Asigne el tipo de dato entero a la columna AgenciaID.
- [x] Cree la columna [Fecha Real Fin] basado en la siguiente regla:
```
    - SI [Fecha Termino] es nulo ENTONCES [Fecha Cierre] SINO [Fecha Termino]
```
- [x] Cree la columna [Dias Cierre], la cual es la diferencia en días entre la [Fecha Real Fin] y [Fecha Creacion].
- [x] Cree la columna [Grupo Dias] basado en la siguiente regla:
```
    - SI [Dias Cierre] es nulo ENTONCES Nulo
    - SI [Dias Cierre] <= 3 ENTONCES “0 a 3 días”
    - SI [Dias Cierre] <= 7 ENTONCES “4 a 7 días”
    - SI [Dias Cierre] <= 15 ENTONCES “8 a 15 días”
    - SI [Dias Cierre] > 15 ENTONCES “+15 días”
```
---
### BASE ATENCIONES
#### Importando Atenciones
- [x] Importe los Excel de la carpeta Atenciones, recuerde que la importación se debe realizar de manera masiva.
- [x] De cada Excel solo se deberá importar las columnas:
    - Numero Ticket
    - Tipo de Ticket
    - Proveedor
    - Costo Atencion
- [x] La columna Costo Atencion debe ser de tipo texto.
- [x] La consulta anterior deberá almacenar el resultado en un dataframe llamado Atenciones.
#### Transformando Atenciones
- [x] Cambie el nombre de la columna “Numero Ticket” por “TicketID”.
- [x] Coloque en mayúscula los valores de la columna [Costo Atencion], luego realice el reemplace de la coma por el punto; así también, reemplace los textos “SIN COSTO” y “COSTO CERO” por el valor “0”.
- [x] Convierta la columna [Costo Atencion] al tipo de dato decimal, todos aquellos valores que no se puedan convertir deberían ser reemplazados por nulo.
---
### COMBINAR Y EXPORTAR
- [x] Realice una combinación de tipo Inner Join entre los dataframe Tickets y Atenciones, usando como columna del match [TicketID].
- [x] Del punto anterior usted deberá extraer solo las columnas:
    - TicketID
    - AgenciaID
    - Agencia
    - Service Desk
    - Estado
    - Fecha Creacion
    - Fecha Real Fin
    - Grupo Dias
    - Tipo de Ticket
    - Costo Atencion.
- [x] Cambie el nombre de las columnas [Fecha Real Fin] por [Fecha Cierre], [Tipo de Ticket] por [Tipo Ticket] y [Costo Atencion] por [Costo].
- [x] Exporte la base consolidada en una hoja llamada “Atenciones” perteneciente a un libro de excel llamado “Consolidado.xlsx”.

[Ver el archivo: "Consolidado.xlsx"](Consolidado.xlsx)

---
```
Nota:
- Recuerde que el formato de la fecha debe ser de tipo “dd/mm/yyyy”
- Además para los números decimales se debe tener solo 2 digitos en la parte decimal.
```
