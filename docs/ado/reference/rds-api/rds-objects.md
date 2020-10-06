---
description: RDS-Objekte
title: RDS-Objekte | Microsoft-Dokumentation
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- objects [ADO], RDS
- RDS objects [ADO]
ms.assetid: f2ac8b3b-f968-41c4-a504-7aee3538b7c7
author: rothja
ms.author: jroth
ms.openlocfilehash: fa9329b1da84643f75a83ee1487f8c1be47601b1
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724341"
---
# <a name="rds-objects"></a>RDS-Objekte
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
|Object|BESCHREIBUNG|  
|-|-|  
|[DataControl (RDS)](./datacontrol-object-rds.md)|Bindet ein Datenabfrage- **Recordset** an ein oder mehrere Steuerelemente (z. b. ein Textfeld, ein Raster Steuerelement oder ein Kombinations Feld), um die **Recordsetdaten** auf einer Webseite anzuzeigen.<br /><br /> Das **DataControl** -Objekt ist für die Skripterstellung sicher.|  
|[DataFactory (RDSServer)](./datafactory-object-rdsserver.md)|Implementiert Methoden, die Lese-/Schreibdaten Zugriff auf angegebene Datenquellen für Client seitige Anwendungen bereitstellen.<br /><br /> Das **DataFactory** -Objekt ist für die Skripterstellung nicht sicher.|  
|[DataSpace (RDS)](./dataspace-object-rds.md)|Erstellt Client seitige Proxys für benutzerdefinierte Geschäftsobjekte auf der mittleren Ebene.<br /><br /> Das **DataSpace** -Objekt ist für die Skripterstellung sicher.|  
|[IRDSService-Schnittstelle (RDS)](./irdsservice-interface-rds.md)|Macht die [invokeservice (RDS)](./invokeservice-rds.md) -Methode verfügbar, die verwendet wird, um einen Zeiger auf die angeforderte Schnittstelle auf einer leistungsfähigeren Version des-Objekts zurückzugeben.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [RDS-API-Referenz](./rds-api-reference.md)