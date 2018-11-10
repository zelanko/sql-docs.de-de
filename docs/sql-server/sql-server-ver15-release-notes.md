---
title: SQL Server 2019 Release Notes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/06/2018
ms.prod: sql-server-2018
ms.reviewer: ''
ms.technology:
- server-general
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 7fba2c4989b6e50fe720a44e127b044dea93876d
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269803"
---
# <a name="sql-server-2019-preview-release-notes"></a>Release Notes zu SQL Server 2019 (Vorschauversion)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel beschreibt Einschränkungen und bekannte Probleme bei der [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Community Technology Preview (CTP) Releases. Verwandte Informationen finden Sie unter:
- [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)

> [!NOTE]
> Vorschauversionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] werden zur Verfügung gestellt, damit Sie die Funktionen des kommenden Release kennenlernen können. Sie werde nicht für die Produktion unterstützt oder lizenziert. Die folgenden Szenarien werden ausdrücklich nicht unterstützt:
>
> - Parallelinstallationen mit anderen Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
> - Upgrades vorhandener SQL Server-Instanzen mit einer beliebigen Version

**Versuchen Sie Folgendes[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]:**
- [![Download aus dem Evaluation Center](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=862101) [Laden Sie [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] für die Installation unter Windows](http://go.microsoft.com/fwlink/?LinkID=862101) herunter.
- Installieren Sie die Version unter Linux für [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) und [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Führen Sie SQL Server 2019 unter Docker aus](../linux/quickstart-install-connect-docker.md).

## <a name="ctp-21-november-2018"></a>CTP 2.1 (November 2018)
[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 ist das neueste öffentliche Release von [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 steht nur als Evaluation Edition zur Verfügung. Es sind keine anderen Editionen verfügbar. Die Unterstützung für CTP 2.1 wird in license_Eval.rtf in den Installationsmedien beschrieben.

Eingeschränkte Unterstützung finden Sie möglicherweise an folgenden Stellen:

- Foren
  - [SQL Server Feedback](http://aka.ms/sqlfeedback)
  - [Erste Schritte mit SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted)
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [SQL Server Documentation (SQL Server-Dokumentation)](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- Oder tweeten Sie [@SQLServer](http://twitter.com/SQLServer) mit [#sqlhelp](https://twitter.com/search?q=%23sqlhelp)

### <a name="documentation-ctp-21"></a>Dokumentation (CTP 2.1)

- **Problem und Kundenbeeinträchtigung**: Die Dokumentation für SQL Server 2019 (15.x) ist eingeschränkt, und die Inhalte sind im [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]-Dokumentationssatz enthalten. Inhalte in Artikeln, die für SQL Server 2019 (15.x) spezifisch sind, sind mit **Gilt für** gekennzeichnet.

- **Problem und Kundenbeeinträchtigung**: [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dokumentation kann nach Version gefiltert werden. Verwenden Sie das Steuerelement oben links auf jeder Dokumentationsseite, um nach Ihren Anforderungen zu filtern. 

- **Problem und Kundenbeeinträchtigung**: Für SQL Server 2019 (15.x) sind keine Offlineinhalte verfügbar.

### <a name="hardware-and-software-requirements"></a>Hardware- und Softwareanforderungen

- **Problem und Kundenbeeinträchtigung**: Die Hard- und Softwareanforderungen werden derzeit noch geprüft und sind noch nicht final für die Produktfreigabe abgeschlossen.

  - **Hardware**
    - [Windows – Anforderungen an Prozessor, Arbeitsspeicher und Betriebssystem](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr)
    - [Linux – Systemanforderungen](../linux/sql-server-linux-setup.md#system)
  - **Software**
    - Windows Server 2016 oder höher. Informationen zu weiteren Anforderungen finden Sie unter [Anforderungen für die Installation von SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
    - Microsoft .NET Framework 4.6.2. Verfügbar im [Download Center](http://www.microsoft.com/download/details.aspx?id=53344).
    - Informationen zu Linux finden Sie unter [Linux – unterstützte Plattformen](../linux/sql-server-linux-setup.md#supportedplatforms)

### <a name="floating-point-results"></a>Gleitkommaergebnisse

- **Problem und Kundenbeeinträchtigung**: Die SQL Server 2019-Vorschauversion verwendet einen aktualisierten Compiler zum Erstellen von SQL Server-Instanzen. In einigen Fällen kann mit dem neuen Compiler kompilierter Code numerische Gleitkommawerte zurückgeben – im Unterschied zu früheren Versionen von SQL Server. Der Behavior Change beschränkt sich in einer künftigen CTP auf den neuen Kompatibilitätsgrad (150).

- **Problemumgehung**: Nicht verfügbar.

- **Gilt für**: SQL Server 2019 CTP 2.1.

### <a name="sql-server-integration-services-ssis-page-deployment-after-switching-db-to-single-user-mode-and-then-switching-back"></a>Seitenbereitstellung von SQL Server Integration Services (SSIS) nach Umstellen der Datenbank in den Einzelbenutzermodus und anschließendem Zurückwechseln

- **Problem und Kundenbeeinträchtigung**: Wenn SSIS vom Einzelbenutzermodus wieder in den Mehrbenutzermodus wechselt, wird beim Bereitstellen eines Pakets ggf. der folgende Fehler gemeldet:

  `Cannot continue the execution because the session is in the kill state.`

- **Problemumgehung**: Beenden Sie die SQL Server-Instanz, und starten Sie sie neu, und versetzen Sie SSIS-Datenbank wieder in den Mehrbenutzermodus. 

- **Gilt für**: SQL Server 2019-Vorschauversion CTP 2.1.


### <a name="udf-inlining"></a>Inlining benutzerdefinierter Funktionen 

- **Problem und Kundenbeeinträchtigung**: Es gibt Ausnahmefälle, in denen geschachtelte Aufrufe von benutzerdefinierten Inlinefunktionen die Sicherheit nicht ordnungsgemäß überprüfen.
  
- **Problemumgehung**: Deaktivieren Sie das Inlining benutzerdefinierter Funktionen für solche benutzerdefinierten Funktionen mit der Einstellung `INLINE = OFF`.

- **Gilt für**: SQL Server 2019 CTP 2.1.

### <a name="lightweight-query-profiling-infrastructure"></a>Profilerstellungsinfrastruktur für Lightweight-Abfragen

- **Problem und Kundenbeeinträchtigung**: Beim Ausführen des Befehls `ALTER DATABASE SCOPED CONFIGURATION SET LIGHTWEIGHT_QUERY_PROFILING = ON` wird ein Syntaxfehler zurückgegeben. Bei allen Szenarien, die von der Ausführung dieses Befehls abhängig sind, tritt ein Fehler auf.

  > [!NOTE]
  > Derzeit kann die Profilerstellungsinfrastruktur für Lightweight-Abfragen (LWP) nicht auf der Ebene der einzelnen Datenbanken gesteuert werden und bleibt standardmäßig für alle Datenbanken aktiviert. Weitere Informationen zu LWP finden Sie unter [Neuigkeiten zu SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

- **Problemumgehung:** Dieses Problem kann nicht für [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTPs behoben werden.

- **Gilt für**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 und CTP 2.0.

### <a name="utf-8-collations"></a>UTF-8-Sortierungen

- **Problem und Kundenbeeinträchtigung**: UTF-8-fähige Sortierungen können nicht mit einigen anderen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Features verwendet werden. UTF-8 wird nicht unterstützt, wenn die folgenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Features verwendet werden:

  - SQL Server-Replikation
  - Verbindungsserver
  - In-Memory-OLTP
  - Externe Tabelle für PolyBase

    Beachten Sie auch, dass es derzeit keine Benutzeroberflächenunterstützung gibt, um UTF-8-fähige Sortierungen in Azure Data Studio oder SSDT auszuwählen. Die neueste SSMS-Version unterstützt die Auswahl von UTF-8-fähigen Sortierungen in der Benutzeroberfläche.

- **Problemumgehung:** Dieses Problem kann nicht für [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTPs behoben werden.

- **Gilt für**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 und CTP 2.0.

### <a name="sql-graph"></a>SQL Graph

- **Problem und Kundenbeeinträchtigung**: Tools, die von DacFx abhängig sind, z.B. Import-Export, funktionieren nicht für die neuen Graphfeatures Edgeeinschränkungen und „Merge DML“. Die Skripterstellung in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] funktioniert möglicherweise nicht.

- **Problemumgehung**: Das Schreiben von [!INCLUDE[tsql](../includes/tsql-md.md)]-Skripts und die Ausführung für den Server mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder SQLCMD funktioniert. Das Exportieren oder Importieren von Datenbankobjekten, die Edgeeinschränkungen erstellen, die neue „Merge DML“-Syntax verwenden oder abgeleitete Tabellen/Ansichten auf Graphobjekten erstellen, funktioniert nicht. Benutzer müssen solche Objekte manuell in ihrer Datenbank mit Hilfe von [!INCLUDE[tsql](../includes/tsql-md.md)]-Skripten erstellen. 

- **Gilt für**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 und CTP 2.0.

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted mit Secure Enclaves

- **Problem und Kundenbeeinträchtigung**: Für umfangreiche Berechnungen stehen noch einige Leistungsoptimierungen aus. Zudem weisen solche Berechnungen eine eingeschränkte Funktionalität auf (z.B. keine Indizierung) und sind derzeit standardmäßig deaktiviert.

- **Problemumgehung**: Zum Aktiveren von umfangreichen Berechnungen führen Sie `DBCC traceon(127,-1)` aus. Weitere Informationen finden Sie unter [Aktivieren umfangreicher Berechnungen](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **Gilt für**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 und CTP 2.0.

### <a name="sql-server-integration-service---fuzzy-lookup-transformation"></a>SQL Server Integration Services – Transformation für Fuzzysuche

- **Problem und Kundenbeeinträchtigung**: Die Transformation für die Fuzzysuche würde fehlschlagen und den folgenden Fehler auslösen, wenn das Wiederverwenden des Index eingerichtet ist:

  `The specified delimiters do not match the delimiters used to build the pre-existing match index "...". This error occurs when the delimiters used to tokenize fields do not match. This can have unknown effects on the matching behavior or results.`

- **Problemumgehung**: Nicht verfügbar.

- **Weitere Informationen**: Nicht verfügbar.  

- **Gilt für**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1.

## <a name="ctp-20-september-2018"></a>CTP 2.0 (September 2018)

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.0 ist die erste öffentliche Version von [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

### <a name="sql-server-integration-services-ssis-transfer-database-task"></a>SQL Server Integration Services (SSIS) – Datenbanken übertragen

- **Problem und Kundenbeeinträchtigung**: Wenn zum Übertragen einer Datenbank im `Database Online`-Modus eine `Transfer Database Task` konfiguriert ist, tritt bei diesem Vorgang der folgende Fehler auf:

  >Die Execute-Methode der Aufgabe gab den Fehlercode 0x80131500 zurück (Bei der Datenübertragung ist ein Fehler aufgetreten. Weitere Informationen finden Sie in der inneren Ausnahme.). Die Execute-Methode muss erfolgreich sein und das Ergebnis mithilfe eines Ausgabeparameters anzeigen.

- **Problemumgehung**: Führen Sie `DBCC TRACEON (7416,-1)` auf dem Server aus, und versuchen Sie es erneut.

- **Gilt für**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.0.

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
