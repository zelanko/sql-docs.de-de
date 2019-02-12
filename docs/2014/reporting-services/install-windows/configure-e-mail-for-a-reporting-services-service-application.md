---
title: Konfigurieren von E-mail für eine Reporting-Dienstanwendung (SharePoint 2010 und SharePoint 2013 Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 106045d6899534bea31e6db264033f79dcb76a96
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56010432"
---
# <a name="configure-e-mail-for-a-reporting-services-service-application-sharepoint-2010-and-sharepoint-2013"></a>Konfigurieren von E-Mail für eine Reporting Services-Dienstanwendung (SharePoint 2010 und SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Datenwarnung sendet Warnungen in E-Mail-Nachrichten. Um E-Mails übermitteln zu können, kann es notwendig sein, dass Sie Ihre [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung konfigurieren und die E-Mail-Übermittlungserweiterung für die Dienstanwendung ändern müssen. Die E-Mail-Einstellungen sind ebenfalls notwendig, wenn Sie beabsichtigen, die E-Mail-Übermittlungserweiterung für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Abonnementfunktion zu verwenden.  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus &#124; SharePoint 2010 und SharePoint 2013.|  
  
### <a name="to-configure-e-mail-for-the-shared-service"></a>So konfigurieren Sie E-Mail-Einstellungen für den freigegebenen Service  
  
1.  Klicken Sie in der SharePoint-Zentraladministration auf **Anwendungsverwaltung**.  
  
2.  Klicken Sie in der Gruppe **Dienstanwendungen** auf **Dienstanwendungen verwalten**.  
  
3.  Klicken Sie in der Liste **Name** auf den Namen Ihrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung.  
  
4.  Klicken Sie auf der Seite **Reporting Services-Anwendung verwalten** auf **E-Mail-Einstellungen** .  
  
5.  Wählen Sie **SMTP-Server verwenden**aus.  
  
6.  Geben Sie im Feld **SMTP-Server für ausgehende Nachrichten** den Namen eines SMTP-Servers ein.  
  
7.  Geben Sie im Feld **Absenderadresse** eine E-Mail-Adresse ein.  
  
     Diese Adresse wird als Absender für alle Warnungs-E-Mail-Nachrichten verwendet.  
  
     Das Konto des in **Absenderadresse** angegebenen Benutzers muss ein verwaltetes Konto sein, das Sie bei der Konfiguration des Anwendungspools für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung angegeben haben. Wenn Sie die entsprechenden Rechte besitzen, können Sie eine Liste aller vorhandenen verwalteten Konten auf der Seite Dienstkonten in der SharePoint-Zentraladministration anzeigen.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a>NTLM-Authentifizierung  
  
1.  Wenn Ihre E-Mail-Umgebung NTLM-Authentifizierung erfordert und keinen anonymen Zugriff zulässt, müssen Sie die Konfiguration der E-Mail-Übermittlungserweiterung für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendungen ändern. Ändern Sie **SMTPAuthenticate** so, dass der Wert „2“ verwendet wird. Dieser Wert kann nicht über die Benutzeroberfläche geändert werden. Das folgende beispielhafte PowerShell-Skript aktualisiert die vollständige Konfiguration für die Berichtsserver-E-Mail-Übermittlungserweiterung für die Dienstanwendung mit dem Namen „SSRS_TESTAPPLICATION“. Beachten Sie, dass einige der im Skript aufgeführten Knoten, wie z. B. die Absenderadresse, über die Benutzeroberfläche festgelegt werden können.  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
    $emailXml = [xml]$emailCfg   
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = "your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = "your FROM email address"  
    Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  Wenn Sie den Namen Ihrer Dienstanwendung überprüfen müssen, führen Sie das Cmdlet **Get-SPRSServiceApplication**aus.  
  
    ```  
    get-sprsserviceapplication  
    ```  
  
3.  Im folgenden Beispiel wird der aktuelle Wert der E-Mail-Erweiterung für die Dienstanwendung mit dem Namen „SSRS_TESTAPPLICATION“ abgerufen.  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
    ```  
  
4.  Im folgenden Beispiel wird eine neue Datei mit dem Namen „emailconfig.txt“ mit den aktuellen Werten der E-Mail-Erweiterung für die Dienstanwendung mit dem Namen „SSRS_TESTAPPLICATION“ erstellt.  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml | out-file c:\emailconfig.txt  
    ```  
  
  
