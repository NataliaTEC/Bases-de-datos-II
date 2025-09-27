
## 📘 Guía para instalas las herramientas de línea de comandos de SQL Server
[![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04%20%7C%2024.04-E95420?logo=ubuntu&logoColor=white)](https://ubuntu.com/)  
[![SQL Server](https://img.shields.io/badge/SQL%20Server-Developer%20Edition-CC2927?logo=microsoftsqlserver&logoColor=white)](https://www.microsoft.com/es-es/sql-server/sql-server-downloads)  
[![WSL](https://img.shields.io/badge/WSL-2-0078D6?logo=windows&logoColor=white)](https://learn.microsoft.com/en-us/windows/wsl/)  

Para crear una base de datos, debe conectarse con una herramienta que pueda ejecutar declaraciones Transact-SQL en SQL Server. Los siguientes pasos instalan las herramientas de línea de comandos de SQL Server: [utilidad sqlcmd](https://learn.microsoft.com/en-us/sql/tools/sqlcmd/sqlcmd-utility?view=sql-server-ver17&tabs=go%2Cwindows-support&pivots=cs1-bash) y [utilidad bcp](https://learn.microsoft.com/en-us/sql/tools/bcp-utility?view=sql-server-ver17&tabs=windows).

### 1️⃣ Modo superUsuario
Ingrese al modo superusuario mediante el comando

```bash
sudo su
```

### 2️⃣ Importar claves
Importe las claves GPG del repositorio público: 

```bash
curl https://packages.microsoft.com/keys/microsoft.asc | sudo tee /etc/apt/trusted.gpg.d/microsoft.asc
```

### 3️⃣ Resgitrar el repositorio
Registre el repositorio de Microsoft Ubuntu: 

```bash
curl https://packages.microsoft.com/config/ubuntu/22.04/prod.list | tee /etc/apt/sources.list.d/mssql-release.list
```

### 4️⃣ Salir del modo superUsuario
Mediante el comando salimos del modo de superUsuario:

```bash
exit
```

### 5️⃣ Actualizar paquetes e instalar de la herramienta
Ahora se utilizan los comandos:

```bash
sudo apt-get update
sudo apt-get install mssql-tools18 unixodbc-dev
```

Para **actualizar** a la última versión de herramientas mssql, ejecute los siguientes comandos:

```bash
sudo apt-get update
sudo apt-get install mssql-tools18
```

### 🚨 Opcional
Agregar **`opt/mssql-tools18/bin/`** a tu PATH variable de entorno en un shell bash.
Para hacer sqlcmd y bcp accesible desde el shell bash para sesiones de inicio de sesión, modifique su **`PATH`** en el **`~/.bash_profile`** archivo con el siguiente comando:

```bash
echo 'export PATH="$PATH:/opt/mssql-tools18/bin"' >> ~/.bash_profile
source ~/.bash_profile
```

Para hacer sqlcmd y bcp accesible desde el shell bash para sesiones interactivas/sin inicio de sesión, modifique el **`PATH`** en el **`~/.bashrc`** archivo con el siguiente comando:

```bash
echo 'export PATH="$PATH:/opt/mssql-tools18/bin"' >> ~/.bashrc
source ~/.bashrc
```
### 📡 Conéctese localmente
Correr sqlcmd con parámetros para su nombre de SQL Server (**`-S`**), el nombre de usuario (**`-U`**), y la contraseña (**`-P`**). En esta guía, te conectas localmente, por lo que el nombre del servidor es **`localhost`**. El nombre de usuario es **`sa`** y la contraseña es la que proporcionaste para el **`sa`** cuenta durante la configuración. 
Para probarlo ejecuta el siguiente comando:
```bash
sqlcmd -S localhost -U sa -P '<password> -C'
```
⚠️ Remplaza **`<password>`** por la contraseña que estableciste a la hora de instalar SQL Server.
