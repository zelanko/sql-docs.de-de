---
title: RDS-Programmiermodell mit Objekten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS programming model [ADO]
- RDS objects [ADO]
ms.assetid: 07ce0ef0-72f1-48f4-823d-1b65d28c0926
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e499503541449d35cf17ded36c8a7e358518680
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737229"
---
# <a name="rds-programming-model-with-objects"></a>RDS-Programmiermodell mit Objekten
Das Ziel von RDS ist zum Zugreifen auf und Aktualisieren von Datenquellen über einen Vermittler, z. B. IIS. Das Programmiermodell gibt an, die Abfolge von Aktivitäten erforderlich, dieses Ziel zu erreichen. Das Objektmodell gibt an, die Objekte, deren Methoden und Eigenschaften das Programmiermodell beeinflussen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 RDS bietet die Möglichkeit, die folgende Sequenz von Aktionen ausführen:  
  
-   Geben Sie das Programm auf dem Server aufgerufen werden, und rufen Sie eine Möglichkeit (Proxy) vom Client darauf verweisen ([RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)).  
  
-   Serverprogramm aufrufen. Übergeben von Parametern an die Server-Anwendung, die die Datenquelle und den Befehl, um das Problem identifiziert (Proxy oder [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)).  
  
-   Das Serverprogramm erhält eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt aus der Datenquelle, in der Regel mithilfe von ADO. Optional können die **Recordset** Objekt wird auf dem Server verarbeitet ([RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)).  
  
-   Serverprogramm gibt zurück, die endgültige **Recordset** Objekt an die Clientanwendung (Proxy).  
  
-   Auf dem Client die **Recordset** Objekt abgelegt eines Formulars, das leicht von visuellen Steuerelementen verwendet werden kann (visuelles Steuerelement und **RDS. DataControl**).  
  
-   Änderungen an der **Recordset** Objekt wieder an den Server gesendet und zum Aktualisieren der Datenquelle verwendet werden (**RDS. DataControl** oder **RDSServer.DataFactory**).  
  
## <a name="see-also"></a>Siehe auch  
 [RDS-Modell: Zusammenfassung](../../../ado/guide/remote-data-service/rds-object-model-summary.md)   
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [DataSpace-Objekt (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [RDS-Architektur](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Verwendung und Sicherheit von RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


