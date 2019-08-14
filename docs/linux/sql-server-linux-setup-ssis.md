---
title: Installieren von SQL Server Integration Services unter Linux
description: In diesem Artikel wird beschrieben, wie SQL Server Integration Services (SSIS) unter Linux ausgeführt werden.
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 68f3497e9f3f47d7e43c2bda0083bc25632d8221
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032435"
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Installieren von SQL Server Integration Services (SSIS) unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Führen Sie die Schritte in diesem Artikel aus, um SQL Server Integration Services (`mssql-server-is`) unter Linux zu installieren. Informationen zu den Features, die in diesem Release von Integration Services für Linux unterstützt werden, finden Sie in den [Versionshinweisen](sql-server-linux-release-notes.md).

Installieren Sie SQL Server Integration-Server für Ihre Plattform:

- [Ubuntu 16.04](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a> Installieren von SSIS unter Ubuntu
Um das `mssql-server-is`-Paket unter Ubuntu zu installieren, führen Sie die folgenden Schritte aus:

1. Importieren Sie die GPG-Schlüssel des öffentlichen Repositorys.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Registrieren Sie das Ubuntu-Repository von Microsoft SQL Server.

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

3. Führen Sie die folgenden Befehle aus, um SQL Server Integration Services zu installieren.

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

4. Führen Sie nach dem Installieren von Integration Services `ssis-conf` aus. Weitere Informationen finden Sie unter [Konfigurieren von SSIS unter Linux mit ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

5. Nachdem die Konfiguration abgeschlossen ist, legen Sie den Pfad fest.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Aktualisieren von SSIS
Wenn Sie `mssql-server-is` bereits installiert haben, können Sie es mit den folgenden Befehlen auf die neueste Version aktualisieren:

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>Entfernen von SSIS
Zum Entfernen von `mssql-server-is` können Sie den folgenden Befehl ausführen:
```bash
sudo apt-get remove mssql-server-is
```

## <a name="RHEL"></a> Installieren von SSIS unter RHEL
Um das `mssql-server-is`-Paket unter RHEL zu installieren, führen Sie die folgenden Schritte aus:

1. Laden Sie die Konfigurationsdatei für das Microsoft SQL Server Red Hat-Repository herunter.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. Führen Sie die folgenden Befehle aus, um SQL Server Integration Services zu installieren.

   ```bash
   sudo yum install -y mssql-server-is
   ```


1. Führen Sie nach der Installation `ssis-conf` aus. Weitere Informationen finden Sie unter [Konfigurieren von SSIS unter Linux mit ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. Nachdem die Konfiguration abgeschlossen ist, legen Sie den Pfad fest.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Aktualisieren von SSIS
Wenn Sie `mssql-server-is` bereits installiert haben, können Sie es mit den folgenden Befehlen auf die neueste Version aktualisieren:

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>Entfernen von SSIS
Zum Entfernen von `mssql-server-is` können Sie den folgenden Befehl ausführen:
```bash
sudo yum remove mssql-server-is
```

## <a name="unattended-installation"></a>Unbeaufsichtigte Installation
Gehen Sie folgendermaßen vor, um beim Ausführen von `ssis-conf setup` eine unbeaufsichtigte Installation auszuführen:
1.  Geben Sie die Option `-n` (keine Aufforderung) an.
2.  Geben Sie erforderliche Werte an, indem Sie Umgebungsvariablen festlegen.

Im folgenden Beispiel werden die folgenden Schritte ausgeführt:
-   SSIS wird installiert.
-   Die Developer-Edition wird durch Angabe eines Werts für die `SSIS_PID`-Umgebungsvariable festgelegt.
-   Die Lizenzbedingungen werden durch Angabe eines Werts für die `ACCEPT_EULA`-Umgebungsvariable akzeptiert.
-   Eine unbeaufsichtigte Installation wird durch Angabe der Option `-n` (keine Aufforderung) ausgeführt.

```
sudo SSIS_PID=Developer ACCEPT_EULA=Y /opt/ssis/bin/ssis-conf -n setup 
```

### <a name="environment-variables-for-unattended-installation"></a>Umgebungsvariablen für die unbeaufsichtigte Installation

| Umgebungsvariable | und Beschreibung |
|---|---|
| **ACCEPT_EULA** | Akzeptiert den SQL Server-Lizenzvertrag bei Festlegung auf einen beliebigen Wert (z.B. `Y`).|
| **SSIS_PID** | Legt die SQL Server-Edition oder den Product Key fest. Die folgenden Werte sind möglich:<br/>Evaluation<br/>Entwickler<br/>Express <br/>Web <br/>Standard<br/>Enterprise <br/>Ein Product Key<br/><br/>Wenn Sie einen Product Key angeben, muss der Product Key die Form `#####-#####-#####-#####-#####` haben, wobei `#` ein Buchstabe oder eine Ziffer ist.  |
| | |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Ausführen von SSIS-Paketen unter Linux finden Sie unter [Extrahieren, Transformieren und Laden von Daten für SQL Server für Linux mit SSIS](sql-server-linux-migrate-ssis.md).

Informationen zum Konfigurieren zusätzlicher SSIS-Einstellungen unter Linux finden Sie unter [Konfigurieren von SQL Server Integration Services unter Linux mit ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="related-content-about-ssis-on-linux"></a>Verwandte Inhalte zu SSIS unter Linux
-   [Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS](sql-server-linux-migrate-ssis.md)
-   [Konfigurieren von SQL Server Integration Services unter Linux mit ssis-conf](sql-server-linux-configure-ssis.md)
-   [Einschränkungen und bekannte Probleme bei SSIS unter Linux](sql-server-linux-ssis-known-issues.md)
-   [Zeitliches Planen der Ausführung von SSIS-Paketen unter Linux mit Cron](sql-server-linux-schedule-ssis-packages.md)
