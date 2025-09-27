# 📘 Guía para conectar SSMS(Windows) a SQL Server(WLS)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04%20%7C%2024.04-E95420?logo=ubuntu&logoColor=white)](https://ubuntu.com/)  
[![SQL Server](https://img.shields.io/badge/SQL%20Server-Developer%20Edition-CC2927?logo=microsoftsqlserver&logoColor=white)](https://www.microsoft.com/es-es/sql-server/sql-server-downloads)  
[![WSL](https://img.shields.io/badge/WSL-2-0078D6?logo=windows&logoColor=white)](https://learn.microsoft.com/en-us/windows/wsl/)

Guía paso a paso para conectar **SSMS (Windows)** a un **SQL Server** que corre dentro de **WSL (Ubuntu)**.

---

## ✅ Requisitos previos
- **SQL Server** ya instalado y en ejecución dentro de WSL/Ubuntu.
- Conoces la contraseña del usuario sa.
- **SQL Server Management Studio (SSMS)** instalado en Windows.

---
### 0️⃣ Asegurarse de que SQL Server esté corriendo (WSL)
En la terminal de Ubuntu (WSL):
```bash
sudo systemctl start mssql-server
sudo systemctl status mssql-server --no-pager
```
Deberías ver **active (running)** en la salida.

📡 Comprueba qué dirección(es) y puerto está escuchando SQL Server:
```bash
sudo ss -ltnp | grep 1433
# o, si no existe ss:
sudo netstat -tulpen | grep 1433
```
- ✅ Si ves 0.0.0.0:1433 → escucha en todas las interfaces (bueno).
- ⚠️ Si ves 127.0.0.1:1433 → sólo localhost dentro de WSL (ver sección Port proxy más abajo).

## Conectarse 

### 🔶 Método A — Usar `localhost`
1. Abre **SQL Server Management Studio (SSMS)** → **Connect to Server**.  
2. Completa los campos:  
   - **Server type**: Database Engine  
   - **Server name**: `localhost,1433` ó `127.0.0.1,1433`  
   - **Authentication**: SQL Server Authentication  
   - **Login**: `sa`  
   - **Password**: *tu contraseña configurada*  
3. Haz clic en **Connect**.  

✅ Si funciona: ¡Conexión exitosa! 🎉  
⚠️ Si falla, continúa con el **Método B**.  

### 🔷 Método B — Usar la IP de WSL
#### Obtener la IP de WSL
En la terminal de Ubuntu:
```bash
ip addr show eth0
# busca la línea 'inet' dentro de eth0; ejemplo: inet 172.20.240.1/20 -> IP = 172.20.240.1
```
O (más corta):
```bash
hostname -I | awk '{print $1}'
```
✅ Copia la IP (ej.: 172.20.240.1). Ten en cuenta que esa IP cambia cada vez que reinicias WSL y vuelve a intentar el método A colocando la ip copiada en **Server name**.

