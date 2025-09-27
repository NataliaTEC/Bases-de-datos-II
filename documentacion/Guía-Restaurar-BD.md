# 📘 Guía para restaurar la base de datos AdventureWorks2022 en SQL Server

Esta guía explica paso a paso cómo restaurar la base de datos **AdventureWorks2022** en SQL Server (instalado dentro de WSL con Ubuntu), utilizando **SQL Server Management Studio (SSMS)**.

---

## ✅ Requisitos previos
Antes de iniciar asegúrate de tener:
- **WSL** instalado y configurado con **Ubuntu**.
- **SQL Server 2022** ejecutándose dentro de WSL.
- Conexión a SQL Server desde **SSMS** en Windows.

## 🔽 1. Descargar la base de datos
Descarga el archivo **AdventureWorks2022.bak** desde la página oficial de Microsoft:  
📑 [AdventureWorks - Microsoft Docs](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver17&tabs=ssms)  

```bash
# Desde tu Ubuntu/WSL, descargar la base de datos
wget https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2022.bak
```

Para este ejemplo usaremos la versión **AdventureWorks2022.bak**.


## 💾 2. Copiar el archivo a un directorio accesible por SQL Server:

```bash
# Crear directorio para backups
sudo mkdir -p /var/opt/mssql/backup

# Copiar el archivo (si lo descargaste en WSL)
sudo cp AdventureWorks2022.bak /var/opt/mssql/backup/

# Dar permisos a SQL Server
sudo chown mssql:mssql /var/opt/mssql/backup/AdventureWorks2022.bak
```
Esto facilita el acceso desde SSMS.


## 🖥️ 3. Abrir la opción de restauración en SSMS
En SSMS:  
- Clic derecho sobre **Databases** → **Restore Database...**  
- Se abrirá la ventana de restauración.  

📸 Ejemplo:  
![Abrir opción de restauración](../codigo/src/assets/IMG_SSMS_Backup_0.png)


## 📂 4. Seleccionar el archivo de backup
1. En la ventana, marca la opción **Device**.  
2. Haz clic en los **tres puntos (...)** al lado derecho.  

📸 Ejemplo:  
![Seleccionar Device](../codigo/src/assets/IMG_SSMS_Backup_1.png)


## ➕ 5. Agregar el archivo `.bak`
1. En la nueva ventana, haz clic en **Add**.  
2. Selecciona el archivo **AdventureWorks2022.bak** que moviste al disco C:.  

📸 Ejemplo:  
![Agregar archivo](../codigo/src/assets/IMG_SSMS_Backup_2.png)  

📸 Selección del archivo:  
![Seleccionar archivo .bak](../codigo/src/assets/IMG_SSMS_Backup_3.png)


## 🚀 6. Restaurar la base de datos
Haz clic en **OK** en todas las ventanas abiertas.  
SSMS iniciará el proceso de restauración automáticamente.  

✅ ¡Listo! Ahora la base de datos **AdventureWorks2022** estará disponible en tu servidor SQL y lista para usar. 🎉

