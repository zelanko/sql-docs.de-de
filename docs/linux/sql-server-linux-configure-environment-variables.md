---
title: Konfigurieren von SQL Server-Einstellungen mit Umgebungsvariablen | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie Sie Umgebungsvariablen verwenden, um bestimmte Einstellungen für SQL Server 2017 unter Linux konfigurieren.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 299a7db7304a0f6a1090d7d60dbbe4a7e451179d
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719418"
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Konfigurieren von SQL Server-Einstellungen mit Umgebungsvariablen unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Sie können mehrere verschiedene Umgebungsvariablen verwenden, so konfigurieren Sie SQL Server 2017 unter Linux. Diese Variablen werden in zwei Szenarien verwendet:

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Sie können mehrere verschiedene Umgebungsvariablen verwenden, so konfigurieren Sie SQL Server-2019 Vorschau unter Linux. Diese Variablen werden in zwei Szenarien verwendet:

::: moniker-end

- So konfigurieren Sie die anfängliche Einrichtung mit dem `mssql-conf setup` Befehl.
- Zum Konfigurieren einer neuen [SQL Server-Container in Docker](quickstart-install-connect-docker.md).

> [!TIP]
> Wenn Sie SQL Server nach der folgenden setupszenarien konfigurieren müssen, finden Sie unter [Konfigurieren von SQL Server unter Linux mit der Mssql-Conf-Tool](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Umgebungsvariablen

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

| Umgebungsvariable | Description |
|-----|-----|
| **ACCEPT_EULA** | Akzeptieren Sie die SQL Server-Lizenzbedingungen, die bei Festlegung auf einen beliebigen Wert (z. B. "Y"). |
| **MSSQL_SA_PASSWORD** | Konfigurieren Sie das Kennwort des SA-Benutzers ein. |
| **MSSQL_PID** | Legen Sie die Edition oder Product Key für SQL Server. Zulässige Werte: </br></br>**Evaluation**</br>**Entwickler**</br>**Express**</br>**Web**</br>**Standard**</br>**Enterprise**</br>**Einen Product key**</br></br>Wenn Sie einen Product Key angeben, muss es in Form von ###-###-###-###-###, sein, wobei "#" eine Zahl oder einem Buchstaben.|
| **MSSQL_LCID** | Legt fest, die Sprach-ID, die für SQL Server verwendet. 1036 ist z. B. Französisch. |
| **MSSQL_COLLATION** | Legt fest, die standardsortierung für SQL Server. Dies überschreibt die standardzuordnung der Sprach-Id (LCID), Sortierung. |
| **MSSQL_MEMORY_LIMIT_MB** | Legt fest, die Höchstmenge an Arbeitsspeicher (in MB), die SQL Server verwenden kann. Standardmäßig ist 80 % des gesamten physischen Arbeitsspeichers. |
| **MSSQL_TCP_PORT** | Konfigurieren Sie den TCP-Port, den SQL Server (Standardport: 1433) überwacht. |
| **MSSQL_IP_ADDRESS** | Legen Sie die IP-Adresse ein. Derzeit muss die IP-Adresse IPv4-Format (0.0.0.0) sein. |
| **MSSQL_BACKUP_DIR** | Legen Sie den Standardspeicherort für das Sicherungsverzeichnis. |
| **MSSQL_DATA_DIR** | Ändern Sie das Verzeichnis, in dem die neuen SQL Server-Datenbank-Datendateien (MDF) erstellt werden. |
| **MSSQL_LOG_DIR** | Ändern Sie das Verzeichnis, in dem die neuen SQL Server-Datenbank-Protokolldatei (.ldf)-Dateien erstellt werden. |
| **MSSQL_DUMP_DIR** | Ändern Sie das Verzeichnis, in dem SQL Server die Speicherabbilder und andere bei der Problembehandlung Dateien standardmäßig ablegt. |
| **MSSQL_ENABLE_HADR** | Aktivieren der Verfügbarkeitsgruppe. Beispielsweise "1" ist aktiviert, und "0" ist deaktiviert. |
| **MSSQL_AGENT_ENABLED** | SQL Server-Agent zu aktivieren. Z. B. "true" aktiviert ist, und "false" ist deaktiviert. Standardmäßig ist der Agent deaktiviert.  |
| **MSSQL_MASTER_DATA_FILE** | Wird der Speicherort der master-Datenbank-Datendatei. Muss den Namen **master.mdf** bis zuerst von SQL Server ausgeführt. |
| **MSSQL_MASTER_LOG_FILE** | Legt den Speicherort der Protokolldatei der master-Datenbank fest. Muss den Namen **mastlog.ldf** bis zuerst von SQL Server ausgeführt. |
| **MSSQL_ERROR_LOG_FILE** | Wird der Speicherort der Dateien im Fehlerprotokoll. |

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

| Umgebungsvariable | Description |
|-----|-----|
| **ACCEPT_EULA** | Akzeptieren Sie die SQL Server-Lizenzbedingungen, die bei Festlegung auf einen beliebigen Wert (z. B. "Y"). |
| **MSSQL_SA_PASSWORD** | Konfigurieren Sie das Kennwort des SA-Benutzers ein. |
| **MSSQL_PID** | Legen Sie die Edition oder Product Key für SQL Server. Zulässige Werte: </br></br>**Evaluation**</br>**Entwickler**</br>**Express**</br>**Web**</br>**Standard**</br>**Enterprise**</br>**Einen Product key**</br></br>Wenn Sie einen Product Key angeben, muss es in Form von ###-###-###-###-###, sein, wobei "#" eine Zahl oder einem Buchstaben.|
| **MSSQL_LCID** | Legt fest, die Sprach-ID, die für SQL Server verwendet. 1036 ist z. B. Französisch. |
| **MSSQL_COLLATION** | Legt fest, die standardsortierung für SQL Server. Dies überschreibt die standardzuordnung der Sprach-Id (LCID), Sortierung. |
| **MSSQL_MEMORY_LIMIT_MB** | Legt fest, die Höchstmenge an Arbeitsspeicher (in MB), die SQL Server verwenden kann. Standardmäßig ist 80 % des gesamten physischen Arbeitsspeichers. |
| **MSSQL_TCP_PORT** | Konfigurieren Sie den TCP-Port, den SQL Server (Standardport: 1433) überwacht. |
| **MSSQL_IP_ADDRESS** | Legen Sie die IP-Adresse ein. Derzeit muss die IP-Adresse IPv4-Format (0.0.0.0) sein. |
| **MSSQL_BACKUP_DIR** | Legen Sie den Standardspeicherort für das Sicherungsverzeichnis. |
| **MSSQL_DATA_DIR** | Ändern Sie das Verzeichnis, in dem die neuen SQL Server-Datenbank-Datendateien (MDF) erstellt werden. |
| **MSSQL_LOG_DIR** | Ändern Sie das Verzeichnis, in dem die neuen SQL Server-Datenbank-Protokolldatei (.ldf)-Dateien erstellt werden. |
| **MSSQL_DUMP_DIR** | Ändern Sie das Verzeichnis, in dem SQL Server die Speicherabbilder und andere bei der Problembehandlung Dateien standardmäßig ablegt. |
| **MSSQL_ENABLE_HADR** | Aktivieren der Verfügbarkeitsgruppe. Beispielsweise "1" ist aktiviert, und "0" ist deaktiviert. |
| **MSSQL_AGENT_ENABLED** | SQL Server-Agent zu aktivieren. Z. B. "true" aktiviert ist, und "false" ist deaktiviert. Standardmäßig ist der Agent deaktiviert.  |
| **MSSQL_MASTER_DATA_FILE** | Wird der Speicherort der master-Datenbank-Datendatei. Muss den Namen **master.mdf** bis zuerst von SQL Server ausgeführt. |
| **MSSQL_MASTER_LOG_FILE** | Legt den Speicherort der Protokolldatei der master-Datenbank fest. Muss den Namen **mastlog.ldf** bis zuerst von SQL Server ausgeführt. |
| **MSSQL_ERROR_LOG_FILE** | Wird der Speicherort der Dateien im Fehlerprotokoll. |

::: moniker-end

## <a name="use-with-initial-setup"></a>Mit der ersten Installation verwenden

In diesem Beispiel führt `mssql-conf setup` Umgebungsvariablen konfiguriert. Die folgenden Umgebungsvariablen werden angegeben:

- **ACCEPT_EULA** akzeptiert den Endbenutzer-Lizenzvertrag.
- **MSSSQL_PID** gibt an, der frei lizenzierten Developer Edition von SQL Server für die Verwendung der nicht für die Produktion.
- **MSSQL_SA_PASSWORD** legt ein sicheres Kennwort ein.
- **MSSQL_TCP_PORT** legt den TCP-Port, der sich bei 1234 von SQL Server überwacht.

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="use-with-docker"></a>Verwendung mit Docker

Diese Beispiel-Docker-Befehl verwendet die folgenden Umgebungsvariablen, um einen neuen SQL Server-Container zu erstellen:

- **ACCEPT_EULA** akzeptiert den Endbenutzer-Lizenzvertrag.
- **MSSSQL_PID** gibt an, der frei lizenzierten Developer Edition von SQL Server für die Verwendung der nicht für die Produktion.
- **MSSQL_SA_PASSWORD** legt ein sicheres Kennwort ein.
- **MSSQL_TCP_PORT** legt den TCP-Port, der sich bei 1234 von SQL Server überwacht. Dies bedeutet, dass anstelle von Mapping-Port 1433 (Standard) mit einem hostPort, der benutzerdefinierte TCP-Port zugeordnet werden muss, mit der `-p 1234:1234` in diesem Beispiel den Befehl.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Wenn Sie Docker unter Linux/MacOS ausführen, verwenden Sie die folgende Syntax mit einfachen Anführungszeichen versehen:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

Wenn Sie Docker für Windows ausführen, verwenden Sie die folgende Syntax mit doppelten Anführungszeichen an:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

> [!NOTE]
> Die Vorgehensweise zum Ausführen von Produktionseditionen in Containern weicht hiervon minimal ab. Weitere Informationen finden Sie unter [Run production container images (Ausführen von Containerimages für Produktionsumgebungen)](sql-server-linux-configure-docker.md#production).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Wenn Sie Docker unter Linux/MacOS ausführen, verwenden Sie die folgende Syntax mit einfachen Anführungszeichen versehen:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

Wenn Sie Docker für Windows ausführen, verwenden Sie die folgende Syntax mit doppelten Anführungszeichen an:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Andere SQL Server-Einstellungen hier nicht aufgeführt wird, finden Sie unter [Konfigurieren von SQL Server unter Linux mit der Mssql-Conf-Tool](sql-server-linux-configure-mssql-conf.md).

Weitere Informationen zum Installieren und Ausführen von SQL Server unter Linux finden Sie unter [Installieren von SQL Server unter Linux](sql-server-linux-setup.md).
