---
title: Hinzufügen eines zusätzlichen Reporting Services-Web-Front-Ends zu einer Farm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d7a11bda-ae26-49ac-b071-37d83cae5afe
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7996ea2541963d0c7a2060d819667e25d102305
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108963"
---
# <a name="add-an-additional-reporting-services-web-front-end-to-a-farm"></a>Hinzufügen eines zusätzlichen Reporting Services-Web-Front-Ends zu einer Farm
  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus schließt für Anwendungsserver und Web-Front-End-Server (WFE) benötigte Komponenten ein. In diesem Thema liegt der Schwerpunkt auf der Installation der erforderlichen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponenten für einen WFE-Server, einschließlich der Anwendungsseiten, die von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktionen wie z. B. Abonnements, Datenwarnungen und [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]verwendet werden. Die primäre für ein WFE benötigte [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation ist das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-In für SharePoint 2010-Produkte.  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
-   Sie müssen lokaler Administrator sein, um SQL Server-Setup auszuführen.  
  
-   Der Computer muss einer Domäne hinzugefügt werden.  
  
-   Sie müssen den Namen des vorhandenen Datenbankservers wissen, der die SharePoint-Konfiguration und Inhaltsdatenbanken hostet.  
  
-   Der Datenbankserver muss konfiguriert sein, um Remotedatenbankverbindungen zu berücksichtigen.  Wenn nicht, sind Sie nicht in der Lage, den neuen Server zur Farm hinzuzufügen, da der neue Server nicht in der Lage ist, eine Verbindung mit den SharePoint-Konfigurationsdatenbanken herzustellen.  
  
-   Auf dem neuen Server muss die gleiche Version von SharePoint installiert sein, die auf den aktuellen Farmservern ausgeführt wird. Wenn auf der Farm z. B. bereits SharePoint 2010 Service Pack 1 (SP1) installieren ist, müssen Sie SP1 auch auf dem neuen Server installieren, bevor er zur Farm hinzugefügt werden kann.  
  
-   Überprüfen Sie die folgenden weiteren Themen, um System- und Versionsanforderungen zu verstehen:  
  
     [Leitfaden zum Verwenden von SQL Server BI-Funktionen in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
## <a name="steps"></a>Schritte  
 Die Schritte in diesem Thema gehen davon aus, dass ein SharePoint-Farmadministrator den Server installiert und konfiguriert. Das Diagramm zeigt eine typische dreistufige Umgebung, und die nummerierten Elemente im Diagramm werden in der folgenden Liste beschrieben:  
  
-   (1) Mehrere Web-Front-End (WFE)-Server. Die WFE-Server erfordern das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint 2010. Mit den folgenden Schritte wird dieser Ebene ein zweiter Anwendungsserver hinzugefügt.  
  
-   (2) Zwei Anwendungsserver, die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und Websites ausführen, z. B. Zentraladministration.  
  
-   (3) Zwei SQL Server-Datenbankserver.  
  
-   (4) Stellt eine Software oder eine Hardware-Netzwerklastenausgleichslösung (NLB) dar  
  
 ![Hinzufügen von SSRS zu einem neuen SharePoint WFE](../../../2014/sql-server/install/media/rs-sharepointscale-wfe.gif "Hinzufügen von SSRS zu einem neuen SharePoint WFE")  
  
 Die folgenden Schritte gehen davon aus, dass ein Administrator den Server installiert und konfiguriert.  
  
|Schritt|Beschreibung und Link|  
|----------|--------------------------|  
|Führen Sie das Vorbereitungstool für SharePoint 2010-Produkte aus.|Sie müssen über die Installationsmedien für SharePoint 2010 verfügen. Das Vorbereitungs Tool auf dem-Installationsmedium ist " **Voraussetzungen. exe** ".|  
|Installieren Sie ein SharePoint 2010-Produkt.|1) wählen Sie den Installationstyp **Server Farm** aus.<br /><br /> 2) wählen Sie für den Servertyp die Option **Fertig** aus.<br /><br /> 3) Wenn die Installation abgeschlossen ist, führen Sie nicht den Konfigurations-Assistenten für SharePoint-Produkte aus, wenn die vorhandene SharePoint-Farm SharePoint 2010 SP1 installiert hat. Sie sollten SharePoint SP1 vor dem Ausführen des Konfigurations-Assistenten für SharePoint-Produkte installieren.|  
|Installieren Sie SharePoint Server 2010 SP1.|Wenn auf Ihrer vorhandenen SharePoint-Farm SharePoint 2010 SP1 installiert ist, laden Sie SharePoint 2010 SP1[https://support.microsoft.com/kb/2460045](https://go.microsoft.com/fwlink/p/?linkID=219697)von: herunter, und installieren Sie es.<br /><br /> Weitere Informationen zu SharePoint 2010 SP1 finden Sie unter [Bekannte Probleme bei der Installation von Office 2010 SP1 und SharePoint 2010 SP1](https://support.microsoft.com/kb/2532126):|  
|Führen Sie den Konfigurations-Assistenten für SharePoint-Produkte aus, um den Server zur Farm hinzuzufügen.|1) klicken Sie in der Programmgruppe **Microsoft SharePoint 2010-Produkte** auf **Konfigurations-Assistent für Microsoft SharePoint 2010-Produkte**.<br /><br /> 2) wählen Sie auf der Seite **Verbindung mit einer Server Farm herstellen** die **Option mit einer vorhandenen Farm verbinden aus,** und klicken Sie auf **weiter**.<br /><br /> 3) geben Sie auf der Seite Einstellungen für die **Konfigurations Datenbank angeben** den Namen des für die vorhandene Farm verwendeten Datenbankservers und den Namen der Konfigurations Datenbank ein. Klicken Sie auf **Weiter**.<br />**&#42;&#42; wichtige &#42;&#42;** Wenn eine Fehlermeldung ähnlich der folgenden angezeigt wird und Sie überprüft haben, dass Sie über die entsprechenden Berechtigungen verfügen, überprüfen Sie, welche Protokolle für die SQL Server-Netzwerkkonfiguration in **SQL Server Configuration Manager**aktiviert sind. "Es konnte keine Verbindung mit dem Datenbankserver hergestellt werden. Stellen Sie sicher, dass die Datenbank vorhanden ist, eine SQL Server-Datenbank ist und Sie über die entsprechenden Berechtigungen für den Zugriff auf den Server verfügen. "<br />**&#42;&#42; wichtige &#42;&#42;** Wenn die Seite **Server Farm Produkt und Patchstatus**angezeigt wird, müssen Sie die Informationen auf der Seite überprüfen und den Server mit den benötigten Dateien aktualisieren, bevor Sie mit dem Hinzufügen des Servers zur Farm fortfahren können.<br /><br /> 4) geben Sie auf der Seite **Farm Sicherheitseinstellungen angeben** die Passphrase der Farm ein, und klicken Sie auf **weiter**. Klicken Sie auf der Bestätigungsseite auf **Weiter** , um den Assistenten auszuführen.<br /><br /> 5) klicken Sie auf **weiter** , um den Assistenten für die **Farm Konfiguration**auszuführen.|  
|Überprüfen Sie, dass der Server zur SharePoint-Farm hinzugefügt wurde.|1) Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Systemeinstellungen** auf **Server in dieser Farm verwalten** .<br /><br /> 2) Überprüfen Sie, ob der neue Server hinzugefügt wurde und der Status richtig ist.<br /><br /> 3) um diesen Server aus der WFE-Rolle zu entfernen, klicken Sie auf **Dienste auf dem Server verwalten** , und führen Sie den Dienst **Microsoft SharePoint Foundation-Webanwendung**aus.|  
|Installieren Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] das-Add-in für SharePoint 2010-Produkte.|Es gibt mehrere Methoden zum Installieren des Add-Ins. Die folgenden Schritte verwenden den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Setup-Assistenten. Weitere Informationen zum Installieren des Add-Ins finden Sie unter [installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Installation [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ausführen:<br /><br /> 1) Wählen Sie auf der Seite **Setuprolle** die Option **SQL Server-Funktionsinstallation**aus.<br /><br /> 2) wählen Sie auf der Seite **Funktionsauswahl** die Option **Reporting Services-Add-in für SharePoint-Produkte aus** .<br /><br /> 3) klicken Sie auf den nächsten Seiten auf **weiter** , um die Setup Optionen abzuschließen.<br /><br /> Weitere Informationen zum [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Installieren von finden Sie unter [install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|Überprüfen Sie, ob der neue Server betriebsbereit ist.|1) Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Systemeinstellungen** auf **Server in dieser Farm verwalten** .<br /><br /> 2) Überprüfen Sie, ob der neue Server in der Liste aufgeführt ist.|  
|Aktualisieren Sie die NLB-Lösung.|Aktualisieren Sie die Hardware- oder Software-NLB-Umgebung, falls erforderlich, um den neuen Server einzuschließen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen eines Web-oder Anwendungs Servers zur Farm (SharePoint Server 2010)](https://technet.microsoft.com/library/bb218968.aspx?missingurl=%2fen-us%2flibrary%2fe1aeaddf-6ee4-43a9-82b7-db20b68c71db\(Office.14\))   
 [Konfigurieren von Diensten (SharePoint Server 2010)](https://technet.microsoft.com/library/ee794878.aspx)  
  
  
