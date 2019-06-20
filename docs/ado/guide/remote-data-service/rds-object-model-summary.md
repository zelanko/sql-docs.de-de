---
title: RDS-Objekt Modellzusammenfassung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 434c27f5e2da0208ba5141664ccc69accfc2fbb2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704248"
---
# <a name="rds-object-model-summary"></a>Zusammenfassung zum RDS-Objektmodell
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Objekt|Description|  
|------------|-----------------|  
|[RDS.DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)|Dieses Objekt enthält eine Methode zum Abrufen eines Server-Proxys. Der Proxy kann es sich um die Standardeinstellung oder benutzerdefinierte Serverprogramm (Business-Objekt) sein. Des Programms aufgerufen werden kann, auf das Internet, Intranet, einem lokalen Netzwerk oder eine lokale Dynamic-Link Library sein.<br /><br /> Die **DataSpace** Objekt für die Skripterstellung sicher ist.|  
|[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Dieses Objekt stellt das Standardprogramm für den Server dar. Dadurch wird das standardmäßige RDS Daten abrufen und aktualisieren Verhalten ausgeführt.<br /><br /> Die **DataFactory** Objekt ist nicht sicher für Skripting.|  
|[RDS.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Dieses Objekt kann automatisch aufrufen, die **RDS. DataSpace** und **RDSServer.DataFactory** Objekte.<br /><br /> Verwenden Sie dieses Objekt, um das standardmäßige Verhalten von RDS-Daten abrufen "oder" Update aufzurufen.<br /><br /> Dieses Objekt stellt auch die Möglichkeiten für visuelle Steuerelemente auf die zurückgegebene **Recordset** Objekt.<br /><br /> Die **DataControl** Objekt für die Skripterstellung sicher ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [RDS-Architektur](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Verwendung und Sicherheit von RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


