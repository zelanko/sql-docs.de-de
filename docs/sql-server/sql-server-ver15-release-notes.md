---
title: SQL Server 2019 Release Notes | Microsoft-Dokumentation
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 40040948b56190a3ce94d9484e09a3386548bd31
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028857"
---
# <a name="sql-server-2019-preview-release-notes"></a>Release Notes zu SQL Server 2019 (Vorschauversion)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel beschreibt Einschränkungen und bekannte Probleme bei der [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Community Technology Preview (CTP) Releases. Verwandte Informationen finden Sie unter:
- [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)

## <a name="ctp-32"></a>CTP 3.2

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2 ist das neueste öffentliche Release von [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2 steht nur als Evaluation Edition zur Verfügung. Es sind keine anderen Editionen verfügbar.

Ausführliche Informationen zu Support und Lizenzen für CTP-Releases sind in `license_Eval.rtf` in den Installationsmedien enthalten.

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

## <a name="documentation"></a>Dokumentation

- **Problem und Kundenbeeinträchtigung:** Die Dokumentation für SQL Server 2019 (15.x) ist eingeschränkt, und die Inhalte sind im [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]-Dokumentationssatz enthalten. Inhalte in Artikeln, die für SQL Server 2019 (15.x) spezifisch sind, sind mit **Gilt für** gekennzeichnet.

- **Problem und Kundenbeeinträchtigung**: [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dokumentation kann nach Version gefiltert werden. Verwenden Sie das Steuerelement oben links auf jeder Dokumentationsseite, um nach Ihren Anforderungen zu filtern.

- **Problem und Kundenbeeinträchtigung:** Für SQL Server 2019 (15.x) sind keine Offlineinhalte verfügbar.

## <a name="hardware-and-software-requirements"></a>Hardware- und Softwareanforderungen

- **Problem und Kundenbeeinträchtigung:** Die Hard- und Softwareanforderungen werden derzeit noch geprüft und sind noch nicht final für die Produktfreigabe abgeschlossen.

  - **Hardware**
    - [Windows – Anforderungen an Prozessor, Arbeitsspeicher und Betriebssystem](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr)
    - [Linux – Systemanforderungen](../linux/sql-server-linux-setup.md#system)
  - **Software**
    - Windows Server 2016 oder höher. Informationen zu weiteren Anforderungen finden Sie unter [Anforderungen für die Installation von SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
    - Microsoft .NET Framework 4.6.2. Verfügbar im [Download Center](https://www.microsoft.com/download/details.aspx?id=53344).
    - Informationen zu Linux finden Sie unter [Linux – unterstützte Plattformen](../linux/sql-server-linux-setup.md#supportedplatforms)

## <a name = "release-notes"></a>Vom Support ausgeschlossene Features

- **Problem und Kundenbeeinträchtigung**: Bei der [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] ist der Support für die folgenden Komponenten, Features und Szenarien ausgeschlossen:
  - SQL Server Analysis Services
  - SQL Server Reporting Services
  - Always On-Verfügbarkeitsgruppen in Kubernetes
  - Verbesserte Wiederherstellung von Datenbanken

- **Problemumgehung**: Keine. Der Ausschluss gilt für alle Kunden, einschließlich Teilnehmer des SQL Early Adopter Program.

- **Gilt für**: Alle CTP-Releases

## <a name="updated-compiler"></a>Aktualisierter Compiler

- **Problem und Kundenbeeinträchtigung:** [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] beinhaltet nun einen aktualisierten Compiler. Bei CTP 2.1 gab es das bekannte Problem, dass die Ergebnisse für eine Gleitkommazahl oder andere Konvertierungsszenarios aufgrund des aktualisierten Compilers möglicherweise einen anderen Wert zurückgegeben haben als in früheren Versionen. In CTP 2.2 wird nun dafür gesorgt, dass die betroffenen Szenarios dieselben Ergebnisse zurückgeben wie frühere Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Ab CTP 3.2 sind keine bestehenden Probleme bekannt. Bitte melden Sie alle Anomalien bei Ergebnissen im Vergleich zu [!INCLUDE[ss2017](../includes/sssqlv14-md.md)] sofort an das [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Team](https://aka.ms/sqlfeedback).

- **Problemumgehung**: –

- **Gilt für**: Alle CTP-Releases

## <a name="installation-wizard-may-wait-between-eula-pages"></a>Der Installations-Assistent pausiert möglicherweise zwischen den Seiten mit Lizenzbedingungen

- **Problem und Kundenbeeinträchtigung:** Während der Installation mit dem Installations-Assistenten pausiert der Prozess möglicherweise für lange Zeit zwischen den Lizenzbedingungen für R Services und den Lizenzbedingungen für Python.

- **Problemumgehung**: Warten Sie, bis der Installations-Assistent fortfährt. Die Wartezeit kann länger als 30 Minuten sein.

- **Gilt für**: SQL Server 2019 CTP 3.0

## <a name="utf-8-collations"></a>UTF-8-Sortierungen

- **Problem und Kundenbeeinträchtigung:** UTF-8-fähige Sortierungen können nicht mit einigen anderen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Features verwendet werden. UTF-8 wird nicht unterstützt, wenn die folgenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Features verwendet werden:

  - In-Memory-OLTP
  - Externe Tabelle für PolyBase
  - Always Encrypted

  > [!Note]
  > Derzeit gibt es keine Benutzeroberflächenunterstützung, um UTF-8-fähige Sortierungen in Azure Data Studio oder SQL Server Data Tools (SSDT) auszuwählen. Die neueste [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]-Version (SSMS) 18 unterstützt die Auswahl von UTF-8-fähigen Sortierungen auf der Benutzeroberfläche.
 
- **Problemumgehung**: Dieses Problem kann für die [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTPs nicht behoben werden.

- **Gilt für**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2, CTP 3.1, CTP 3.0, CTP 2.5, CTP 2.4, CTP 2.3, CTP 2.2, CTP 2.1, CTP 2.0.

## <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted mit Secure Enclaves

- **Problem und Kundenbeeinträchtigung:** Für umfangreiche Berechnungen stehen Leistungsoptimierungen und Verbesserungen für die Fehlerbehandlung aus. Zudem sind diese Berechnungen derzeit standardmäßig deaktiviert.

- **Problemumgehung**: Zum Aktiveren von umfangreichen Berechnungen führen Sie `DBCC traceon(127,-1)` aus. Weitere Informationen finden Sie unter [Konfigurieren von Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **Gilt für**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2, CTP 3.1

## <a name="sql-server-configuration-manager-may-not-start"></a>Der SQL Server-Konfigurations-Manager kann möglicherweise nicht gestartet werden.

- **Problem und Kundenbeeinträchtigung:** Der SQL Server-Konfigurations-Manager startet möglicherweise nicht auf einem Computer, wenn die Datei „VCRUNTIME140.dll“ nicht vorhanden ist. Beim Starten des SQL Server-Konfigurations-Managers wird dem Benutzer u. U. folgendes Dialogfeld angezeigt: 

  `
  MMC could not create the snap-in. The snap-in might not have been installed correctly.
  `

- **Problemumgehung**:  Installieren Sie die neueste Version der Visual C++ 2013-Runtime (x86):

  - [Ausführlich](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)
  - [Direkt](https://support.microsoft.com/en-us/help/4032938/update-for-visual-c-2013-redistributable-package)

- **Gilt für**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.1, CTP 3.0, CTP 2.5

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
