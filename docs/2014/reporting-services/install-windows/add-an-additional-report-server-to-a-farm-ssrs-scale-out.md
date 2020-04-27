---
title: Hinzufügen eines zusätzlichen Berichtsservers zu einer Farm (Horizontales Skalieren für SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1a6b683-15cf-44ae-ac60-ceee63a60aaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b90bb5624e5b5cdbf3f1542ad0bef0d2765da248
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108967"
---
# <a name="add-an-additional-report-server-to-a-farm-ssrs-scale-out"></a>Hinzufügen eines zusätzlichen Berichtsservers zu einer Farm (Horizontales Skalieren für SSRS)
  Wenn Sie einen zweiten oder weitere Berichtsserver im SharePoint-Modus zur SharePoint-Farm hinzufügen, können die Leistung und die Antwortzeit für die Verarbeitung des Berichtsservers verbessert werden. Wenn Sie beim Hinzufügen weiterer Benutzer, Berichte und anderer Anwendungen zum Berichtsserver feststellen, dass es zu Leistungseinbußen kommt, kann die Leistung durch das Hinzufügen weiterer Berichtsserver verbessert werden. Es wird außerdem empfohlen, einen zweiten Berichtsserver hinzuzufügen, um die Verfügbarkeit von Berichtsservern zu vergrößern, wenn es Probleme mit der Hardware gibt oder Sie allgemeine Wartungsarbeiten auf einzelnen Servern in der Umgebung durchführen. Ab Version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] entsprechen die Schritte für horizontales Skalieren einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Umgebung im SharePoint-Modus der Standardbereitstellung von SharePoint-Farmen und nutzen die SharePoint-Lastenausgleichsfunktionen.  
  
> [!IMPORTANT]  
>  Das horizontales Skalieren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird nicht in allen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt. Weitere Informationen finden Sie im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Abschnitt der Features, [die von den Editionen von SQL Server 2014 unterstützt werden](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
> [!TIP]  
>  Ab Version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] verwenden Sie nicht mehr den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager, um Server hinzuzufügen und Berichtsserver aufzuskalieren. SharePoint-Produkte verwalten das horizontale Skalieren von Berichtsdiensten, da SharePoint-Server mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst der Farm hinzugefügt werden.  
  
 Informationen zum horizontalen Skalieren von Berichtsservern im einheitlichen Modus finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für Bereitstellungen für horizontales Skalieren &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
-   [Lastenausgleich](#bkmk_loadbalancing)  
  
-   [Voraussetzungen](#bkmk_prerequisites)  
  
-   [Nehmen](#bkmk_steps)  
  
-   [Zusätzliche Konfiguration](#bkmk_additional)  
  
##  <a name="load-balancing"></a><a name="bkmk_loadbalancing"></a>Lastenausgleich  
 Der Lastenausgleich von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendungen wird automatisch von SharePoint verwaltet, außer wenn die Umgebung eine benutzerdefinierte oder eine Drittanbieter-Lastenausgleichslösung hat. Das Standard-SharePoint-Lastenausgleichsverhalten ist, dass jede [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung von allen Anwendungsservern ausgeglichen wird, wo Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst gestartet haben. Um zu überprüfen, ob der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst installiert und gestartet ist, klicken Sie auf **Dienste auf dem Server verwalten** in der SharePoint-Zentraladministration.  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a> Voraussetzungen  
  
-   Sie müssen lokaler Administrator sein, um SQL Server-Setup auszuführen.  
  
-   Der Computer muss einer Domäne hinzugefügt werden.  
  
-   Sie müssen den Namen des vorhandenen Datenbankservers wissen, der die SharePoint-Konfiguration und Inhaltsdatenbanken hostet.  
  
-   Der Datenbankserver muss konfiguriert sein, um Remotedatenbankverbindungen zu berücksichtigen.  Wenn nicht, sind Sie nicht in der Lage, den neuen Server zur Farm hinzuzufügen, da der neue Server nicht in der Lage ist, eine Verbindung mit den SharePoint-Konfigurationsdatenbanken herzustellen.  
  
-   Auf dem neuen Server muss die gleiche Version von SharePoint installiert sein, die auf den aktuellen Farmservern ausgeführt wird. Wenn auf der Farm z. B. bereits SharePoint 2010 Service Pack 1 (SP1) installieren ist, müssen Sie SP1 auch auf dem neuen Server installieren, bevor er zur Farm hinzugefügt werden kann.  
  
-   Überprüfen Sie die folgenden weiteren Themen, um System- und Versionsanforderungen zu verstehen:  
  
     [Leitfaden zum Verwenden von SQL Server BI-Funktionen in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="steps"></a><a name="bkmk_steps"></a>Nehmen  
 Die Schritte in diesem Thema gehen davon aus, dass ein SharePoint-Farmadministrator den Server installiert und konfiguriert. Das Diagramm zeigt eine typische dreistufige Umgebung, und die nummerierten Elemente im Diagramm werden in der folgenden Liste beschrieben:  
  
-   (1) Mehrere Web-Front-End (WFE)-Server. Die WFE-Server erfordern das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint 2010.  
  
-   (2) Ein Einzelanwendungsserver, der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und Websites ausführt, z. B. Zentraladministration. Mit den folgenden Schritte wird dieser Ebene ein zweiter Anwendungsserver hinzugefügt.  
  
-   (3) Zwei SQL Server-Datenbankserver.  
  
-   (4) Stellt eine Software oder eine Hardware-Netzwerklastenausgleichslösung (NLB) dar  
  
 ![Hinzufügen eines Reporting Services-Anwendungsservers](../../../2014/sql-server/install/media/rs-sharepointscale.gif "Hinzufügen eines Reporting Services-Anwendungsservers")  
  
 Die folgenden Schritte gehen davon aus, dass ein Administrator den Server installiert und konfiguriert. Der Server wird als neuer Anwendungsserver in der Farm eingerichtet und nicht als Web-Front-End (WFE) verwendet.  
  
|Schritt|Beschreibung und Link|  
|----------|--------------------------|  
|Führen Sie das Vorbereitungstool für SharePoint 2010-Produkte aus.|Sie müssen über die Installationsmedien für SharePoint 2010 verfügen. Das Vorbereitungstool heißt **PrerequisiteInstaller.exe** auf dem Installationsmedium.|  
|Installieren Sie ein SharePoint 2010-Produkt.|1) wählen Sie den Installationstyp **Server Farm** aus.<br /><br /> 2) wählen Sie für den Servertyp die Option **Fertig** aus.<br /><br /> 3) Wenn die Installation abgeschlossen ist, führen Sie nicht den Konfigurations-Assistenten für SharePoint-Produkte aus, wenn die vorhandene SharePoint-Farm SharePoint 2010 SP1 installiert hat. Sie sollten SharePoint SP1 vor dem Ausführen des Konfigurations-Assistenten für SharePoint-Produkte installieren.|  
|Installieren Sie SharePoint Server 2010 SP1.|Wenn auf Ihrer vorhandenen SharePoint-Farm SharePoint 2010 SP1 installiert ist, laden Sie SharePoint 2010 SP1[https://support.microsoft.com/kb/2460045](https://go.microsoft.com/fwlink/p/?linkID=219697)von: herunter, und installieren Sie es.<br /><br /> Weitere Informationen zu SharePoint 2010 SP1 finden Sie unter [Bekannte Probleme bei der Installation von Office 2010 SP1 und SharePoint 2010 SP1](https://support.microsoft.com/kb/2532126):|  
|Führen Sie den Konfigurations-Assistenten für SharePoint-Produkte aus, um den Server zur Farm hinzuzufügen.|1) klicken Sie in der Programmgruppe **Microsoft SharePoint 2010-Produkte** auf **Konfigurations-Assistent für Microsoft SharePoint 2010-Produkte**.<br /><br /> 2) wählen Sie auf der Seite **Verbindung mit einer Server Farm herstellen** die **Option mit einer vorhandenen Farm verbinden aus,** und klicken Sie auf **weiter**.<br /><br /> 3) geben Sie auf der Seite Einstellungen für die **Konfigurations Datenbank angeben** den Namen des für die vorhandene Farm verwendeten Datenbankservers und den Namen der Konfigurations Datenbank ein. Klicken Sie auf **Weiter**.<br />** \* Wichtig \* \* ** Wenn eine Fehlermeldung ähnlich der folgenden angezeigt wird und Sie überprüft haben, ob Sie über die entsprechenden Berechtigungen verfügen, überprüfen Sie, welche Protokolle für die SQL Server Netzwerkkonfiguration in **SQL Server**aktiviert sind Configuration Manager: "Fehler beim Herstellen einer Verbindung mit dem Daten Bank Server. Stellen Sie sicher, dass die Datenbank vorhanden ist, eine SQL Server-Datenbank ist und Sie über die entsprechenden Berechtigungen für den Zugriff auf den Server verfügen. "<br />** \* Wichtig \* \* ** Wenn die Seite **Server Farm Produkt und Patchstatus**angezeigt wird, müssen Sie die Informationen auf der Seite überprüfen und den Server mit den benötigten Dateien aktualisieren, bevor Sie mit dem Hinzufügen des Servers zur Farm fortfahren können.<br /><br /> 4) geben Sie auf der Seite **Farm Sicherheitseinstellungen angeben** die Passphrase der Farm ein, und klicken Sie auf **weiter**. Klicken Sie auf der Bestätigungsseite auf **Weiter** , um den Assistenten auszuführen.<br /><br /> 5) klicken Sie auf **weiter** , um den Assistenten für die **Farm Konfiguration**auszuführen.|  
|Überprüfen Sie, dass der Server zur SharePoint-Farm hinzugefügt wurde.|1) Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Systemeinstellungen** auf **Server in dieser Farm verwalten** .<br /><br /> 2) Überprüfen Sie, ob der neue Server hinzugefügt wurde und der Status richtig ist.<br /><br /> 3) beachten Sie, dass der Dienst **SQL Server Reporting Services Dienst** nicht ausgeführt wird. Der Dienst wird im nächsten Schritt installiert.<br /><br /> 4) um diesen Server aus der WFE-Rolle zu entfernen, klicken Sie auf **Dienste auf dem Server verwalten** , und führen Sie den Dienst **Microsoft SharePoint Foundation-Webanwendung**aus.|  
|Installieren und konfigurieren Sie Reporting Services im SharePoint-Modus.|Führen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installation aus. Weitere Informationen zur Installation des SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Modus finden Sie unter [Installieren von Reporting Services SharePoint-Modus für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) wenn der Server nur als Anwendungsserver verwendet wird und der Server nicht als WFE verwendet wird, müssen Sie **Reporting Services-Add-in für SharePoint-Produkte** nicht auswählen in:<br /><br /> Wählen Sie auf der Seite **Setup Rolle** die Option **SQL Server Funktions Installation** aus.<br /><br /> Wählen Sie auf der Seite **Funktionsauswahl** die Option **Reporting Services-SharePoint** aus.<br /><br /> ODER<br /><br /> Überprüfen Sie auf der Seite **Reporting Services Konfiguration** , ob die Option **nur installieren** für **Reporting Services SharePoint-Modus**ausgewählt ist.|  
|Überprüfen Sie, ob der Reporting Services betriebsbereit ist.|1) Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Systemeinstellungen** auf **Server in dieser Farm verwalten** .<br /><br /> 2) Überprüfen Sie den **SQL Server Reporting Services-Dienst**.<br /><br /> Weitere Informationen finden Sie unter [Überprüfen einer Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md) .|  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional"></a>Zusätzliche Konfiguration  
 Sie können einzelne [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Server in einer horizontal skalierten Bereitstellung optimieren, um nur die Hintergrundverarbeitung auszuführen, damit sie bei der interaktiven Berichtsausführung keine zusätzlichen Ressourcen verbrauchen. Hintergrundverarbeitung schließt Zeitpläne, Abonnements und Datenwarnungen ein.  
  
 Um das Verhalten einzelner Berichts Server zu ändern, legen Sie ** \<iswebserviceenable>** in der Konfigurationsdatei **RSReportServer. config** auf false fest.  
  
 Bei der Konfiguration von Berichtsservern wird der Wert \<IsWebServiceEnable> standardmäßig auf TRUE festgelegt. Wenn alle Server auf TRUE festgelegt werden, besteht bei der interaktiven und Hintergrundverarbeitung ein Lastenausgleich über alle Knoten hinweg in der Farm.  
  
 Wenn Sie bei der Konfiguration sämtlicher Berichtsserver den Wert \<IsWebServiceEnable> auf FALSE festlegen, wird eine Fehlermeldung angezeigt, die derjenigen ähnelt, die angezeigt wird, wenn Sie versuchen, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Funktionen zu verwenden:  
  
 Der Reporting Services-Webdienst ist nicht aktiviert. Konfigurieren Sie mindestens eine Instanz des Reporting Services SharePoint-Dienstanbieter \<, damit iswebserviceenable> auf true festgelegt ist. Weitere Informationen finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Web-oder Anwendungsservern zu Farmen in SharePoint 2013](https://technet.microsoft.com/library/cc261752.aspx)   
 [Konfigurieren von Diensten (SharePoint Server 2010)](https://technet.microsoft.com/library/ee794878.aspx)  
  
  
