---
title: Installieren von Data Quality Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 486e4216-a946-4c6e-828c-61bc905f7ec1
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 728d69dcf44e0cab436c73396d833f754891a3f5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62792613"
---
# <a name="install-data-quality-services"></a>Installieren von Data Quality Services
  [!INCLUDE[ssDQSnoversionLong](../../includes/ssdqsnoversionlong-md.md)] (DQS) enthält die folgenden zwei Komponenten: **[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]** und **[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]**.  
  
|DQS-Komponente|Description|  
|-------------------|-----------------|  
|[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]|[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] wird auf der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Datenbank-Engine installiert und enthält drei Datenbanken: DQS_MAIN, DQS_PROJECTS und DQS_STAGING_DATA. DQS_MAIN enthält DQS-gespeicherte Prozeduren, die DQS-Engine und veröffentlichte Knowledge Bases. DQS_PROJECTS enthält die Datenqualitätsprojektinformationen. DQS_STAGING_DATA ist der Stagingbereich, in den Sie die Quelldaten zum Ausführen von DQS-Vorgängen kopieren können, um die verarbeiteten Daten anschließend zu exportieren.|  
|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] ist eine eigenständige Anwendung, die eine Verbindung mit [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]ermöglicht und eine hochgradig intuitive grafische Benutzeroberfläche bereitstellt, um Data Quality- und andere Verwaltungsaufgaben für DQS auszuführen.|  
  
> [!IMPORTANT]
>  Neben den beiden oben erwähnten DQS-Komponenten haben Sie folgende Möglichkeiten:  
> 
>  -   Verwenden Sie die DQS-Bereinigungstransformation in Integration Services, die die Datenbereinigung innerhalb des Integration Services-Verpackungsprozesses ausführt und automatisch mit Integration Services installiert wird. Informationen zum Installieren von Integration Services finden Sie unter [Installieren von Integration Services](../../integration-services/install-windows/install-integration-services.md).  
> -   Aktivieren Sie die DQS-Integration in Master Data Services, um die DQS-Abgleichfunktionalität im Master Data Services-Add-In für Excel zu verwenden. Weitere Informationen finden Sie unter [Aktivieren der Data Quality Services-Integration in Master Data Services](../../master-data-services/install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 Die DQS-Installation besteht aus drei Teilen:  
  
-   [Vor der Installation:](#PreInstallationTasks) Überprüfen Sie die Systemanforderungen, bevor Sie DQS installieren.  
  
-   [Data Quality Services-Installationstasks:](#DQSInstallation) Installieren Sie DQS mithilfe des SQL Server-Setups.  
  
-   [Nach der Installation:](#PostInstallationTasks) Führen Sie nach dem SQL Server-Setup diese Aktionen durch, um die Installation von DQS abzuschließen.  
  
> [!NOTE]  
>  Dieses Thema enthält keine Anweisungen zum Ausführen des Setups über die Befehlszeile. Informationen zu Befehlszeilenoptionen zum Installieren von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] und -Clients finden Sie unter [Funktionsparameter](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#Feature) in [Installieren von SQL Server 2014 über die Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
##  <a name="PreInstallationTasks"></a> Installationsvorbereitung  
 Stellen Sie vor dem Installieren von DQS sicher, dass der Computer die Mindestsystemanforderungen erfüllt. Die folgende Tabelle enthält Informationen zu den Mindestsystemanforderungen für die DQS-Komponenten:  
  
|DQS-Komponente|Mindestsystemanforderungen|  
|-------------------|---------------------------------|  
|[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]|Arbeitsspeicher (RAM):<br />-Minimum: 2 GB<br />-Empfohlen: 4 GB oder mehr<br /><br /> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Datenbank-Engine. Weitere Informationen finden Sie unter [über die SQL Server-Datenbank-Engine](../../database-engine/sql-server-database-engine-overview.md).|  
|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]|.NET Framework 4.0 (wird mit dem [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] installiert, sofern nicht bereits installiert)<br /><br /> Internet Explorer 6.0 SP1 oder höher|  
  
> [!IMPORTANT]
>  -   [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] und [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] können auf demselben Computer oder auf verschiedenen Computern installiert werden. Beide Komponenten können unabhängig voneinander und in beliebiger Reihenfolge installiert werden. Damit der [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]verwendet werden kann, muss jedoch ein [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installiert sein, mit dem eine Verbindung hergestellt wird.  
> -   Sie können eine Verbindung mit der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] unter Verwendung der aktuellen oder einer früheren Version von [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] und der DQS-Bereinigungstransformation herstellen. Informationen zum Aktualisieren der vorhandenen DQS-Version auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]finden Sie unter [Aktualisieren von Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md).  
> -   Obwohl Microsoft Excel keine erforderliche Komponente zum Installieren von Data Quality-Client ist, muss Microsoft Excel 2003 oder höher auf dem Data Quality-Clientcomputer installiert sein, damit verschiedene Vorgänge in der Clientanwendung wie das Importieren von Domänenwerten aus einer Excel-Datei oder das Zuordnen zu den Quelldaten in einer Excel-Datei für Wissensermittlungs-, Bereinigungs- oder Abgleichsaktivitäten durchgeführt werden können.  
  
 Ausführliche Informationen zu den mindestsystemanforderungen für die Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], finden Sie unter [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
##  <a name="DQSInstallation"></a> Data Quality Services Installationstasks  
 Zum Installieren der DQS-Komponenten müssen Sie das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Setup ausführen. Beim Ausführen des SQL Server-Setups müssen Sie mehrere Seiten des Installations-Assistenten durchgehen, um basierend auf Ihren Anforderungen die entsprechenden Optionen auszuwählen. In der folgenden Tabelle sind nur die Seiten des Installations-Assistenten mit den Optionen aufgeführt, die sich auf die Installation von DQS auswirken:  
  
|Page|Aktion|  
|----------|------------|  
|Funktionsauswahl|Wählen Sie Folgendes:<br /><br /> **Data Quality Services** unter **Database Engine Services** , um den [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]zu installieren. <br />Wenn Sie das Kontrollkästchen **Data Quality Services** aktivieren, kopiert SQL Server-Setup eine Installationsdatei, DQSInstaller.exe, im Verzeichnis der SQL Server-Instanz auf dem Computer. Sie müssen diese Datei nach dem Abschließen des SQL Server-Setups ausführen, um die Installation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] *abzuschließen*. Sie müssen außerdem einige zusätzliche Schritte zum Konfigurieren von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ausführen, bevor Sie ihn verwenden können. Weitere Informationen finden Sie unter [Installationsnachbereitung](#PostInstallationTasks).<br /><br /> **Data Quality-Client** zur Installation von [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].<br /><br /> (Empfohlen) **Verwaltungstools > Vollständig** unter **Verwaltungstools > Einfach** zur Installation von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Ihnen steht eine grafische Benutzeroberfläche zur Verwaltung der SQL Server-Instanz zur Verfügung, und Sie werden bei der Ausführung weiterer Tasks während der Installationsnachbereitung unterstützt. Diese werden im folgenden Abschnitt erläutert.|  
|Datenbank-Engine-Konfiguration|Klicken Sie auf **Aktuellen Benutzer hinzufügen** , um der festen Serverrolle sysadmin das Windows-Benutzerkonto hinzuzufügen. Dies ist erforderlich, damit Sie später die Datei DQSInstaller.exe ausführen können, um die Installation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] abzuschließen.|  
  
##  <a name="PostInstallationTasks"></a> Installationsnachbereitung  
 Nach dem Abschließen des SQL Server-Installations-Assistenten müssen Sie die in diesem Abschnitt erläuterten zusätzlichen Schritte ausführen, um die Installation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] abzuschließen, ihn zu konfigurieren und in Betrieb zu nehmen.  
  
|Aktion|Description|Verwandte Themen|  
|------------|-----------------|--------------------|  
|Abschließen der [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]-Installation|Führen Sie die Datei DQSInstaller.exe aus. Beim Ausführen der Datei DQSInstaller.exe geschieht Folgendes:<br /><br /> Die Datenbanken DQS_MAIN, DQS_PROJECTS und DQS_STAGING_DATA werden erstellt.<br /><br /> Die Anmeldenamen ##MS_dqs_db_owner_login## und ##MS_dqs_service_login## werden erstellt.<br /><br /> Die Rollen dqs_administrator, dqs_kb_editor und dqs_kb_operator werden in der DQS_MAIN-Datenbank erstellt.<br /><br /> Die gespeicherte DQInitDQS_MAIN-Prozedur wird in der master-Datenbank erstellt.<br /><br /> Die Datei DQS_install.log wird normalerweise in der c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL12 erstellt. *< Instance_name >* \MSSQL\Log-Ordner. Die Datei enthält Informationen zu den Aktionen, die beim Ausführen der Datei DQSInstaller.exe ablaufen.<br /><br /> Wenn eine Master Data Services-Datenbank in der gleichen SQL Server-Instanz wie [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]vorhanden ist, wird ein der Master Data Services-Anmeldung zugeordneter Benutzer erstellt und ihm die dqs_administrator-Rolle in der Datenbank DQS_MAIN erteilt.<br /><br /> <br /><br /> Damit ist die Installation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] abgeschlossen.|[Ausführen von DQSInstaller.exe zum Abschließen der Installation von Data Quality Server](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)|  
|Zuweisen von DQS-Rollen an Benutzer|Für die Anmeldung [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] mit [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)], ein Benutzer muss eine der folgenden drei Rollen in der Datenbank DQS_MAIN verfügen: **"dqs_administrator"**, **Rolle "dqs_kb_editor"**, oder **Dqs_kb_ Operator**. Wenn das Benutzerkonto ein Element der festen Serverrolle sysadmin ist, können Sie sich standardmäßig am [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] anmelden, der den [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] verwendet, auch wenn dem Benutzerkonto keine der DQS-Rollen gewährt wird. Weitere Informationen zu den drei DQS-Rollen finden Sie unter [DQS-Sicherheit](../dqs-security.md).<br /><br /> Hinweis: Die drei DQS-Rollen sind für die Datenbanken DQS_PROJECTS und DQS_STAGING_DATA nicht verfügbar.|[Zuweisen von DQS-Rollen an Benutzer](grant-dqs-roles-to-users.md)|  
|Bereitstellen von Daten für DQS-Vorgänge|Stellen Sie sicher, dass Sie auf die Quelldaten für die DQS-Vorgänge zugreifen können, und dass Sie die verarbeiteten Daten in eine Tabelle in einer Datenbank exportieren können.|[Zugriff auf Daten für DQS-Vorgänge](access-data-for-the-dqs-operations.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Video: Install and Configure DQS (Video: Installieren und Konfigurieren von DQS)](https://go.microsoft.com/fwlink/?LinkId=238241)   
 [Aktualisieren der SQLCLR-Assemblys nach dem Aktualisieren von .NET Framework](upgrade-sqlclr-assemblies-after-net-framework-update.md)   
 [Export und Importieren von DQS-Wissensdatenbanken mit DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md)   
 [Aktualisieren von Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md)   
 [Entfernen von Data Quality Server-Objekten](../../sql-server/install/remove-data-quality-server-objects.md)   
 [Installieren von SQL Server 2014-BI-Funktionen](../../sql-server/install/install-sql-server-business-intelligence-features.md)   
 [Deinstallieren von SQLServer 2014](../../sql-server/install/uninstall-sql-server.md)   
 [Data Quality Services](../data-quality-services.md)   
 [Behandeln von Installations- und Konfigurationsproblemen in DQS](https://social.technet.microsoft.com/wiki/contents/articles/3776.aspx)  
  
  
