---
title: Berichtsserver-Datenbank (nativer SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- databases [Reporting Services]
- report servers [Reporting Services], databases
- temporary databases [Reporting Services]
- report server database
- reportservertempdb
- reportserver database
ms.assetid: 0fc5c033-3fe1-4cea-86c7-66ea5e424d65
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b1ee55e0ec602ee2723b9e31b5dc80c611071b8e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48073880"
---
# <a name="report-server-database-ssrs-native-mode"></a>Berichtsserver-Datenbank (nativer SSRS-Modus)
  Ein Berichtsserver ist ein zustandsloser Server, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-[!INCLUDE[ssDE](../../includes/ssde-md.md)] zum Speichern von Metadaten und Objektdefinitionen verwendet. Eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation im nativen Modus verwendet zwei Datenbanken, um den persistenten Datenspeicher von temporären Speicheranforderungen zu trennen. Die Datenbanken werden gemeinsam erstellt und sind durch ihre Namen aneinander gebunden. Die Namen der Datenbanken lauten standardmäßig **reportserver** bzw. **reportservertempdb**.  
  
 Bei einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation im SharePoint-Modus wird zusätzlich eine Datenbank für die Datenwarnfunktion erstellt. Die drei Datenbanken im SharePoint-Modus sind [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienstanwendungen zugeordnet. Weitere Informationen finden Sie unter [Verwalten einer Reporting Services-SharePoint-Dienstanwendung](../manage-a-reporting-services-sharepoint-service-application.md)  
  
 Die Datenbanken können in einer lokalen oder einer Remoteinstanz der [!INCLUDE[ssDE](../../includes/ssde-md.md)] ausgeführt werden. Die Auswahl einer lokalen Instanz ist sinnvoll, wenn Sie über genügend Systemressourcen verfügen oder Softwarelizenzen einsparen möchten. Allerdings kann durch Ausführen der Datenbanken auf einem Remotecomputer die Leistung verbessert werden.  
  
 Sie können eine bereits vorhandene Berichtsserver-Datenbank aus einer früheren Installation oder einer anderen Instanz mit einer anderen Berichtsserverinstanz portieren oder wiederverwenden. Das Schema der Berichtsserver-Datenbank muss mit der Berichtsserverinstanz kompatibel sein. Falls die Datenbank in einem älteren Format vorliegt, werden Sie zum Aktualisieren auf das aktuelle Format aufgefordert. Ein Downgrade einer neueren auf eine ältere Version ist nicht möglich. Zudem können Sie, falls Sie mit einer neueren Berichtsserver-Datenbank arbeiten, diese nicht mit einer früheren Version einer Berichtsserverinstanz verwenden. Weitere Informationen zum Aktualisieren der Berichtsserver-Datenbanken auf neuere Formate finden Sie unter [Aktualisieren der Berichtsserver-Datenbank](../install-windows/upgrade-a-report-server-database.md).  
  
> [!IMPORTANT]  
>  Die Tabellenstruktur für die Datenbanken ist speziell für Servervorgänge vorgesehen und darf nicht geändert oder optimiert werden. Sie kann von [!INCLUDE[msCoName](../../includes/msconame-md.md)] von einer Version zur nächsten geändert werden. Wenn Sie die Datenbank selbst ändern oder erweitern, ist die Ausführung künftiger Upgrades oder die Anwendung von Service Packs nicht mehr oder nur noch teilweise möglich. Auch können durch Ihre Änderungen Berichtsservervorgänge beeinträchtigt werden. Wenn Sie z.B. in der ReportServer-Datenbank READ_COMMITTED_SNAPSHOT aktivieren, machen Sie die interaktive Sortierfunktion unbrauchbar.  
  
 Alle Zugriffe auf eine Berichtsserver-Datenbank müssen durch den Berichtsserver abgewickelt werden. Für den Zugriff auf Inhalte in einer Berichtsserver-Datenbank können Sie Berichtsserver-Verwaltungstools, wie z.B. den Berichts-Manager oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], oder befehlsorientierte Benutzerschnittstellen verwenden, wie z.B. einen URL-Zugriff, den Berichtsserver-Webdienst oder den WMI-Anbieter (Windows Management Instrumentation, Windows-Verwaltungsinstrumentation).  
  
 Die Verbindung mit der Berichtsserver-Datenbank wird normalerweise über den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager definiert. Die Verbindung kann jedoch auch während des Setupvorgangs definiert werden, sofern Sie die Standardkonfiguration installieren. Weitere Informationen zur Berichtsserververbindung mit der Datenbank finden Sie unter [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
## <a name="report-server-database"></a>Berichtsserver-Datenbank  
 Die Berichtsserver-Datenbank ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank, in der folgende Inhalte gespeichert werden:  
  
-   Von einem Berichtsserver verwalteten Elemente (.. / Berichte und verknüpfte Berichte, freigegebene Datenquellen, Berichtsmodelle, Ordner, Ressourcen) und alle Eigenschaften und Sicherheitseinstellungen, die diesen Elementen zugeordnet sind.  
  
-   Abonnements und Zeitplandefinitionen  
  
-   Berichtsmomentaufnahmen (einschließlich Abfrageergebnisse) und Berichtsverlauf  
  
-   Systemeigenschaften und Sicherheitseinstellungen auf Systemebene  
  
-   Protokolldaten zur Berichtsausführung  
  
-   Symmetrische Schlüssel, die verschlüsselte Verbindung und Anmeldeinformationen für externe Datenquellen  
  
 Da in der Berichtsserver-Datenbank der Anwendungsstatus und persistente Daten gespeichert sind, empfiehlt es sich, einen Sicherungszeitplan für diese Datenbank zu erstellen, um Datenverlust zu vermeiden. Empfehlungen und eine Anleitung zum Sichern der Datenbank finden Sie unter [Verschieben von Berichtsserver-Datenbanken auf einen anderen Computer &#40;einheitlicher SSRS-Modus&#41;](moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
## <a name="report-server-temporary-database"></a>Temporäre Berichtsserver-Datenbank  
 Jede Berichtsserver-Datenbank speichert mithilfe einer zugehörigen temporären Datenbank Sitzungs- und Ausführungsdaten, zwischengespeicherte Berichte und Arbeitstabellen, die vom Berichtsserver generiert werden. Im Hintergrund ausgeführte Serverprozesse entfernen regelmäßig ältere und nicht mehr verwendete Elemente aus den Tabellen in der temporären Datenbank.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erstellt eine fehlende temporäre Datenbank nicht neu und repariert auch keine fehlenden oder geänderten Tabellen. Auch wenn die temporäre Datenbank keine persistenten Daten enthält, sollten Sie eine Kopie davon sichern, sodass Sie sie im Rahmen einer Wiederherstellung nach einem Fehler nicht neu erstellen müssen.  
  
 Wenn Sie die temporäre Datenbank sichern und anschließend wiederherstellen, sollten Sie die Inhalte löschen. Grundsätzlich können die Inhalte der temporären Datenbank jederzeit bedenkenlos gelöscht werden. Nach dem Löschen der Inhalte müssen Sie den Windows-Dienst „Berichtsserver“ jedoch neu starten.  
  
## <a name="see-also"></a>Siehe auch  
 [Hosten einer Berichtsserver-Datenbank in einem SQL Server-Failovercluster](../install-windows/host-a-report-server-database-in-a-sql-server-failover-cluster.md)   
 [SSRS-Verschlüsselungsschlüssel: Speichern verschlüsselter Berichtsserverdaten](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Reporting Services-Berichtsserver](../reporting-services-report-server.md)   
 [Verwalten einer Berichtsserver-Datenbank &#40;nativer SSRS-Modus&#41;](report-server-database-ssrs-native-mode.md)   
 [Erstellen einer Berichtsserver-Datenbank](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)   
 [Sicherungs- und Wiederherstellungsvorgänge für Reporting Services](../install-windows/backup-and-restore-operations-for-reporting-services.md)  
  
  
