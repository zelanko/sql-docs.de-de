---
description: Zusammenfassung zum RDS-Objektmodell
title: Zusammenfassung des RDS-Objektmodells | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
author: rothja
ms.author: jroth
ms.openlocfilehash: d7488811326dda4228ef2f458b70d5575b33b122
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452142"
---
# <a name="rds-object-model-summary"></a>Zusammenfassung zum RDS-Objektmodell
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
|Object|Beschreibung|  
|------------|-----------------|  
|[RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)|Dieses Objekt enthält eine Methode zum Abrufen eines Server Proxys. Bei dem Proxy kann es sich um das Standard-oder ein benutzerdefiniertes Serverprogramm (Geschäftsobjekt) handeln. Das Serverprogramm kann über das Internet, ein Intranet, ein lokales Netzwerk oder eine lokale Dynamic Link Library aufgerufen werden.<br /><br /> Das **DataSpace** -Objekt ist für die Skripterstellung sicher.|  
|[RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Dieses Objekt stellt das standardmäßige Serverprogramm dar. Er führt den standardmäßigen RDS-Datenabruf und das Aktualisierungs Verhalten aus.<br /><br /> Das **DataFactory** -Objekt ist für die Skripterstellung nicht sicher.|  
|[RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Dieses Objekt kann das RDS automatisch aufrufen **. DataSpace** -und **RDSServer. DataFactory** -Objekte.<br /><br /> Verwenden Sie dieses Objekt, um das standardmäßige RDS-Datenabruf-oder Update Verhalten aufzurufen.<br /><br /> Dieses Objekt bietet auch die Möglichkeit, dass visuelle Steuerelemente auf das zurückgegebene **Recordset** -Objekt zugreifen können.<br /><br /> Das **DataControl** -Objekt ist für die Skripterstellung sicher.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [RDS-Grundlagen](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [RDS-Szenario](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Verwendung und Sicherheit von RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


