---
title: Datenbankkonfiguration (Seite im Konfigurations-Manager für Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.dbpg.f1
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7f5f11ba4154b70c5aa1fd0ae0e7579c746ce744
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483185"
---
# <a name="database-configuration-page-master-data-services-configuration-manager"></a>Datenbankkonfiguration (Seite im Konfigurations-Manager für Master Data Services)
  Verwenden Sie die Seite **Datenbankkonfiguration** , um Systemeinstellungen einer [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank zu bearbeiten. Systemeinstellungen wirken sich auf alle Webanwendungen und Webdienste aus, die der ausgewählten [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank zugewiesen sind. Sie müssen eine [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank auswählen oder erstellen, damit Systemeinstellungen aktiviert und zur Konfiguration verfügbar sind.  
  
## <a name="current-database"></a>Aktuelle Datenbank  
 Wählen Sie eine vorhandene [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank aus, oder erstellen Sie eine neue Datenbank, deren Systemeinstellungen Sie bearbeiten. Die neue Datenbank ist nach der Erstellung ausgewählt.  
  
|Steuerelementname|BESCHREIBUNG|  
|------------------|-----------------|  
|**SQL Server Instanz**|Zeigt den Namen der ausgewählten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz an. Dieses Feld bleibt so lange leer, bis Sie eine Verbindung mit einer Instanz herstellen und dann eine [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank auswählen oder erstellen.|  
|**Master Data Services Datenbank**|Zeigt den Namen der ausgewählten [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank an. Dieses Feld bleibt so lange leer, bis Sie eine Verbindung mit einer Instanz herstellen und dann eine [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank auswählen oder erstellen.|  
|**Master Data Services-Datenbankversion**|Die Version des [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbankschemas.|  
|**Datenbank erstellen**|Öffnet den Assistenten **Datenbank erstellen** , von dem aus Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz herstellen und eine [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank für diese Instanz erstellen.|  
|**Datenbank auswählen**|Öffnet das Dialogfeld **Verbindung mit Datenbank herstellen** , in dem Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz herstellen und eine [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank auswählen.|  
|**Datenbank aktualisieren**|Öffnet einen Assistenten, in dem Sie eine angegebene [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank aktualisieren können. Diese Schaltfläche ist nur aktiviert, wenn die angegebene Datenbank ein Upgrade erfordert.|  
|**Datenbank reparieren**|Klicken Sie auf diese Schaltfläche, um sicherzustellen, dass die MDS-Datenbank ordnungsgemäß installiert ist. Dies kann nützlich sein, wenn Sie eine MDS-Datenbank in einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz sichern und wiederherstellen, die nie eine MDS-Datenbank gehostet hat.|  
  
## <a name="system-settings"></a>Systemeinstellungen  
 Bearbeiten Sie Systemeinstellungen für alle Webanwendungen und Webdienste, die der ausgewählten [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank zugeordnet sind.  
  
 Diese Einstellungen sind in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] verfügbar und werden in der Datenbank in der Tabelle Systemeinstellungen (mdm.tblSystemSetting) gespeichert. Eine Liste mit allen Einstellungen finden Sie unter [Systemeinstellungen &#40;Master Data Services&#41;](system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einrichten der Datenbank und Website für Master Data Services](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [Datenbankanforderungen &#40;Master Data Services&#41;](install-windows/database-requirements-master-data-services.md)  
  
  
