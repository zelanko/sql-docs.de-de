---
title: Installieren von Master Data Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: bb7aa3e7-8807-42c8-884f-0e41d7a20837
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c52c5a160148b914874d5b237ecfae7edf8518c3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62924147"
---
# <a name="install-master-data-services"></a>Installieren von Master Data Services
  Der folgende Workflow bietet eine Übersicht über die Installation und Konfiguration von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Installation besteht aus drei Teilen:  
  
-   [Vor der Installation:](#preinstall) Überprüfen Sie vor der Installation die Systemanforderungen [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
-   [Installationsvorgänge](#install): Installieren Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup oder über die Eingabeaufforderung.  
  
-   [Nach der Installation:](#postinstall) Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] um Vorgänge zur installationsnachbereitung abzuschließen. Erstellen und konfigurieren Sie die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank, die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung und die Webdienste, und stellen Sie ein Beispielmodell bereit.  
  
##  <a name="preinstall"></a> Installationsvorbereitung  
  
|Aktion|Details|Verwandte Themen|  
|------------|-------------|--------------------|  
|Überprüfen der Installationsanforderungen|Der Computer, auf dem Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup ausführen, muss Mindestanforderungen für folgende Komponenten erfüllen:<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup<br /><br /> Die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung und die Webdienste<br /><br /> Die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank, wenn Sie die Datenbank auf dem gleichen Computer wie die Webanwendung hosten<br /><br /> Beachten Sie, dass Sie den Webservercomputer und Datenbankservercomputer trennen können, indem Sie Setup auf dem Webservercomputer ausführen und erstellen die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Datenbank auf einem Remotecomputer befindet, der eine unterstützte Version und Edition von ausgeführt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[Von den SQL Server 2014-Editionen unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)<br /><br /> [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)<br /><br /> [Anforderungen für die Webanwendung &#40;Master Data Services&#41;](web-application-requirements-master-data-services.md)<br /><br /> [Datenbankanforderungen &#40;Master Data Services&#41;](database-requirements-master-data-services.md)|  
|Konfigurieren der erforderlichen Rollen, Rollendienste und Funktionen|Bevor Sie das Setup ausführen, müssen Sie den Computer mit den erforderlichen Windows-Rollen, Rollendiensten und Funktionen konfigurieren.<br /><br /> Hinweis: Obwohl Sie diesen Schritt später im Workflow ausführen können, ist es hilfreich, diese Konfiguration vor Ausführen des Setups, damit Sie die Web-Konfigurationstasks, die direkt nach der Installation ausführen können.|[Anforderungen für die Webanwendung &#40;Master Data Services&#41;](web-application-requirements-master-data-services.md)|  
|Überprüfen der Sprachunterstützung|Bestimmen Sie die Sprache, in der Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] installieren und ausführen möchten.|[Mehrsprachige und globale Bereitstellungen &#40;Master Data Services&#41;](multi-lingual-and-global-deployments-master-data-services.md)|  
  
##  <a name="install"></a> Installationsvorgänge  
  
|Aktion|Details|Verwandte Themen|  
|------------|-------------|--------------------|  
|Führen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup aus.|Führen Sie auf dem Computer, der als Host für die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung und die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Webdienste fungiert, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup aus, oder verwenden Sie die Eingabeaufforderung, um [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]zu installieren. Im Setup von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] auf der Seite **Funktionsauswahl** unter **Freigegebene Funktionen**verfügbar. Wenn Sie eine Eingabeaufforderung verwenden, ist [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] als Funktionsparameter verfügbar. Beachten Sie, dass [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]durch den Setupvorgang in der Befehlszeile zwar installiert, aber nicht konfiguriert wird. Zur Konfiguration müssen Sie den Konfigurations-Manager für Master Data Services verwenden. Installationsvorgang:<br /><br /> Installiert die Ordner und Dateien von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] an dem Ort, der für freigegebene Funktionen angegeben wurde, und weist den Objekten Berechtigungen zu.<br /><br /> Registriert [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Assemblys im Global Assembly Cache (GAC).<br /><br /> Installiert [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].|[Installieren von SQLServer 2014 vom Installations-Assistenten &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)<br /><br /> [Ordner- und Dateiberechtigungen &#40;Master Data Services&#41;](../folder-and-file-permissions-master-data-services.md)|  
  
##  <a name="postinstall"></a> Installationsnachbereitung  
  
|Aktion|Details|Verwandte Themen|  
|------------|-------------|--------------------|  
|Öffnen Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , um die Vorgänge zur Installationsnachbereitung abzuschließen.|Nach dem Abschluss von Setup öffnen Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] führt die folgenden Vorgänge zur Installationsnachbereitung auf dem lokalen Computer aus:<br /><br /> Erstellt die Windows-Gruppe **MDS_ServiceAccounts**, die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Dienstkonten für Anwendungspools enthält.<br /><br /> Erstellt im Installationspfad von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] den Ordner MDSTempDir und weist Berechtigungen für **MDS_ServiceAccounts**zu. In diesem Ordner werden temporäre Kompilierungsdateien für die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung kompiliert.<br /><br /> In der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config-Datei konfiguriert die `tempDirectory` Attribut der  **\<Kompilierung >** -Elements mit dem Pfad zum Ordner MDSTempDir.<br /><br /> <br /><br /> Wenn Sie ein Skript für den Installationsvorgang schreiben, können Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] öffnen, um das [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]-Snap-In zu registrieren, die anderen Schritte müssen Sie jedoch manuell ausführen, um die Konfiguration abzuschließen. [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] stellt einen assistentengesteuerten Konfigurationsprozess zur Verfügung. Zum Konfigurieren von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] ist kein Befehlszeilenprozess verfügbar.|[Ordner- und Dateiberechtigungen &#40;Master Data Services&#41;](../folder-and-file-permissions-master-data-services.md)<br /><br /> [Webkonfigurationsreferenz &#40;Master Data Services&#41;](../web-configuration-reference-master-data-services.md)|  
|Erstellen einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank|Verwenden Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , um eine [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank für die Masterdaten zu erstellen.|[Erstellen einer Master Data Services-Datenbank](create-a-master-data-services-database.md)|  
|Erstellen einer [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung|Verwenden Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , um eine Webanwendung zu erstellen und zu konfigurieren, die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]hostet.|[Erstellen einer Master Data Manager-Webanwendung &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)|  
|Zuordnen einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank zu einer Webanwendung|Verwenden Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , um die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank zuzuordnen.|[Zuordnen einer Master Data Services-Datenbank und -Webanwendung](associate-a-master-data-services-database-and-web-application.md)|  
|Konfigurieren von Internet Explorer mit verstärkter Sicherheit|Wenn Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] auf einem Computer mit Windows Server 2008 oder Windows Server 2008 R2 installieren, müssen Sie möglicherweise verstärkte Sicherheit von Internet Explorer konfigurieren, um die Skripterstellung für die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Anwendungswebsite zuzulassen. Andernfalls kann auf dem Servercomputer die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Anwendungswebsite nicht aufgerufen werden.|[InternetExplorer: Verstärkte Sicherheitskonfiguration](https://go.microsoft.com/fwlink/p/?LinkId=223869)|  
|Installieren von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|Benutzer, die mit Masterdaten arbeiten, können [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]installieren.|[https://go.microsoft.com/fwlink/?LinkId=219530](https://go.microsoft.com/fwlink/?LinkId=219530)|  
|Integration in Data Quality Services (DQS) aktivieren|Aktivieren Sie für Benutzer von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]die Integration in das DQS-Feature, das zum Abgleich ähnlicher Daten verwendet werden kann.|[Aktivieren der Data Quality Services-Integration in Master Data Services](enable-data-quality-services-integration-with-master-data-services.md)|  
|Bereitstellen eines Beispielmodells|Pakete mit Beispielmodellen werden mit Master Data Services installiert und können unter Verwendung von MDSModelDeploy.exe bereitgestellt werden.|[Bereitstellen von MDS-Beispielen in SQL Server](https://go.microsoft.com/fwlink/?LinkId=251486&clcid=0x409)|  
  
 Wenn während des Installationsvorgangs oder der Anfangskonfiguration Probleme auftreten, finden Sie weitere Informationen in TechNet Wiki unter [Behandeln von Installations- und Konfigurationsproblemen](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-installation-and-configuration-issues-master-data-services.aspx) .  
  
 Wenn Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] auf einem Computer nicht mehr benötigen, können Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] deinstallieren und bei Bedarf die Elemente entfernen, die vom Deinstallationsvorgang nicht betroffen sind. Weitere Informationen finden Sie unter [Deinstallieren und Entfernen von Master Data Services](../../sql-server/install/uninstall-and-remove-master-data-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von SQL Server 2014](../../database-engine/install-windows/install-sql-server.md)  
  
  
