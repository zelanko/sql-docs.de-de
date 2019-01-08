---
title: Beispiel für eine Konfiguration mit Mindestberechtigungen für PowerPivot für SharePoint 2013 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: c1e09e6c-52d3-48ab-8c70-818d5d775087
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b79b9c6662b40b860cfacd85d77b09dbfb04117d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53368392"
---
# <a name="example-of-a-minimum-privilege-configuration-for-powerpivot-for-sharepoint-2013"></a>Beispiel für eine PowerPivot für SharePoint 2013-Konfiguration mit Mindestberechtigungen
  In diesem Thema wird eine PowerPivot für SharePoint 2013-Konfiguration mit Mindestberechtigungen anhand eines Beispiels veranschaulicht. Bei der Konfiguration wird für jede der drei Komponenten ein anderes Konto verwendet, von denen jedes über Mindestberechtigungen verfügt.  
  
## <a name="summary-of-accounts"></a>Übersicht der Konten  
 PowerPivot für SharePoint 2013 unterstützt die Verwendung des Netzwerkdienstkontos für das Analysis Services-Dienstkonto. Das Netzwerkdienstkonto ist kein unterstütztes Szenario unter SharePoint 2010. Weitere Informationen zu Dienstkonten finden Sie unter [konfigurieren Windows-Dienstkonten und-Berechtigungen](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) (https://msdn.microsoft.com/library/ms143504.aspx).  
  
 In der folgenden Tabelle werden die Eigenschaften der drei Konten zusammengefasst, die in diesem Beispiel für eine Konfiguration mit Mindestberechtigungen verwendet werden.  
  
|Bereich|Name|  
|-----------|----------|  
|SharePoint-Administratorkonto|**SPAdmin**|  
|SharePoint-Farmkonto|**SPFarm**|  
|Analysis Services-Dienstkonto|**SPsvc**|  
  
### <a name="the-sharepoint-administrator-account-spadmin"></a>Das SharePoint-Administratorkonto (SpAdmin)  
 **SPAdmin** ist ein Domänenkonto, das Sie zum Installieren und Konfigurieren der Farm verwenden. Konto zum Ausführen von den SharePoint-Konfigurations-Assistenten und das PowerPivot-Konfigurationstool für SharePoint 2013 **SPAdmin** Konto ist das einzige Konto, das lokale Administratorrechte erforderlich sind. Vor dem Ausführen des PowerPivot-Konfigurationstools, die **SPAdmin** -Konto Berechtigungen für die SQL Server-Datenbankinstanz, auf SharePoint Inhalts- und Konfigurationsdatenbanken einrichtet. Damit Sie das SPAdmin-Konto in einem Szenario mit Mindestberechtigungen konfigurieren können, muss es Mitglied in den Rollen **securityadmin** und **dbcreator**sein.  
  
### <a name="the-farm-account-spfarm"></a>Das Farmkonto (SPFarm)  
 **SPFarm** ist ein Domänenkonto, das der SharePoint-Timerdienst und die Webanwendung der Zentraladministration für den Zugriff auf die SharePoint-Inhaltsdatenbank verwenden. Dieses Konto muss nicht als lokaler Administrator eingerichtet sein. Der SharePoint-Konfigurations-Assistent gewährt die entsprechenden Mindestberechtigungen in der SQL Server-Back-End-Datenbank. Die Mindestberechtigung für die SQL Server-Konfiguration ist die Mitgliedschaft in den Rollen **securityadmin** und **dbcreator**.  
  
### <a name="the-service-account-for-powerpivot-service-spsvc"></a>Das Dienstkonto für den PowerPivot-Dienst (SPsvc)  
 Wenn eine neue SharePoint-Farm vor dem Ausführen des PowerPivot-Konfigurationstools noch nicht konfiguriert wurde, werden standardmäßig folgende Anwendungen vom PowerPivot-Konfigurationstool erstellt:  
  
-   PowerPivot-Service-Anwendung.  
  
-   Excel Services-Anwendung  
  
-   Secure Storage-Anwendung  
  
 Das PowerPivot-Konfigurationstool konfiguriert alle drei Dienstanwendungen im Standardanwendungspool. Dieser Anwendungspool ist normalerweise für die Ausführung als SPFarm-Konto konfiguriert, das Zugriff auf viele Ressourcen hat, die von einem Dienstkonto jedoch nicht benötigt werden. Um eine Umgebung mit Mindestberechtigungen zu erhalten, konfigurieren Sie ein neues Domänenkonto, das vom betreffenden Anwendungspool und der betreffenden Webanwendung verwendet wird.  
  
 **So erstellen Sie ein neues SPsvc-Domänenkonto, das als SharePoint-Dienstkonto verwendet werden soll**  
  
1.  Klicken Sie im SharePoint-Zentraladministration auf **Sicherheit**.  
  
2.  Klicken Sie auf **Dienstkonten konfigurieren**  
  
3.  Klicken Sie auf **neues verwaltetes Konto registrieren**.  
  
 Das **SPSvc** -Konto verfügt über keine lokalen Administratorberechtigungen, und SPsvc verfügt über keine Berechtigungen in der SharePoint-Datenbank. Die einzigen Berechtigungen, die SPsvc erfordert, sind Administratorrechte für die PowerPivot-Instanz von Analysis Services.  
  
 **So konfigurieren Sie den entsprechenden Anwendungspool für die Verwendung des SPsvc-Kontos**  
  
1.  Klicken Sie im SharePoint-Zentraladministration auf **Sicherheit**.  
  
2.  Klicken Sie auf **Dienstkonten konfigurieren**.  
  
3.  Wählen Sie den von der PowerPivot-Dienstanwendung verwendeten Dienstanwendungspool aus. Wählen Sie dann das SPSvc-Konto aus.  
  
 **So gewähren Sie Zugriff auf die Webanwendung mit PowerShell**  
  
1.  Führen Sie die SharePoint 2013-Verwaltungsshell mit Administratorberechtigungen aus.  
  
2.  Führen Sie den folgenden PowerShell-Code aus:  
  
    ```  
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")  
  
    ```  
  
  
