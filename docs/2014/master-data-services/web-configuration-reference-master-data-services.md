---
title: Webkonfigurationsverweis (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ee3582e7de37b99cd7f665f563e789259954b722
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65478485"
---
# <a name="web-configuration-reference-master-data-services"></a>Webkonfigurationsreferenz (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] benutzt die Datei „Web.config“, die die Konfigurationseinstellungen enthält, die Internetinformationsdienste (IIS) aktivieren, um die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung und den entsprechenden Webdienst zu hosten. Diese Datei Web.config Datei befindet sich im Ordner WebApplication des [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Installationspfads. Weitere Informationen zu Pfaden und Berechtigungen finden Sie unter [Ordner- und Dateiberechtigungen &#40;Master Data Services&#41;](folder-and-file-permissions-master-data-services.md).  
  
## <a name="webconfig-elements"></a>Web.Config-Elemente  
 Die Datei „Web.config“ enthält zusätzlich zu den Konfigurationselementen Standard-IIS, .NET Framework, ASP.NET und Windows Communication Foundation (WCF) ein benutzerdefiniertes [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Element, und zwar **\<masterDataServices>**. Die folgende Tabelle beschreibt die Elemente mit den enthaltenen Web.config-Dateien.  
  
|Konfigurationselement|Description|  
|---------------------------|-----------------|  
|`masterDataServices`|Benutzerdefiniertes Element. Verbindet den [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Web-Service mit einer [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank.|  
|`connectionStrings`|ASP.NET-Element. Weitere Informationen finden Sie unter [connectionStrings-Element (ASP.NET-Einstellungsschema)](https://go.microsoft.com/fwlink/?LinkId=178347) in der MSDN Library.|  
|`system.web`|ASP.NET-Element. Weitere Informationen finden Sie unter [system.web-Element (ASP.NET-Einstellungsschema)](https://go.microsoft.com/fwlink/?LinkId=178348) in der MSDN Library.|  
|`startup`|.NET Framework-Element. Weitere Informationen finden Sie unter [\<startup>-Element](https://go.microsoft.com/fwlink/?LinkId=178349) in der MSDN-Bibliothek.|  
|`runtime`|.NET Framework-Element. Weitere Informationen finden Sie unter [\<runtime>-Element](https://go.microsoft.com/fwlink/?LinkId=178350) in der MSDN-Bibliothek.|  
|`system.codedom`|.NET Framework-Element. Weitere Informationen finden Sie unter [\<system.codedom>-Element](https://go.microsoft.com/fwlink/?LinkId=178351) in der MSDN-Bibliothek.|  
|`system.web.extensions`|ASP.NET-Element. Weitere Informationen finden Sie unter [system.web.extensions-Element (ASP.NET-Einstellungsschema)](https://go.microsoft.com/fwlink/?LinkId=178352) in der MSDN Library.|  
|`system.webServer`|Abschnittsgruppe, die IIS-Elemente enthält. Weitere Informationen finden Sie unter [system.webServer Section Group \[IIS 7 Settings Schema\]](https://go.microsoft.com/fwlink/?LinkId=178353) (Abschnittsgruppe „system.webServer“ [IIS 7-Einstellungsschema]) in der MSDN Library.|  
|`system.serviceModel`|WCF-Element. Weitere Informationen finden Sie unter [\<system.serviceModel>](https://go.microsoft.com/fwlink/?LinkId=178354) in der MSDN-Bibliothek.|  
|`system.diagnostics`|.NET Framework-Element. Weitere Informationen finden Sie unter [\<system.diagnostics>-Element](https://go.microsoft.com/fwlink/?LinkId=178355) in der MSDN-Bibliothek.|  
|`appSettings`|ASP.NET-Element. Weitere Informationen finden Sie unter [appSettings-Element (allgemeines Einstellungsschema)](https://go.microsoft.com/fwlink/?LinkId=178356) in der MSDN Library.|  
  
## <a name="masterdataservices-element"></a>masterDataServices-Element  
 Das **\<masterDataServices>**-Element ist ein benutzerdefiniertes Element, das verwendet wird, um einen [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Webdienst mit einer [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Datenbank zu verbinden.  
  
### <a name="syntax"></a>Syntax  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a>Elemente und Attribute  
  
|Element|Description|  
|----------|-----------------|  
|`instance`|Untergeordnetes Element. Enthält Attribute, die Informationen für den Webdienst und Datenbankverbindungszeichenfolge angeben.|  
|`virtualPath`|Attribute. Gibt den virtuellen Pfad der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung und des entsprechenden Diensts an. Dies entspricht der `path` Attribut der  **\<Anwendung >** Element unter den  **\<Standort >** Element in der IIS ApplicationHost.config-Datei.|  
|`siteName`|Attribute. Gibt den Namen der Website an, die die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung und den entsprechenden Dienst hostet. Dies entspricht der `name` Attribut der  **\<Site >** Element unter  **\<Standorte >** in der IIS ApplicationHost.config-Datei.|  
|`connectionName`|Attribute. Gibt den Namen der zu verwendeten Verbindung an. Dies entspricht der `name` Attribut der  **\<hinzufügen >** Element unter den  **\<ConnectionStrings >** Element in "Web.config".|  
|`serviceName`|Attribute. Gibt den Namen des Web-Services an. Dies entspricht der `name` Attribut der  **\<Service >** Element unter der  **\<Services >** Element in "Web.config".|  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Dienst mit dem Namen MDS1 auf der Contoso-Website veranschaulicht und /MDs-Pfad, der eine von MDSDB angegebene Verbindungszeichenfolge verwendet.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
