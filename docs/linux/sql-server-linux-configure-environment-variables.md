---
title: Konfigurieren von SQL Server Einstellungen mit Umgebungsvariablen
description: In diesem Artikel wird beschrieben, wie Sie Umgebungsvariablen verwenden, um bestimmte SQL Server 2017-Einstellungen unter Linux zu konfigurieren.
author: VanMSFT
ms.author: vanto
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 51589a2183043c5c8ea8d1f9bf5d4af6fcc1eea3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419248"
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Konfigurieren von SQL Server Einstellungen mit Umgebungsvariablen unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Sie können mehrere verschiedene Umgebungsvariablen verwenden, um SQL Server 2017 unter Linux zu konfigurieren. Diese Variablen werden in zwei Szenarien verwendet:

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Sie können mehrere verschiedene Umgebungsvariablen verwenden, um SQL Server 2019-Vorschau unter Linux zu konfigurieren. Diese Variablen werden in zwei Szenarien verwendet:

::: moniker-end

- So konfigurieren Sie die anfängliche Einrichtung `mssql-conf setup` mit dem Befehl
- So konfigurieren Sie einen neuen [SQL Server Container in docker](quickstart-install-connect-docker.md)

> [!TIP]
> Wenn Sie SQL Server nach diesen Setup Szenarien konfigurieren müssen, finden Sie weitere Informationen unter [Konfigurieren von SQL Server für Linux mit dem MSSQL-conf-Tool](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Umgebungsvariablen

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

| Umgebungsvariable | Beschreibung |
|-----|-----|
| **ACCEPT_EULA** | Legen Sie für die Variable **ACCEPT_EULA** einen beliebigen Wert fest, um Ihre Zustimmung zum [End-User Licensing Agreement (Benutzerlizenzvertrag)](https://go.microsoft.com/fwlink/?LinkId=746388) zu geben. Diese Einstellung ist für das SQL Server-Image zwingend erforderlich. |
| **MSSQL_SA_PASSWORD** | Konfigurieren Sie das SA-Benutzer Kennwort. |
| **MSSQL_PID** | Legen Sie die SQL Server Edition oder Product Key fest. Zulässige Werte: </br></br>**Evaluation**</br>**Entwickler**</br>**Drückt**</br>**Web**</br>**Standard**</br>**Fangen**</br>**Eine Product Key**</br></br>Wenn eine Product Key angegeben wird, muss Sie das Format # # # # #-# # # # #-# # # # #-# # # # #-# # # # # aufweisen, wobei "#" eine Zahl oder ein Buchstabe ist.|
| **MSSQL_LCID** | Legt die Sprachen-ID fest, die für SQL Server verwendet werden soll. Beispiel: 1036 ist Französisch. |
| **MSSQL_COLLATION** | Legt die Standardsortierung für SQL Server fest. Dadurch wird die Standard Zuordnung der Sprachen-ID (LCID) zur Sortierung überschrieben. |
| **MSSQL_MEMORY_LIMIT_MB** | Legt die maximale Größe des Arbeitsspeichers (in MB) fest, der von SQL Server verwendet werden kann. Der Standardwert ist 80% des gesamten physischen Speichers. |
| **MSSQL_TCP_PORT** | Konfigurieren Sie den TCP-Port, den SQL Server überwacht (standardmäßig 1433). |
| **MSSQL_IP_ADDRESS** | Legen Sie die IP-Adresse fest. Derzeit muss die IP-Adresse im IPv4-Format (0.0.0.0) sein. |
| **MSSQL_BACKUP_DIR** | Legen Sie den Standard Speicherort für das Sicherungs Verzeichnis fest. |
| **MSSQL_DATA_DIR** | Ändern Sie das Verzeichnis, in dem die neuen SQL Server Daten Bank Datendateien (. mdf) erstellt werden. |
| **MSSQL_LOG_DIR** | Ändern Sie das Verzeichnis, in dem die neuen SQL Server-Daten Bank Protokolldateien (LDF) erstellt werden. |
| **MSSQL_DUMP_DIR** | Ändern Sie das Verzeichnis, in dem SQL Server die Speicher Abbilder und andere Dateien für die Problembehandlung standardmäßig ablegen. |
| **MSSQL_ENABLE_HADR** | Aktivieren Sie die Verfügbarkeits Gruppe. Beispielsweise ist ' 1 ' aktiviert, und ' 0 ' ist deaktiviert. |
| **MSSQL_AGENT_ENABLED** | Aktivieren Sie SQL Server-Agent. Beispielsweise ist ' true ' aktiviert, und ' false ' ist deaktiviert. Standardmäßig ist der-Agent deaktiviert.  |
| **MSSQL_MASTER_DATA_FILE** | Legt den Speicherort der Datendatei der Master-Datenbank fest. Muss als **Master. mdf** benannt werden, bis die erste SQL Server ausgeführt wird. |
| **MSSQL_MASTER_LOG_FILE** | Legt den Speicherort der Protokolldatei der Master-Datenbank fest. Muss als " **Mastlog. ldf** " benannt werden, bis die erste SQL Server ausgeführt wird. |
| **MSSQL_ERROR_LOG_FILE** | Legt den Speicherort der ErrorLog-Dateien fest. |

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

| Umgebungsvariable | Beschreibung |
|-----|-----|
| **ACCEPT_EULA** | Legen Sie für die Variable **ACCEPT_EULA** einen beliebigen Wert fest, um Ihre Zustimmung zum [End-User Licensing Agreement (Benutzerlizenzvertrag)](https://go.microsoft.com/fwlink/?LinkId=746388) zu geben. Diese Einstellung ist für das SQL Server-Image zwingend erforderlich. |
| **MSSQL_SA_PASSWORD** | Konfigurieren Sie das SA-Benutzer Kennwort. |
| **MSSQL_PID** | Legen Sie die SQL Server Edition oder Product Key fest. Zulässige Werte: </br></br>**Evaluation**</br>**Entwickler**</br>**Drückt**</br>**Web**</br>**Standard**</br>**Fangen**</br>**Eine Product Key**</br></br>Wenn eine Product Key angegeben wird, muss Sie das Format # # # # #-# # # # #-# # # # #-# # # # #-# # # # # aufweisen, wobei "#" eine Zahl oder ein Buchstabe ist.|
| **MSSQL_LCID** | Legt die Sprachen-ID fest, die für SQL Server verwendet werden soll. Beispiel: 1036 ist Französisch. |
| **MSSQL_COLLATION** | Legt die Standardsortierung für SQL Server fest. Dadurch wird die Standard Zuordnung der Sprachen-ID (LCID) zur Sortierung überschrieben. |
| **MSSQL_MEMORY_LIMIT_MB** | Legt die maximale Größe des Arbeitsspeichers (in MB) fest, der von SQL Server verwendet werden kann. Der Standardwert ist 80% des gesamten physischen Speichers. |
| **MSSQL_TCP_PORT** | Konfigurieren Sie den TCP-Port, den SQL Server überwacht (standardmäßig 1433). |
| **MSSQL_IP_ADDRESS** | Legen Sie die IP-Adresse fest. Derzeit muss die IP-Adresse im IPv4-Format (0.0.0.0) sein. |
| **MSSQL_BACKUP_DIR** | Legen Sie den Standard Speicherort für das Sicherungs Verzeichnis fest. |
| **MSSQL_DATA_DIR** | Ändern Sie das Verzeichnis, in dem die neuen SQL Server Daten Bank Datendateien (. mdf) erstellt werden. |
| **MSSQL_LOG_DIR** | Ändern Sie das Verzeichnis, in dem die neuen SQL Server-Daten Bank Protokolldateien (LDF) erstellt werden. |
| **MSSQL_DUMP_DIR** | Ändern Sie das Verzeichnis, in dem SQL Server die Speicher Abbilder und andere Dateien für die Problembehandlung standardmäßig ablegen. |
| **MSSQL_ENABLE_HADR** | Aktivieren Sie die Verfügbarkeits Gruppe. Beispielsweise ist ' 1 ' aktiviert, und ' 0 ' ist deaktiviert. |
| **MSSQL_AGENT_ENABLED** | Aktivieren Sie SQL Server-Agent. Beispielsweise ist ' true ' aktiviert, und ' false ' ist deaktiviert. Standardmäßig ist der-Agent deaktiviert.  |
| **MSSQL_MASTER_DATA_FILE** | Legt den Speicherort der Datendatei der Master-Datenbank fest. Muss als **Master. mdf** benannt werden, bis die erste SQL Server ausgeführt wird. |
| **MSSQL_MASTER_LOG_FILE** | Legt den Speicherort der Protokolldatei der Master-Datenbank fest. Muss als " **Mastlog. ldf** " benannt werden, bis die erste SQL Server ausgeführt wird. |
| **MSSQL_ERROR_LOG_FILE** | Legt den Speicherort der ErrorLog-Dateien fest. |

::: moniker-end

## <a name="use-with-initial-setup"></a>Verwendung mit der anfänglichen Einrichtung

Dieses Beispiel `mssql-conf setup` wird mit den konfigurierten Umgebungsvariablen ausgeführt. Die folgenden Umgebungsvariablen werden angegeben:

- **ACCEPT_EULA** akzeptiert den Endbenutzer-Lizenzvertrag.
- **MSSSQL_PID** gibt die frei lizenzierte Developer Edition von SQL Server für die nicht produktive Verwendung an.
- **MSSQL_SA_PASSWORD** legt ein sicheres Kennwort fest.
- **MSSQL_TCP_PORT** legt den TCP-Port fest, den SQL Server an 1234 lauscht.

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="use-with-docker"></a>Verwendung mit docker

Der Docker-Beispiel Befehl verwendet die folgenden Umgebungsvariablen, um einen neuen SQL Server Container zu erstellen:

- **ACCEPT_EULA** akzeptiert den Endbenutzer-Lizenzvertrag.
- **MSSSQL_PID** gibt die frei lizenzierte Developer Edition von SQL Server für die nicht produktive Verwendung an.
- **MSSQL_SA_PASSWORD** legt ein sicheres Kennwort fest.
- **MSSQL_TCP_PORT** legt den TCP-Port fest, den SQL Server an 1234 lauscht. Dies bedeutet, dass anstelle von Port 1433 (Standard) einem hostport der benutzerdefinierte TCP-Port mit dem `-p 1234:1234` Befehl in diesem Beispiel zugeordnet werden muss.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Wenn Sie docker unter Linux/macOS ausführen, verwenden Sie die folgende Syntax in einfachen Anführungszeichen:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

Wenn Sie docker unter Windows ausführen, verwenden Sie die folgende Syntax mit doppelten Anführungszeichen:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

> [!NOTE]
> Die Vorgehensweise zum Ausführen von Produktionseditionen in Containern weicht hiervon minimal ab. Weitere Informationen finden Sie unter [Run production container images (Ausführen von Containerimages für Produktionsumgebungen)](sql-server-linux-configure-docker.md#production).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Wenn Sie docker unter Linux/macOS ausführen, verwenden Sie die folgende Syntax in einfachen Anführungszeichen:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

Wenn Sie docker unter Windows ausführen, verwenden Sie die folgende Syntax mit doppelten Anführungszeichen:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Weitere SQL Server Einstellungen, die hier nicht aufgeführt sind, finden Sie unter [Konfigurieren von SQL Server für Linux mit dem MSSQL-conf-Tool](sql-server-linux-configure-mssql-conf.md).

Weitere Informationen zum Installieren und Ausführen von SQL Server für Linux finden Sie unter [Install SQL Server für Linux](sql-server-linux-setup.md).
