---
title: SQLServer unter Linux – häufig gestellte Fragen | Microsoft-Dokumentation
description: Dieser Artikel enthält Antworten auf häufig gestellte Fragen zu SQL Server unter Linux ausgeführt wird.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/22/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: b0df550ee3489ba8c37ded47878096d75909343e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38001792"
---
# <a name="sql-server-on-linux-frequently-asked-questions-faq"></a>SQLServer unter Linux: häufig gestellte Fragen (FAQ)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Die folgenden Abschnitte enthalten allgemeine Fragen und Antworten für SQL Server unter Linux ausgeführt wird.

## <a name="general-questions"></a>Allgemeine Fragen

1. **Welche Linux-Plattformen werden unterstützt?**

   SQL Server wird derzeit auf Ubuntu, SUSE Linux Enterprise Server und Red Hat Enterprise Server unterstützt. Es unterstützt auch die in einem Container mit Docker ausführen. Aktuelle Informationen zu den unterstützten Versionen finden Sie unter [unterstützte Plattformen](sql-server-linux-setup.md#supportedplatforms).

1. **SQL Server unter Linux funktioniert auf anderen Plattformen**?

   SQL Server wird getestet und für die zuvor aufgeführten Distributionen unter Linux unterstützt. Andere Linux-Distributionen sind eng miteinander verknüpft und möglicherweise zum Ausführen von SQL Server (z. B. CentOS ist eng verwandt mit Red Hat Enterprise Server). Aber wenn Sie SQL Server auf einem nicht unterstützten Betriebssystem installieren möchten, lesen Sie bitte die **Supportrichtlinie** im Abschnitt der [technischer Support-Richtlinie für Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server) zu verstehen, die Unterstützung Auswirkungen auf. Beachten Sie außerdem, dass einige Community, dass die Linux-Distributionen keine formale können Support zu erhalten verwaltet, wenn das zugrunde liegende Betriebssystem, das Problem ist.

1. **Welche SQL Server-Funktionen unter Linux unterstützt werden?**

   Eine vollständige Liste der unterstützten Features und bekannten Problemen, finden Sie unter den [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md).

1. **Was ist die Unterstützungsrichtlinie für SQL Server?**

   Um die Support-Richtlinie zu verstehen, lesen Sie die [technische Support-Richtlinie für SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

1. **Ich bin aus dem Windows SQL Server-Umfeld stammen. Gibt es Ressourcen, um zu erfahren, wie Sie SQL Server unter Linux verwenden?**

   Die [Schnellstarts](sql-server-linux-setup.md#platforms) enthalten schrittweise Anleitungen zum Installieren von SQL Server unter Linux und Ausführen von Transact-SQL-Abfragen. Andere Tutorials enthalten zusätzliche Anleitungen zur Verwendung von SQL Server unter Linux. Eine Liste der Drittanbieter-Tipps, finden Sie unter den [MSSQLTIPS Liste von SQL Server unter Linux Tipps](https://www.mssqltips.com/sql-server-tip-category/226/sql-server-on-linux/).

## <a name="installation"></a>Installation

1. **Wie erhalte ich SQL Server auf Meine Linux-Server installiert?**

   Microsoft behält Package-Repositorys für die Installation von SQL Server und unterstützt die Installation über natives Paket-Managern, z. B. Yum, Zypper, und apt. Um schnell zu installieren, finden Sie in der [Schnellstarts](sql-server-linux-setup.md#platforms).

1. **Kann ich SQL Server auf dem Linux-Subsystem für Windows 10 installieren?**

   Nein. Linux unter Windows 10 ist derzeit nicht unterstützte Plattform für SQL Server und verwandte Tools.

1. **Welche Linux-Dateisysteme kann SQL Server 2017 für Datendateien verwenden?**

   SQL Server unter Linux unterstützt derzeit ext4- und XFS. Unterstützung für andere Dateisysteme werden in der Zukunft und Bedarf hinzugefügt werden.

1. **Kann ich die Installationspakete aus, um SQL Server offline-Installation herunterladen?**

   Ja. Weitere Informationen finden Sie in das Paket herunterladen Hyperlinks in den [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md). Lesen Sie auch die [Anweisungen für Offlineinstallationen](sql-server-linux-setup.md#offline).

1. **Kann ich eine unbeaufsichtigte Installation von SQL Server unter Linux durchführen?**

   Ja. Eine Erläuterung der für die unbeaufsichtigte Installation, finden Sie unter [zur Installation von SQL Server unter Linux](sql-server-linux-setup.md#unattended). Finden Sie die Beispielskripts für [Red Hat](sample-unattended-install-redhat.md), [SUSE Linux Enterprise Server](sample-unattended-install-suse.md), und [Ubuntu](sample-unattended-install-ubuntu.md). Sie können auch überprüfen [dieses Beispielskript](https://blogs.msdn.microsoft.com/sqlcat/2017/10/03/unattended-install-and-configuration-for-sql-server-2017-on-linux/) von SQL Server Customer Advisory Teams erstellt.

## <a name="tools"></a>Tools

1. **Kann ich die SQL Server Management Studio-Client für Windows verwenden den Zugriff auf SQL Server unter Linux?**

   Ja, können Sie alle Ihre vorhandenen Tools, die in Windows den Zugriff auf SQL Server unter Linux ausgeführt. Dazu gehören Tools von Microsoft, z. B. SQL Server Management Studio (SSMS), SQL Server Data Tools (SSDT), und OSS und Drittanbieter-Tools.

1. **Gibt es ein Tool wie SSMS zurück, die unter Linux ausgeführt wird?**

   Die neue Microsoft SQL Operations Studio (preview) ist eine plattformübergreifende-Tool zum Verwalten von SQL Server. Weitere Informationen finden Sie unter [neuerungen von Microsoft SQL Operations Studio (Vorschau)](../sql-operations-studio/what-is.md).

1. **Sind Sie Befehle wie Sqlcmd und Bcp unter Linux verfügbar?**

   Ja, [Sqlcmd und Bcp](sql-server-linux-setup-tools.md) nativ unter Linux, MacOS und Windows verfügbar sind. Darüber hinaus verwenden Sie die neue [Mssql-Skripter](https://github.com/Microsoft/mssql-scripter) Befehlszeilentool unter Linux, MacOS oder Windows zum Generieren von T-SQL-Skripts für Ihre SQL-Datenbank, die überall ausgeführt. Sehen Sie sich auch für die Vorschauversion [Mssql-Cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/).

1. **Ist es möglich, zeigen Sie den Aktivitätsmonitor, wenn für eine Instanz über SSMS auf Windows verbunden unter Linux werden ausgeführt?**

   Ja, Sie können SSMS unter Windows eine Remoteverbindung herstellen, und verwenden Extras / features wie als Aktivitätsmonitor-Befehle auf einer Linux-Instanz.

1. **Welche Tools stehen zur Überwachung der Leistung von SQL Server unter Linux zur Verfügung?**

   Sie können [dynamische Verwaltungssichten (DMVs) für System](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) zum Sammeln von verschiedenen Arten von Informationen über SQL Server, einschließlich der Informationen für Linux-Prozesses. Sie können [Query Store](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md) abfrageleistung zu verbessern. Andere Tools, z. B. der integrierte [Leistungsdashboard](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/)Remote in SQL Server Management Studio (SSMS) von Windows funktionieren.

## <a name="administration"></a>Verwaltung

1. **Hat Microsoft eine wie die SQL Server-Konfigurations-Manager-app unter Linux erstellt?**

   Ja, es gibt ein-Konfigurationstool für SQL Server unter Linux: [Mssql-Conf](sql-server-linux-configure-mssql-conf.md).

1. **Unterstützt SQL Server unter Linux mehrere Instanzen auf demselben Host?**

   Es wird empfohlen, mehrere Container auf einem Host für mehrere unterschiedliche Instanzen ausgeführt. Jeder Container muss zu einem anderen Port lauschen. Weitere Informationen finden Sie unter [führen mehrere SQL Server-Container](sql-server-linux-configure-docker.md#run-multiple-sql-server-containers).

1. **Werden Active Directory-Authentifizierung wird unter Linux unterstützt?**

   Ja. Weitere Informationen finden Sie unter [Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md).

1. **Befinden sich immer auf, und unterstützt clustering unter Linux?**

   Failoverclustering und hohe Verfügbarkeit unter Linux werden mit Pacemaker unter Linux erreicht. Weitere Informationen finden Sie unter [Business Continuity und datenbankwiederherstellung – SQL Server unter Linux](sql-server-linux-business-continuity-dr.md).

1. **Ist es möglich, zum Konfigurieren der Replikation von Linux, Windows und umgekehrt?**

   Schreibgeschützte Replikate können für die unidirektionale Datenreplikation zwischen Windows und Linux verwendet werden.

1. **Ist es möglich, vorhandene Datenbanken in früheren Versionen von SQL Server von Windows zu Linux migrieren?**

   Ja, es gibt [mehrere Methoden](sql-server-linux-migrate-overview.md) dies zu erreichen.

1. **Kann ich meine Daten von Oracle und andere Datenbank-Engines zu SQL Server unter Linux migrieren?**

   Ja. SSMA unterstützt die Migration von mehrere Typen von Datenbank-Engines: Microsoft Access, DB2, MySQL, Oracle und SAP ASE (früher SAP Sybase ASE). Ein Beispiel zur Verwendung von SSMA finden Sie unter [migrieren ein Oracle-Schemas nach SQL Server 2017 unter Linux mit dem SQL Server-Migrationsassistenten](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json).

1. **Welche Berechtigungen für SQL Server-Dateien erforderlich sind?**

   Alle Dateien in die `/var/opt/mssql` Dateiordner sollten im Besitz der **Mssql** Benutzer und gehören zu den **Mssql** Gruppe. Sowohl die **Mssql** Benutzer- und Lese-/ Schreibberechtigungen für alle Dateien und Verzeichnissen verfügen. Beachten Sie die folgenden speziellen Szenarien im Zusammenhang mit Datei- und Verzeichnisberechtigungen:

   * Berechtigungen für die Mssql-Besitzer und die Gruppe müssen für bereitgestellte Netzwerkfreigaben, die zum Speichern von SQL Server-Dateien verwendet werden.
   * Wenn Sie Datenbankdateien oder die Sicherungen in einem nicht standardmäßigen-Verzeichnis gefunden werden, müssen Sie auch Berechtigungen für dieses Verzeichnis festlegen.
   * Wenn Sie die standardmäßigen Stamm "umask" 0022 ändern, schlägt der SQL Server-Konfiguration nach der Installation fehl. Sie müssen anschließend manuell erforderliche Berechtigungen auf SQL Server-Startkonto anwenden.

1. **Kann ich den Besitz von SQL Server-Dateien und Verzeichnissen aus dem installierten Mssql-Konto und die Gruppe ändern?**

   Wir unterstützen keine, ändern den Besitz des SQL Server-Verzeichnis und die Dateien aus der Standardinstallation. Die Mssql-Konto und die Gruppe ist speziell für SQL Server verwendet, und hat keinen Zugriff für die interaktive Anmeldung.

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
