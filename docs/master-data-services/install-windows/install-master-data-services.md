---
title: Installationsaufgaben
description: Dieser Artikel bietet eine Übersicht über die Installation von Master Data Services, einschließlich der Installation und vor und nach der Installation.
ms.custom: ''
ms.date: 03/24/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: bb7aa3e7-8807-42c8-884f-0e41d7a20837
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 00248c7767e3b6205d19c395a1556ca8693e798e
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92257852"
---
# <a name="installation-tasks-for-master-data-services"></a>Installationsaufgaben für Master Data Services

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Dieser Artikel enthält eine Übersicht über die Installationsaufgaben sowie Links zu Anweisungen. Eine exemplarische Vorgehensweise zum Installieren und Konfigurieren von Master Data Services finden Sie unter [Master Data Services – Installation und Konfiguration](../../master-data-services/master-data-services-installation-and-configuration.md). 
  
-   [Installationsvorbereitung](#preinstall): Überprüfen Sie die Systemanforderungen, bevor Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]installieren.  
  
-   [Installationsvorgänge](#install): Installieren Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup oder über die Eingabeaufforderung.  
  
-   [Installationsnachbereitung](#postinstall): Öffnen Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , um die Vorgänge zur Installationsnachbereitung abzuschließen. Erstellen und konfigurieren Sie die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank, die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung und die Webdienste, und stellen Sie ein Beispielmodell bereit.  
  
##  <a name="pre-installation-tasks"></a><a name="preinstall"></a> Aufgaben vor der Installation  
  
|Aktion|Details|Verwandte Themen|  
|------------|-------------|--------------------|  
|Überprüfen der Installationsanforderungen|Der Computer, auf dem Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup ausführen, muss Mindestanforderungen für folgende Komponenten erfüllen:<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup<br /><br /> Die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung und die Webdienste<br /><br /> Die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank, wenn Sie die Datenbank auf dem gleichen Computer wie die Webanwendung hosten<br /><br /> <br /><br /> Sie können den Webservercomputer und Datenbankservercomputer trennen, indem Sie Setup nur auf dem Webservercomputer ausführen und die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank auf einem Remotecomputer erstellen, auf dem eine unterstützte Version und Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird.|[Von den Editionen von SQL Server 2016 unterstützte Funktionen](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)<br /><br /> [Hardware- und Softwareanforderungen für die Installation von SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)<br /><br /> [Anforderungen für die Webanwendung &#40;Master Data Services&#41;](../../master-data-services/install-windows/web-application-requirements-master-data-services.md)<br /><br /> [Datenbankanforderungen &#40;Master Data Services&#41;](../../master-data-services/install-windows/database-requirements-master-data-services.md)|  
|Konfigurieren der erforderlichen Rollen, Rollendienste und Funktionen|Bevor Sie das Setup ausführen, müssen Sie den Computer mit den erforderlichen Windows-Rollen, Rollendiensten und Funktionen konfigurieren.<br /><br /> Hinweis: Sie können diesen Schritt zwar auch zu einem späteren Zeitpunkt im Workflow ausführen, es ist jedoch hilfreich, diese Konfiguration vor dem Setup auszuführen, damit Sie direkt nach der Installation mit den Webkonfigurationstasks beginnen können.|[Anforderungen für die Webanwendung &#40;Master Data Services&#41;](../../master-data-services/install-windows/web-application-requirements-master-data-services.md)|  
|Überprüfen der Sprachunterstützung|Bestimmen Sie die Sprache, in der Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] installieren und ausführen möchten.|[Mehrsprachige und globale Bereitstellungen &#40;Master Data Services&#41;](../../master-data-services/install-windows/multi-lingual-and-global-deployments-master-data-services.md)|  
  
##  <a name="installation-operations"></a><a name="install"></a> Installationsvorgänge  
  
|Aktion|Details|Verwandte Themen|  
|------------|-------------|--------------------|  
|Führen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup aus.|Führen Sie auf dem Computer, der als Host für die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung und die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Webdienste fungiert, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup aus, oder verwenden Sie die Eingabeaufforderung, um [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]zu installieren. Im Setup von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] auf der Seite **Funktionsauswahl** unter **Freigegebene Funktionen**verfügbar. Wenn Sie eine Eingabeaufforderung verwenden, ist [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] als Funktionsparameter verfügbar. Beachten Sie, dass [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]durch den Setupvorgang in der Befehlszeile zwar installiert, aber nicht konfiguriert wird. Zur Konfiguration müssen Sie den Konfigurations-Manager für Master Data Services verwenden.<br /><br /> Installationsvorgang:<br /><br /> Installiert die Ordner und Dateien von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] an dem Ort, der für freigegebene Funktionen angegeben wurde, und weist den Objekten Berechtigungen zu.<br /><br /> Registriert [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Assemblys im Global Assembly Cache (GAC).<br /><br /> Installiert [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].|[Installieren Sie SQL Server 2016 über den Installations-Assistenten &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)<br /><br /> [Ordner- und Dateiberechtigungen &#40;Master Data Services&#41;](../../master-data-services/folder-and-file-permissions-master-data-services.md)|  
  
##  <a name="post-installation-tasks"></a><a name="postinstall"></a> Aufgaben nach der Installation  
  
|Aktion|Details|Verwandte Themen|  
|------------|-------------|--------------------|  
|Öffnen Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , um die Vorgänge zur Installationsnachbereitung abzuschließen.|Nach dem Abschluss von Setup öffnen Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] führt die folgenden Vorgänge zur Installationsnachbereitung auf dem lokalen Computer aus:<br /><br /> Erstellt die Windows-Gruppe **MDS_ServiceAccounts**, die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Dienstkonten für Anwendungspools enthält.<br /><br /> Erstellt im Installationspfad von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] den Ordner MDSTempDir und weist Berechtigungen für **MDS_ServiceAccounts**zu. In diesem Ordner werden temporäre Kompilierungsdateien für die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung kompiliert.<br /><br /> Konfiguriert in der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config-Datei das **tempDirectory** -Attribut des- **\<compilation>** Elements mit dem Pfad zum Ordner mdstempdir.|[Ordner- und Dateiberechtigungen &#40;Master Data Services&#41;](../../master-data-services/folder-and-file-permissions-master-data-services.md)<br /><br /> [Webkonfigurationsreferenz &#40;Master Data Services&#41;](../../master-data-services/web-configuration-reference-master-data-services.md)|  
|Erstellen einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank|Verwenden Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , um eine [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank für die Masterdaten zu erstellen.|[Erstellen einer Master Data Services-Datenbank](../../master-data-services/install-windows/create-a-master-data-services-database.md)|  
|Erstellen einer [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung|Verwenden Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , um eine Webanwendung zu erstellen und zu konfigurieren, die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]hostet.|[Erstellen einer Master Data Manager-Webanwendung &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)|  
|Zuordnen einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank zu einer Webanwendung|Verwenden Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , um die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank zuzuordnen.|[Zuordnen einer Master Data Services-Datenbank und -Webanwendung](../../master-data-services/install-windows/associate-a-master-data-services-database-and-web-application.md)|  
|Konfigurieren von Internet Explorer mit verstärkter Sicherheit|Wenn Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] auf einem Computer mit Windows Server 2012 installieren, müssen Sie möglicherweise die verstärkte Sicherheit von Internet Explorer konfigurieren, um die Skripterstellung für die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Anwendungswebsite zuzulassen. Andernfalls kann auf dem Servercomputer die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Anwendungswebsite nicht aufgerufen werden.|[Verstärkte Sicherheitskonfiguration für Internet Explorer](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd883248(v=ws.10))|  
|Installieren von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|Benutzer, die mit Masterdaten arbeiten, können [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]installieren.|[https://go.microsoft.com/fwlink/?LinkID=398159](https://go.microsoft.com/fwlink/?LinkID=398159)|  
|Integration in Data Quality Services (DQS) aktivieren|Aktivieren Sie für Benutzer von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]die Integration in das DQS-Feature, das zum Abgleich ähnlicher Daten verwendet werden kann.|[Aktivieren der Data Quality Services-Integration in Master Data Services](../../master-data-services/install-windows/enable-data-quality-services-integration-with-master-data-services.md)|  
|Bereitstellen eines Beispielmodells|Pakete mit Beispielmodellen werden mit Master Data Services installiert und können unter Verwendung von MDSModelDeploy.exe bereitgestellt werden.|[Bereitstellen von MDS-Beispielen in SQL Server](~/master-data-services/sql-server-samples-model-deployment-packages-mds.md)|
  
 Wenn während des Installationsvorgangs oder der Anfangskonfiguration Probleme auftreten, finden Sie weitere Informationen in TechNet Wiki unter [Behandeln von Installations- und Konfigurationsproblemen](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-installation-and-configuration-issues-master-data-services.aspx) .  
  
 Wenn Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] auf einem Computer nicht mehr benötigen, können Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] deinstallieren und bei Bedarf die Elemente entfernen, die vom Deinstallationsvorgang nicht betroffen sind. Weitere Informationen finden Sie unter [Deinstallieren und Entfernen von Master Data Services](../../sql-server/install/uninstall-and-remove-master-data-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installationsleitfaden für SQL Server](../../database-engine/install-windows/install-sql-server.md)  
  
