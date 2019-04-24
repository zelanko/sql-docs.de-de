---
title: SQL Server 2019 Release Notes | Microsoft-Dokumentation
ms.date: 03/27/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 3362a03fe1437b15985fdc557fac6536db5fd2f7
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582874"
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
- [![Download aus dem Evaluation Center](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=862101) [Laden Sie [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] für die Installation unter Windows](https://go.microsoft.com/fwlink/?LinkID=862101) herunter.
- Installieren Sie die Version unter Linux für [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) und [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Führen Sie SQL Server 2019 unter Docker aus](../linux/quickstart-install-connect-docker.md).

## <a name="ctp-24"></a>CTP 2.4
[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4 ist das neueste öffentliche Release von [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4 steht nur als Evaluation Edition zur Verfügung. Es sind keine anderen Editionen verfügbar. Die Unterstützung für CTP-Releases wird in den Installationsmedien in `license_Eval.rtf` beschrieben.

Eingeschränkte Unterstützung finden Sie möglicherweise an folgenden Stellen:

- Foren
  - [SQL Server Feedback](https://aka.ms/sqlfeedback)
  - [Erste Schritte mit SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted)
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [SQL Server Documentation (SQL Server-Dokumentation)](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- Oder tweeten Sie [@SQLServer](https://twitter.com/SQLServer) mit [#sqlhelp](https://twitter.com/search?q=%23sqlhelp)

### <a name="documentation-ctp-24"></a>Dokumentation (CTP 2.4)

- **Problem und Kundenbeeinträchtigung:** Die Dokumentation für SQL Server 2019 (15.x) ist eingeschränkt, und die Inhalte sind im [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]-Dokumentationssatz enthalten. Inhalte in Artikeln, die für SQL Server 2019 (15.x) spezifisch sind, sind mit **Gilt für** gekennzeichnet.

- **Problem und Kundenbeeinträchtigung**: [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dokumentation kann nach Version gefiltert werden. Verwenden Sie das Steuerelement oben links auf jeder Dokumentationsseite, um nach Ihren Anforderungen zu filtern.

- **Problem und Kundenbeeinträchtigung:** Für SQL Server 2019 (15.x) sind keine Offlineinhalte verfügbar.

### <a name="hardware-and-software-requirements-ctp-24"></a>Hardware- und Softwareanforderungen (CTP 2.4)

- **Problem und Kundenbeeinträchtigung:** Die Hard- und Softwareanforderungen werden derzeit noch geprüft und sind noch nicht final für die Produktfreigabe abgeschlossen.

  - **Hardware**
    - [Windows – Anforderungen an Prozessor, Arbeitsspeicher und Betriebssystem](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr)
    - [Linux – Systemanforderungen](../linux/sql-server-linux-setup.md#system)
  - **Software**
    - Windows Server 2016 oder höher. Informationen zu weiteren Anforderungen finden Sie unter [Anforderungen für die Installation von SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
    - Microsoft .NET Framework 4.6.2. Verfügbar im [Download Center](https://www.microsoft.com/download/details.aspx?id=53344).
    - Informationen zu Linux finden Sie unter [Linux – unterstützte Plattformen](../linux/sql-server-linux-setup.md#supportedplatforms)

### <a name="updated-compiler"></a>Aktualisierter Compiler

- **Problem und Kundenbeeinträchtigung:** [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] beinhaltet nun einen aktualisierten Compiler. Bei CTP 2.1 gab es das bekannte Problem, dass die Ergebnisse für eine Gleitkommazahl oder andere Konvertierungsszenarios aufgrund des aktualisierten Compilers möglicherweise einen anderen Wert zurückgegeben haben als in früheren Versionen. In CTP 2.2 wird nun dafür gesorgt, dass die betroffenen Szenarios dieselben Ergebnisse zurückgeben wie frühere Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Ab CTP 2.3 sind keine bestehenden Probleme bekannt. Bitte melden Sie alle Anomalien bei Ergebnissen im Vergleich zu [!INCLUDE[ss2017](../includes/sssqlv14-md.md)] sofort an das [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Team](http://aka.ms/sqlfeedback).

- **Problemumgehung**: –

- **Gilt für**: SQL Server 2019 CTP 2.4, CTP 2.3, CTP 2.2, CTP 2.1

### <a name="utf-8-collations"></a>UTF-8-Sortierungen

- **Problem und Kundenbeeinträchtigung:** UTF-8-fähige Sortierungen können nicht mit einigen anderen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Features verwendet werden. UTF-8 wird nicht unterstützt, wenn die folgenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Features verwendet werden:

  - Verbindungsserver
  - In-Memory-OLTP
  - Externe Tabelle für PolyBase
  - Always Encrypted

  > [!Note]
  > Derzeit gibt es keine Benutzeroberflächenunterstützung, um UTF-8-fähige Sortierungen in Azure Data Studio oder SQL Server Data Tools (SSDT) auszuwählen. Die neueste [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]-Version (SSMS) unterstützt die Auswahl von UTF-8-fähigen Sortierungen in der Benutzeroberfläche.
 
- **Problemumgehung**: Dieses Problem kann für [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTPs nicht behoben werden.

- **Gilt für**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4, CTP 2.3, CTP 2.2, CTP 2.1, CTP 2.0.

### <a name="sql-graph"></a>SQL Graph

- **Problem und Kundenbeeinträchtigung:** Tools, die von DacFx abhängig sind, z.B. Import-Export, funktionieren nicht für die neuen Graphfeatures, Edgeeinschränkungen und „Merge DML“. Die Skripterstellung in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] funktioniert möglicherweise nicht.

- **Problemumgehung**: Das Schreiben von [!INCLUDE[tsql](../includes/tsql-md.md)]-Skripts und die Ausführung für den Server mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder SQLCMD funktioniert. Das Exportieren oder Importieren von Datenbankobjekten, die Edgeeinschränkungen erstellen, die neue „Merge DML“-Syntax verwenden oder abgeleitete Tabellen/Ansichten auf Graphobjekten erstellen, funktioniert nicht. Benutzer müssen solche Objekte manuell in ihrer Datenbank mit Hilfe von [!INCLUDE[tsql](../includes/tsql-md.md)]-Skripten erstellen. 

- **Gilt für**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4, CTP 2.3, CTP 2.2, CTP 2.1, 2.0.

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted mit Secure Enclaves

- **Problem und Kundenbeeinträchtigung:** Für umfangreiche Berechnungen stehen noch einige Leistungsoptimierungen aus. Zudem weisen solche Berechnungen eine eingeschränkte Funktionalität auf (z. B. keine Indizierung) und sind derzeit standardmäßig deaktiviert.

- **Problemumgehung**: Zum Aktiveren von umfangreichen Berechnungen führen Sie `DBCC traceon(127,-1)` aus. Weitere Informationen finden Sie unter [Aktivieren umfangreicher Berechnungen](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **Gilt für**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4, CTP 2.3, 2.2, CTP 2.1, 2.0.

### <a name="system-dynamic-management-views"></a>Dynamische Systemverwaltungssichten

- **Problem und Kundenbeeinträchtigung:** Die Systemtabellenwertfunktion [sys.dm_db_objects_disabled_on_compatibility_level_change](../relational-databases/system-dynamic-management-views/spatial-data-sys-dm-db-objects-disabled-on-compatibility-level-change.md) gibt zufällige Werte in der Spalte `dependency` zurück.

- **Gilt für**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4, CTP 2.3.

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
