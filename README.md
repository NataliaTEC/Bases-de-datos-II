# 🔄 Replicación en SQL Server con AdventureWorks
[![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04%20%7C%2024.04-E95420?logo=ubuntu&logoColor=white)](https://ubuntu.com/)  
[![SQL Server](https://img.shields.io/badge/SQL%20Server-Developer%20Edition-CC2927?logo=microsoftsqlserver&logoColor=white)](https://www.microsoft.com/es-es/sql-server/sql-server-downloads)  
[![WSL](https://img.shields.io/badge/WSL-2-0078D6?logo=windows&logoColor=white)](https://learn.microsoft.com/en-us/windows/wsl/)

## 📖 Introducción
Las **bases de datos distribuidas** se han convertido en un componente fundamental en los sistemas de información modernos.  
Cuando múltiples aplicaciones o sedes requieren acceder a los mismos datos, surge la necesidad de **sincronización** y **consistencia**.

**Microsoft SQL Server** ofrece un conjunto de herramientas denominadas **replicaciones**, cuyo objetivo es **copiar y distribuir datos y objetos de bases de datos de un servidor a otro**, manteniendo la coherencia de la información.

### 📌 Tipos de replicación en SQL Server
- **📸 Replicación de instantánea (Snapshot Replication):** copia los datos completos en un momento específico.  
- **⚡ Replicación transaccional (Transactional Replication):** replica cambios en **tiempo casi real** (ideal para sistemas críticos).  
- **🔀 Replicación de mezcla (Merge Replication):** permite que diferentes servidores hagan cambios y luego se sincronicen.

Esta investigación busca dar al estudiante un **primer acercamiento** a estas funcionalidades, que resultan especialmente útiles en entornos donde se trabaja con **bases de datos distribuidas**.

---

## 📝 Descripción del proyecto
Se trabajará con **dos bases de datos AdventureWorks** en un mismo servidor SQL Server.

El objetivo es **configurar la replicación** para que las tablas:

- `Production.Product`  
- `Production.ProductCategory`  
- `Production.ProductSubcategory`  

puedan replicar operaciones de:  
- **Insertar**  
- **Modificar**  
- **Eliminar**

entre ambas bases de datos.

---

## 🎯 Guías

- [Guía de instalación de SQL Server en WSL con Ubuntu](https://github.com/NataliaTEC/Bases-de-datos-II/blob/5fa204b470f3e819bacafaf4f9c142a7d022e767/documentacion/Gu%C3%ADa-de-instalaci%C3%B3n-SQL-WSL-Ubuntu.md)
- [Guía para instalas las herramientas de línea de comandos de SQL Server](https://github.com/NataliaTEC/Bases-de-datos-II/blob/69c099e34cbdeb3d3548abaf11ff0ce051ededa5/documentacion/Guia-instalar-herramientas-de-linea-comandos-SQLServer.md)
- [Guía para conectar SSMS(Windows) a SQL Server(WLS)](https://github.com/NataliaTEC/Bases-de-datos-II/blob/5fa204b470f3e819bacafaf4f9c142a7d022e767/documentacion/Gu%C3%ADa-para-conectar-SSMS-SQLServer.md)
- [Guía para restaurar la base de datos AdventureWorks2022 en SQL Server](https://github.com/NataliaTEC/Bases-de-datos-II/blob/5fa204b470f3e819bacafaf4f9c142a7d022e767/documentacion/Gu%C3%ADa-Restaurar-BD.md)

---
