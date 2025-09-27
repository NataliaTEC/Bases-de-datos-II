# 📘 Guía de instalación de SQL Server en WSL con Ubuntu

[![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04%20%7C%2024.04-E95420?logo=ubuntu&logoColor=white)](https://ubuntu.com/)  
[![SQL Server](https://img.shields.io/badge/SQL%20Server-Developer%20Edition-CC2927?logo=microsoftsqlserver&logoColor=white)](https://www.microsoft.com/es-es/sql-server/sql-server-downloads)  
[![WSL](https://img.shields.io/badge/WSL-2-0078D6?logo=windows&logoColor=white)](https://learn.microsoft.com/en-us/windows/wsl/)  

Guía paso a paso para instalar **SQL Server** en una distribución **Ubuntu** dentro del **Subsistema de Windows para Linux (WSL)**.  
Basada en la [documentación oficial de Microsoft](https://learn.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver17&tabs=ubuntu2004%2C2025ubuntu2204%2Codbc-ubuntu-1804).  

---

## ✅ Requisitos previos

Antes de comenzar asegúrate de:

- Tener [**WSL instalado**](https://www.youtube.com/watch?v=KH1scsIjy6g) y configurado con **Ubuntu** como distribución.  
- Acceso a la **terminal de Ubuntu** dentro de WSL.  
- Conexión a internet estable.  

---

## 💻 Proceso de instalación

### 1️⃣ Abrir la terminal de WSL Ubuntu  
- Inicia la terminal desde **Windows**.  

---

### 2️⃣ Actualizar los paquetes del sistema  
```bash
sudo apt update && sudo apt upgrade -y
````

---

### 3️⃣ Instalar la clave pública de Microsoft

Para **Ubuntu 22.04**, descargue la clave pública, conviértala del formato ASCII al formato GPG y escríbala en la ubicación requerida:

```bash
curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor -o /usr/share/keyrings/microsoft-prod.gpg
```

#### 🚨 Advertencia

Si recibe una **advertencia** acerca de que la clave pública no está disponible, puede utilizar el siguiente comando en su lugar:

```bash
curl https://packages.microsoft.com/keys/microsoft.asc | sudo tee /etc/apt/trusted.gpg.d/microsoft.asc
```

---

### 4️⃣ Descargar el repositorio oficial de SQL Server

Descargue y registre manualmente el repositorio **Ubuntu 22.04** de SQL Server:

```bash
curl -fsSL https://packages.microsoft.com/config/ubuntu/22.04/mssql-server-preview.list | sudo tee /etc/apt/sources.list.d/mssql-server-preview.list
```

---

### 5️⃣ Actualizar las dependencias

Ejecute el siguiente comando para hacer la actualización de las dependencias:

```bash
sudo apt-get update
```

---

### 6️⃣ Instalar SQL Server

Ejecute el siguiente comando para instalar SQL Server:

```bash
sudo apt-get install -y mssql-server
```

---

### 7️⃣ Configuración inicial

Una vez finalizada la instalación del paquete, ejecute **`mssql-conf setup`** y siga las instrucciones para configurar el **usuario `sa`**, su **contraseña** y la **edición** de SQL Server.

⚡ Ediciones con licencia gratuita: **Evaluation, Developer y Express**.

```bash
sudo /opt/mssql/bin/mssql-conf setup
```

* Define la contraseña para el usuario **`sa`**.
* Selecciona la edición de SQL Server (**Developer** recomendada para desarrollo).

---

### 8️⃣ Verificar el estado del servicio

Una vez realizada la configuración, verifique que el servicio se esté ejecutando:

```bash
systemctl status mssql-server --no-pager
```

✔ Si aparece como **active (running)**, la instalación fue exitosa 🎉

⚠️ Si planea conectarse de forma remota, es posible que también necesite abrir el **puerto TCP 1433** en su firewall.

---
