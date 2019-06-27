---
title: Konfigurieren von Nutzung und Erfassung von Diagnosedaten für SQLServer unter Linux | Microsoft-Dokumentation
description: Beschreibt, wie SQL Server Customer nutzungs- und Diagnosedaten gesammelt und auf Linux konfiguriert.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: bf15eb58412bda764b710f48bd90be849748000e
ms.sourcegitcommit: 65ceea905030582f8d89e75e97758abf3b1f0bd6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67399988"
---
# <a name="configure-usage-and-diagnostic-data-collection-for-sql-server-on-linux"></a>Konfigurieren von Nutzung und Erfassung von Diagnosedaten für SQLServer unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Microsoft SQL Server erfasst standardmäßig Informationen darüber, wie Kunden die Anwendung verwenden. Dies bedeutet, dass SQL Server Informationen zur Installationserfahrung, Nutzung und Leistung sammelt. Mit diesen Informationen kann Microsoft besser an die Bedürfnisse der Kunden anpassen. Microsoft erfasst z.B. Informationen zu Fehlercodes von Kunden, sodass wir damit verknüpfte Probleme beheben, die Dokumentation zu SQL Server verbessern und bestimmen können, ob wir dem Produkt weitere Funktionen hinzufügen müssen, um die Benutzererfahrung zu optimieren.

Dieses Dokument enthält Informationen darüber, welche Arten von Informationen gesammelt werden und Informationen zum Konfigurieren von Microsoft SQL Server unter Linux zum Senden von diesem gesammelten Informationen an Microsoft. SQL Server 2017 beinhaltet eine datenschutzerklärung, die Informationen erläutert, wir und keine von Benutzern sammeln. Weitere Informationen finden Sie unter den [Datenschutzbestimmungen](https://go.microsoft.com/fwlink/?LinkID=868444).

Microsoft sendet nicht die folgenden Informationen mit diesem Mechanismus:

- Werte aus Benutzertabellen
- Anmeldeinformationen oder andere Authentifizierungsinformationen
- personenbezogene Informationen (PII)

SQL Server 2017 erfasst und sammelt kontinuierlich Informationen zur Installationserfahrung des Einrichtungsvorgangs, damit wir schnell Installationsprobleme erkennen und beheben können, die der Kunde hat. SQL Server 2017 kann so konfiguriert werden, nicht, dass Informationen (pro Instanz pro Server) über an Microsoft senden **Mssql-Conf**. MSSQL-Conf ist ein Konfigurationsskript, das mit SQL Server 2017 für Red Hat Enterprise Linux, SUSE Linux Enterprise Server und Ubuntu installiert.

> [!NOTE]
> Sie können das Senden von Informationen an Microsoft nur in bezahlten Versionen von SQL Server deaktivieren.

## <a name="disable-usage-and-diagnostic-data-collection"></a>Deaktivieren Sie die Nutzung und Erfassung von Diagnosedaten

Diese Option können Sie die ändern, wenn SQL Server Nutzung und Erfassung von Diagnosedaten an Microsoft oder nicht sendet. Dieser Wert wird standardmäßig festgelegt auf "true". Um den Wert zu ändern, führen Sie die folgenden Befehle aus:

> [!IMPORTANT]
> Sie können nicht die Nutzung und Erfassung von Diagnosedaten für kostenlose Editionen von SQL Server "," Express "und" Developer deaktivieren.

### <a name="on-red-hat-suse-and-ubuntu"></a>Red Hat, SUSE und Ubuntu

1. Führen Sie das Mssql-Conf-Skript als Root-Benutzer mit der **festgelegt** Befehl **telemetry.customerfeedback**. Das folgende Beispiel deaktiviert die Nutzung und Erfassung von Diagnosedaten durch Angabe **"false"** .

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Starten Sie SQL Server-Dienst neu:

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>Für Docker
Um Nutzung und Erfassung von Diagnosedaten für Docker zu deaktivieren, müssen Sie Docker [speichern Ihre Daten](sql-server-linux-configure-docker.md). 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Hinzufügen einer `mssql.conf` -Datei mit den Zeilen `[telemetry]` und `customerfeedback = false` im Hostverzeichnis:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```

2. Ausführen des containerimages

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Hinzufügen einer `mssql.conf` -Datei mit den Zeilen `[telemetry]` und `customerfeedback = false` im Hostverzeichnis:

   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```

2. Ausführen des containerimages

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```

::: moniker-end

## <a name="local-audit-for-sql-server-on-linux-usage-and-diagnostic-data-collection"></a>Lokale Überwachung für SQLServer unter Verwendung von Linux und Erfassung von Diagnosedaten

Microsoft SQL Server 2017 enthält Internetaktivierte Features, die gesammelt und Informationen über Ihren Computer oder Gerät ("Standardcomputerinformationen") an Microsoft senden können. Die lokale Überwachung-Komponente des SQL Server-Verwendungs-und Diagnosedaten kann in einen bestimmten Ordner, die Darstellung der Daten (Protokolle), die an Microsoft gesendet werden, von dem Dienst erfassten Daten schreiben. Der Zweck der lokalen Überwachung besteht darin, dass es Benutzern gestattet wird, alle Daten hinsichtlich Zustimmung, behördlicher Bestimmungen oder aus Datenschutzgründen anzuzeigen, die Microsoft mithilfe dieses Features erfasst.

In SQL Server unter Linux kann die lokale Überwachung auf Instanzebene für SQL Server-Datenbank-Engine konfiguriert. Andere SQL Server-Komponenten und die SQL Server-Tools müssen sich nicht auf lokale die Überwachungsfunktion für Nutzung und Erfassung von Diagnosedaten aus.

### <a name="enable-local-audit"></a>Lokale Überwachung aktivieren

Diese Option ermöglicht die lokale Überwachung und können Sie das Verzeichnis festlegen, in die Protokolle der lokalen Überwachung erstellt werden.

1. Erstellen Sie ein Zielverzeichnis für neue Protokolle der lokalen Überwachung. Das folgende Beispiel erstellt ein neues **/Tmp/Audit** Verzeichnis:

   ```bash
   sudo mkdir /tmp/audit
   ```

2. Ändern Sie den Besitzer und die Gruppe des Verzeichnisses, das die **Mssql** Benutzer:

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

3. Führen Sie das Mssql-Conf-Skript als Root-Benutzer mit der **festgelegt** Befehl **telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

4. Starten Sie SQL Server-Dienst neu:

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>Für Docker
Um die lokale Überwachung für Docker zu aktivieren, müssen Sie Docker [speichern Ihre Daten](sql-server-linux-configure-docker.md). 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Das Zielverzeichnis für die neue lokale Überwachungsprotokolle werden im Container. Erstellen Sie ein Zielverzeichnis für die neue lokale Überwachungsprotokolle, in die Hostverzeichnis auf Ihrem Computer. Das folgende Beispiel erstellt ein neues **/audit** Verzeichnis:

   ```bash
   sudo mkdir <host directory>/audit
   ```

1. Hinzufügen einer `mssql.conf` -Datei mit den Zeilen `[telemetry]` und `userrequestedlocalauditdirectory = <host directory>/audit` im Hostverzeichnis:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```

1. Ausführen des containerimages

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Das Zielverzeichnis für die neue lokale Überwachungsprotokolle werden im Container. Erstellen Sie ein Zielverzeichnis für die neue lokale Überwachungsprotokolle, in die Hostverzeichnis auf Ihrem Computer. Das folgende Beispiel erstellt ein neues **/audit** Verzeichnis:

   ```bash
   sudo mkdir <host directory>/audit
   ```

1. Hinzufügen einer `mssql.conf` -Datei mit den Zeilen `[telemetry]` und `userrequestedlocalauditdirectory = <host directory>/audit` im Hostverzeichnis:
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```

1. Ausführen des containerimages

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server unter Linux finden Sie unter den [Übersicht über SQL Server unter Linux](sql-server-linux-overview.md).
