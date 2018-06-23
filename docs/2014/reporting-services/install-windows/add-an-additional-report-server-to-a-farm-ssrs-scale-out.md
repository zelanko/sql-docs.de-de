---
title: Hinzufügen eines zusätzlichen Berichtsservers zu einer Farm (Horizontales Skalieren für SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1a6b683-15cf-44ae-ac60-ceee63a60aaf
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: e3f59bd35ed4886c5c8ce35107120ab9a5eca87f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147848"
---
# <a name="add-an-additional-report-server-to-a-farm-ssrs-scale-out"></a>Hinzufügen eines zusätzlichen Berichtsservers zu einer Farm (Horizontales Skalieren für SSRS)
  Wenn Sie einen zweiten oder weitere Berichtsserver im SharePoint-Modus zur SharePoint-Farm hinzufügen, können die Leistung und die Antwortzeit für die Verarbeitung des Berichtsservers verbessert werden. Wenn Sie beim Hinzufügen weiterer Benutzer, Berichte und anderer Anwendungen zum Berichtsserver feststellen, dass es zu Leistungseinbußen kommt, kann die Leistung durch das Hinzufügen weiterer Berichtsserver verbessert werden. Es wird außerdem empfohlen, einen zweiten Berichtsserver hinzuzufügen, um die Verfügbarkeit von Berichtsservern zu vergrößern, wenn es Probleme mit der Hardware gibt oder Sie allgemeine Wartungsarbeiten auf einzelnen Servern in der Umgebung durchführen. Ab Version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] entsprechen die Schritte für horizontales Skalieren einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Umgebung im SharePoint-Modus der Standardbereitstellung von SharePoint-Farmen und nutzen die SharePoint-Lastenausgleichsfunktionen.  
  
> [!IMPORTANT]  
>  Das horizontales Skalieren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird nicht in allen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt. Weitere Informationen finden Sie unter der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Abschnitt [von den Editionen von SQL Server 2014 unterstützte Funktionen](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
> [!TIP]  
>  Ab Version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] verwenden Sie nicht mehr den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, um Server hinzuzufügen und Berichtsserver zu skalieren. SharePoint-Produkte verwalten das horizontale Skalieren von Berichtsdiensten, da SharePoint-Server mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst der Farm hinzugefügt werden.  
  
 Informationen zum horizontalen Skalieren von Berichtsservern im einheitlichen Modus finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für Bereitstellungen für horizontales Skalieren &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
-   [Lastenausgleich](#bkmk_loadbalancing)  
  
-   [Erforderliche Komponenten](#bkmk_prerequisites)  
  
-   [Schritte](#bkmk_steps)  
  
-   [Zusätzliche Konfiguration](#bkmk_additional)  
  
##  <a name="bkmk_loadbalancing"></a> Lastenausgleich  
 Der Lastenausgleich von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendungen wird automatisch von SharePoint verwaltet, außer wenn die Umgebung eine benutzerdefinierte oder eine Drittanbieter-Lastenausgleichslösung hat. Das Standard-SharePoint-Lastenausgleichsverhalten ist, dass jede [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung von allen Anwendungsservern ausgeglichen wird, wo Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst gestartet haben. Um zu überprüfen, ob der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst installiert und gestartet ist, klicken Sie auf **Dienste auf dem Server verwalten** in der SharePoint-Zentraladministration.  
  
##  <a name="bkmk_prerequisites"></a> Voraussetzungen  
  
-   Sie müssen lokaler Administrator sein, um SQL Server-Setup auszuführen.  
  
-   Der Computer muss einer Domäne hinzugefügt werden.  
  
-   Sie müssen den Namen des vorhandenen Datenbankservers wissen, der die SharePoint-Konfiguration und Inhaltsdatenbanken hostet.  
  
-   Der Datenbankserver muss konfiguriert sein, um Remotedatenbankverbindungen zu berücksichtigen.  Wenn nicht, sind Sie nicht in der Lage, den neuen Server zur Farm hinzuzufügen, da der neue Server nicht in der Lage ist, eine Verbindung mit den SharePoint-Konfigurationsdatenbanken herzustellen.  
  
-   Auf dem neuen Server muss die gleiche Version von SharePoint installiert sein, die auf den aktuellen Farmservern ausgeführt wird. Wenn auf der Farm z. B. bereits SharePoint 2010 Service Pack 1 (SP1) installieren ist, müssen Sie SP1 auch auf dem neuen Server installieren, bevor er zur Farm hinzugefügt werden kann.  
  
-   Überprüfen Sie die folgenden weiteren Themen, um System- und Versionsanforderungen zu verstehen:  
  
     [Leitfaden zum Verwenden von SQL Server BI-Features in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="bkmk_steps"></a> Schritte  
 Die Schritte in diesem Thema gehen davon aus, dass ein SharePoint-Farmadministrator den Server installiert und konfiguriert. Das Diagramm zeigt eine typische dreistufige Umgebung, und die nummerierten Elemente im Diagramm werden in der folgenden Liste beschrieben:  
  
-   (1) Mehrere Web-Front-End (WFE)-Server. Die WFE-Server erfordern das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint 2010.  
  
-   (2) Ein Einzelanwendungsserver, der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und Websites ausführt, z. B. Zentraladministration. Mit den folgenden Schritte wird dieser Ebene ein zweiter Anwendungsserver hinzugefügt.  
  
-   (3) Zwei SQL Server-Datenbankserver.  
  
-   (4) Stellt eine Software oder eine Hardware-Netzwerklastenausgleichslösung (NLB) dar  
  
 ![Hinzufügen eines Reporting Services-Anwendungsservers](../../../2014/sql-server/install/media/rs-sharepointscale.gif "Adding a Reporting Services application server")  
  
 Die folgenden Schritte gehen davon aus, dass ein Administrator den Server installiert und konfiguriert. Der Server wird als neuer Anwendungsserver in der Farm eingerichtet und nicht als Web-Front-End (WFE) verwendet.  
  
|Schritt|Beschreibung und Link|  
|----------|--------------------------|  
|Führen Sie das Vorbereitungstool für SharePoint 2010-Produkte aus.|Sie müssen über die Installationsmedien für SharePoint 2010 verfügen. Das Vorbereitungstool heißt **PrerequisiteInstaller.exe** auf dem Installationsmedium.|  
|Installieren Sie ein SharePoint 2010-Produkt.|(1) Wählen Sie die **Serverfarm** Installationstyp.<br /><br /> 2) Wählen Sie **Complete** für den Servertyp.<br /><br /> 3) Wenn die Installation abgeschlossen ist, führen Sie nicht den Konfigurations-Assistenten für SharePoint-Produkte aus, wenn die vorhandene SharePoint-Farm SharePoint 2010 SP1 installiert hat. Sie sollten SharePoint SP1 vor dem Ausführen des Konfigurations-Assistenten für SharePoint-Produkte installieren.|  
|Installieren Sie SharePoint Server 2010 SP1.|Verfügt die vorhandene SharePoint-Farm SharePoint 2010 SP1 installiert SharePoint 2010 SP1 aus herunterladen und installieren:[http://support.microsoft.com/kb/2460045](http://go.microsoft.com/fwlink/p/?linkID=219697).<br /><br /> Weitere Informationen zu SharePoint 2010 SP1 finden Sie unter [Bekannte Probleme bei der Installation von Office 2010 SP1 und SharePoint 2010 SP1](http://support.microsoft.com/kb/2532126):|  
|Führen Sie den Konfigurations-Assistenten für SharePoint-Produkte aus, um den Server zur Farm hinzuzufügen.|1) klicken Sie in der **Microsoft SharePoint 2010-Produkte** Programmgruppe, klicken Sie auf **Konfigurations-Assistenten für Microsoft SharePoint 2010-Produkte**.<br /><br /> (2) auf den **Herstellen einer Verbindung mit einer Serverfarm** Seite **Herstellen einer Verbindung mit einer vorhandenen Farm** , und klicken Sie auf **Weiter**.<br /><br /> (3) auf die **Einstellungen für die Konfigurationsdatenbank angeben** Seite, geben Sie den Namen des Datenbankservers, der für die vorhandene Farm und den Namen der Konfigurationsdatenbank verwendet. Klicken Sie auf **Weiter**.<br />**\*\* Wichtige \* \***  , wenn Sie eine Fehlermeldung ähnlich der folgenden sehen aus, und Sie überprüft haben, Sie sind berechtigt, dann überprüfen Sie welche Protokolle aktiviert sind, für die SQL Server-Netzwerkkonfiguration im **Sql Server Configuration Manager**: "Fehler beim Verbinden mit dem Datenbankserver. Sicher, dass die Datenbank vorhanden ist, ist ein Sql Server und, dass Sie die entsprechenden Berechtigungen zum Zugriff auf den Server verfügen."<br />**\*\* Wichtige \* \***  Wenn die Seite dort **Serverfarmprodukte und Patch Status**, müssen Sie die Informationen auf der Seite überprüfen und den Server mit den benötigten Dateien aktualisieren, bevor Sie fortfahren können mit den Server zur Farm hinzuzufügen.<br /><br /> (4) auf die **Farmsicherheitseinstellungen angeben** Seite Geben Sie die Passphrase der Farm ein, und klicken Sie auf **Weiter**. Klicken Sie auf der Bestätigungsseite auf **Weiter** , um den Assistenten auszuführen.<br /><br /> 5) klicken Sie auf **Weiter** zum Ausführen der **Farm-Konfigurations-Assistenten**.|  
|Überprüfen Sie, dass der Server zur SharePoint-Farm hinzugefügt wurde.|1) Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Systemeinstellungen** auf **Server in dieser Farm verwalten** .<br /><br /> 2) Überprüfen Sie, ob der neue Server hinzugefügt wurde und der Status richtig ist.<br /><br /> (3) Beachten Sie den Dienst nicht angezeigt **SQL Server Reporting Services-Dienst** ausgeführt wird. Der Dienst wird im nächsten Schritt installiert.<br /><br /> (4) um diesen Server aus der WFE-Rolle zu entfernen, klicken Sie auf **Dienste auf dem Server verwalten** und Beenden des Diensts **Microsoft SharePoint Foundation-Webanwendungsdienst**.|  
|Installieren und konfigurieren Sie Reporting Services im SharePoint-Modus.|Führen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installation aus. Für Weitere Informationen zur Installation von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus finden Sie unter [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) , wenn der Server nur verwendet werden, wird einem Anwendungsserver und dem Server nicht als verwendet ein WFE, Sie müssen nicht auf **Reporting Services-add-in für SharePoint-Produkte** auf:<br /><br /> die **Setuprolle** Seite **SQL Server-Funktionsinstallation**<br /><br /> die **Funktionsauswahl** Seite **Reporting Services - SharePoint**<br /><br /> -oder-<br /><br /> die **Reporting Services-Konfiguration** für die seitenüberprüfung der **nur Installation** ausgewählt ist für **SharePoint-Modus von Reporting Services**.|  
|Überprüfen Sie, ob der Reporting Services betriebsbereit ist.|1) Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Systemeinstellungen** auf **Server in dieser Farm verwalten** .<br /><br /> 2) Überprüfen Sie den **SQL Server Reporting Services-Dienst**.<br /><br /> Weitere Informationen finden Sie unter [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).|  
  
##  <a name="bkmk_additional"></a> Zusätzliche Konfiguration  
 Sie können einzelne [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Server in einer horizontal skalierten Bereitstellung optimieren, um nur die Hintergrundverarbeitung auszuführen, damit sie bei der interaktiven Berichtsausführung keine zusätzlichen Ressourcen verbrauchen. Hintergrundverarbeitung schließt Zeitpläne, Abonnements und Datenwarnungen ein.  
  
 Um das Verhalten einzelner Berichtsserver zu ändern, legen Sie **\<IsWebServiceEnable>** in der Konfigurationsdatei **RSreportServer.config** auf FALSE fest.  
  
 Bei der Konfiguration von Berichtsservern wird der Wert \<IsWebServiceEnable> standardmäßig auf TRUE festgelegt. Wenn alle Server auf TRUE festgelegt werden, besteht bei der interaktiven und Hintergrundverarbeitung ein Lastenausgleich über alle Knoten hinweg in der Farm.  
  
 Wenn Sie bei der Konfiguration sämtlicher Berichtsserver den Wert \<IsWebServiceEnable> auf FALSE festlegen, wird eine Fehlermeldung angezeigt, die derjenigen ähnelt, die angezeigt wird, wenn Sie versuchen, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Funktionen zu verwenden:  
  
 Der Reporting Services-Webdienst ist nicht aktiviert. Konfigurieren Sie mindestens eine Instanz von Reporting Services SharePoint Service haben \<IsWebServiceEnable > auf "true" festgelegt ist. Weitere Informationen finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Web-oder Anwendungsservers zu Farmen in SharePoint 2013](http://technet.microsoft.com/library/cc261752.aspx)   
 [Konfigurieren von Diensten (SharePoint Server 2010)](http://technet.microsoft.com/library/ee794878.aspx)  
  
  