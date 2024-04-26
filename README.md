# Gestion-Atenciones
### Primer enregable - Python for ETL
### Javier Aquino - javier.aquino@gmail.com
---

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
    - SI [Fecha Termino] es nulo ENTONCES [Fecha Cierre] SINO [Fecha Termino]
- [x] Cree la columna [Dias Cierre], la cual es la diferencia en días entre la [Fecha Real Fin] y [Fecha Creacion].
- [x] Cree la columna [Grupo Dias] basado en la siguiente regla:
    - SI [Dias Cierre] es nulo ENTONCES Nulo
    - SI [Dias Cierre] <= 3 ENTONCES “0 a 3 días”
    - SI [Dias Cierre] <= 7 ENTONCES “4 a 7 días”
    - SI [Dias Cierre] <= 15 ENTONCES “8 a 15 días”
    - SI [Dias Cierre] > 15 ENTONCES “+15 días”
