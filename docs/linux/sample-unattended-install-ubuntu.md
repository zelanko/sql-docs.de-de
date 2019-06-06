---
title: Unbeaufsichtigte Installation für SQL Server unter Ubuntu
titleSuffix: SQL Server
description: SQL Server-Skriptbeispiel – für die unbeaufsichtigte Installation unter Ubuntu
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: caa08ab4780defb1ddcd6dedd49e261ea9c45625
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66713551"
---
# <a name="sample-unattended-sql-server-installation-script-for-ubuntu"></a>Beispiel: Für die unbeaufsichtigte Installation-SQL Server-Skript für Ubuntu

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Das folgende Bash-Skript installiert die SQL Server 2017 auf Ubuntu 16.04 ohne interaktive Eingabe. Bietet Beispiele für die Installation der Datenbank-Engine, die SQL Server-Befehlszeilentools, SQL Server-Agent und führt Schritte aus, nach der Installation. Sie können optional Volltext-Suchdienst installieren und erstellen einen Administrator.

> [!TIP]
> Wenn Sie ein Skript für die unbeaufsichtigte Installation nicht benötigen, ist die schnellste Möglichkeit zum Installieren von SQL Server, führen die [Schnellstart für Ubuntu](quickstart-install-connect-ubuntu.md). Weitere Informationen zum Setup finden Sie unter [zur Installation von SQL Server unter Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

- Sie benötigen mindestens 2 GB Arbeitsspeicher zum Ausführen von SQL Server unter Linux.
- Das Dateisystem muss **XFS** oder **EXT4**. Andere Dateisysteme, z. B. **BTRFS**, werden nicht unterstützt.
- Weitere Informationen zu den Systemanforderungen finden Sie unter [Systemanforderungen für SQL Server unter Linux](sql-server-linux-setup.md#system).

## <a name="sample-script"></a>Beispielskript

```bash
#!/bin/bash -e

# Use the following variables to control your install:

# Password for the SA user (required)
MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'

# Product ID of the version of SQL server you're installing
# Must be evaluation, developer, express, web, standard, enterprise, or your 25 digit product key
# Defaults to developer
MSSQL_PID='evaluation'

# Install SQL Server Agent (recommended)
SQL_INSTALL_AGENT='y'

# Install SQL Server Full Text Search (optional)
# SQL_INSTALL_FULLTEXT='y'

# Create an additional user with sysadmin privileges (optional)
# SQL_INSTALL_USER='<Username>'
# SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'

if [ -z $MSSQL_SA_PASSWORD ]
then
  echo Environment variable MSSQL_SA_PASSWORD must be set for unattended install
  exit 1
fi

echo Adding Microsoft repositories...
sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
repoargs="$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
sudo add-apt-repository "${repoargs}"
repoargs="$(curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
sudo add-apt-repository "${repoargs}"

echo Running apt-get update -y...
sudo apt-get update -y

echo Installing SQL Server...
sudo apt-get install -y mssql-server

echo Running mssql-conf setup...
sudo MSSQL_SA_PASSWORD=$MSSQL_SA_PASSWORD \
     MSSQL_PID=$MSSQL_PID \
     /opt/mssql/bin/mssql-conf -n setup accept-eula

echo Installing mssql-tools and unixODBC developer...
sudo ACCEPT_EULA=Y apt-get install -y mssql-tools unixodbc-dev

# Add SQL Server tools to the path by default:
echo Adding SQL Server tools to your path...
echo PATH="$PATH:/opt/mssql-tools/bin" >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc

# Optional SQL Server Agent installation:
if [ ! -z $SQL_INSTALL_AGENT ]
then
  echo Installing SQL Server Agent...
  sudo apt-get install -y mssql-server-agent
fi

# Optional SQL Server Full Text Search installation:
if [ ! -z $SQL_INSTALL_FULLTEXT ]
then
    echo Installing SQL Server Full-Text Search...
    sudo apt-get install -y mssql-server-fts
fi

# Configure firewall to allow TCP port 1433:
echo Configuring UFW to allow traffic on port 1433...
sudo ufw allow 1433/tcp
sudo ufw reload

# Optional example of post-installation configuration.
# Trace flags 1204 and 1222 are for deadlock tracing.
# echo Setting trace flags...
# sudo /opt/mssql/bin/mssql-conf traceflag 1204 1222 on

# Restart SQL Server after installing:
echo Restarting SQL Server...
sudo systemctl restart mssql-server

# Connect to server and get the version:
counter=1
errstatus=1
while [ $counter -le 5 ] && [ $errstatus = 1 ]
do
  echo Waiting for SQL Server to start...
  sleep 3s
  /opt/mssql-tools/bin/sqlcmd \
    -S localhost \
    -U SA \
    -P $MSSQL_SA_PASSWORD \
    -Q "SELECT @@VERSION" 2>/dev/null
  errstatus=$?
  ((counter++))
done

# Display error if connection failed:
if [ $errstatus = 1 ]
then
  echo Cannot connect to SQL Server, installation aborted
  exit $errstatus
fi

# Optional new user creation:
if [ ! -z $SQL_INSTALL_USER ] && [ ! -z $SQL_INSTALL_USER_PASSWORD ]
then
  echo Creating user $SQL_INSTALL_USER
  /opt/mssql-tools/bin/sqlcmd \
    -S localhost \
    -U SA \
    -P $MSSQL_SA_PASSWORD \
    -Q "CREATE LOGIN [$SQL_INSTALL_USER] WITH PASSWORD=N'$SQL_INSTALL_USER_PASSWORD', DEFAULT_DATABASE=[master], CHECK_EXPIRATION=ON, CHECK_POLICY=ON; ALTER SERVER ROLE [sysadmin] ADD MEMBER [$SQL_INSTALL_USER]"
fi

echo Done!
```

### <a name="running-the-script"></a>Ausführen des Skripts

So führen Sie das Skript aus

1. Fügen Sie das Beispiel in Ihrem bevorzugten Text-Editor, und speichern Sie sie einen einprägsamen Namen, z. B. `install_sql.sh`.

1. Anpassen von `MSSQL_SA_PASSWORD`, `MSSQL_PID`, und die anderen Variablen, die Sie ändern möchten.

1. Markieren Sie das Skript als ausführbar

   ```bash
   chmod +x install_sql.sh
   ```

1. Führen Sie das Skript

   ```bash
   ./install_sql.sh
   ```

### <a name="understanding-the-script"></a>Dem Skript vertraut
Im ersten Schritt wird das Bash-Skript wird einige Variablen festgelegt. Diese kann entweder "Skriptvariablen, wie im Beispiel" oder "Umgebungsvariablen. Die Variable `MSSQL_SA_PASSWORD` ist **erforderlichen** von SQL Server-Installation, die die anderen sind benutzerdefinierte Variablen, die für das Skript erstellt wurde. Das Beispielskript führt die folgenden Schritte aus:

1. Importieren Sie die öffentlichen Microsoft GPG-Schlüssel.

1. Registrieren Sie den Microsoft-Repositorys für SQL Server und die Befehlszeilentools.

1. Aktualisieren Sie die lokalen Repositorys

1. Installieren von SQL Server

1. Konfigurieren von SQL Server mit der ```MSSQL_SA_PASSWORD``` und das automatische Akzeptieren der Endbenutzer-Lizenzvertrag.

1. Automatisch annehmen Sie des Endbenutzer-Lizenzvertrag für die SQL Server-Befehlszeilentools, installieren Sie sie und installieren Sie das Unixodbc-Dev-Paket.

1. Fügen Sie die SQL Server-Befehlszeilentools, auf den Pfad zur einfacheren Verwendung.

1. Installieren Sie SQL Server-Agent aus, wenn die Skriptvariable ```SQL_INSTALL_AGENT``` standardmäßig festgelegt ist, auf.

1. Installieren Sie SQL Server-Volltextsuche, optional, wenn die Variable ```SQL_INSTALL_FULLTEXT``` festgelegt ist.

1. Sperre für Port 1433 für TCP in der System-Firewall, von einem anderen System eine Verbindung mit SQL Server erforderlich.

1. Legen Sie optional die Ablaufverfolgungsflags des Typs für die Ablaufverfolgung von Deadlocks. (erfordert die auskommentierung der Zeilen aufgehoben)

1. SQL Server ist jetzt installiert werden, damit operative können, starten Sie den Prozess.

1. Stellen Sie sicher, dass SQL Server ordnungsgemäß installiert ist, und alle Fehlermeldungen ausblenden.

1. Erstellen Sie einen neuen Server-Administrator-Benutzer aus, wenn ```SQL_INSTALL_USER``` und ```SQL_INSTALL_USER_PASSWORD``` festgelegt sind.

## <a name="next-steps"></a>Nächste Schritte

Vereinfachen Sie mehrere unbeaufsichtigte Installationen aus, und Erstellen eines eigenständigen Bash-Skripts, das die entsprechenden Umgebungsvariablen festlegt. Sie können Variablen entfernen, die das Beispielskript, verwendet, und platzieren Sie sie in ihren eigenen Bash-Skript.

```bash
#!/bin/bash
export MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'
export MSSQL_PID='evaluation'
export SQL_INSTALL_AGENT='y'
export SQL_INSTALL_USER='<Username>'
export SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'
export SQL_INSTALL_AGENT='y'
```

Führen Sie das Bash-Skript dann wie folgt aus:
```bash
. ./my_script_name.sh
```

Weitere Informationen zu SQL Server unter Linux finden Sie unter [SQL Server unter Linux – Übersicht](sql-server-linux-overview.md).
