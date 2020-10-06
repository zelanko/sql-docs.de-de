---
description: RDS-Programmiermodell mit Objekten
title: RDS-Programmiermodell mit Objekten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS programming model [ADO]
- RDS objects [ADO]
ms.assetid: 07ce0ef0-72f1-48f4-823d-1b65d28c0926
author: rothja
ms.author: jroth
ms.openlocfilehash: 6ee41cabf8175bc7f2a34c0381193e406d33f38f
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724911"
---
# <a name="rds-programming-model-with-objects"></a>RDS-Programmiermodell mit Objekten
Das Ziel von RDS besteht darin, über einen Vermittler wie IIS auf Datenquellen zuzugreifen und diese zu aktualisieren. Das-Programmiermodell gibt die Abfolge der Aktivitäten an, die zum Erreichen dieses Ziels erforderlich sind. Das Objektmodell gibt die Objekte an, deren Methoden und Eigenschaften sich auf das Programmiermodell auswirken.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
 RDS bietet die Möglichkeit, die folgende Aktions Sequenz auszuführen:  
  
-   Geben Sie das Programm an, das auf dem Server aufgerufen werden soll, und rufen Sie eine Methode (Proxy) ab, mit der vom Client (RDS) darauf verwiesen wird[. DataSpace](../../reference/rds-api/dataspace-object-rds.md)).  
  
-   Rufen Sie das Serverprogramm auf. Übergeben Sie Parameter an das Serverprogramm, das die Datenquelle identifiziert, und den auszugebenden Befehl (Proxy oder [RDS). DataControl](../../reference/rds-api/datacontrol-object-rds.md)).  
  
-   Das Serverprogramm Ruft ein [Recordset](../../reference/ado-api/recordset-object-ado.md) -Objekt aus der Datenquelle ab, in der Regel mithilfe von ADO. Optional wird das **Recordset** -Objekt auf dem Server ([RDSServer. DataFactory](../../reference/rds-api/datafactory-object-rdsserver.md)) verarbeitet.  
  
-   Das Serverprogramm gibt das endgültige **Recordset** -Objekt an die Client Anwendung (Proxy) zurück.  
  
-   Auf dem Client wird das **Recordset** -Objekt in ein Formular eingefügt, das leicht von visuellen Steuerelementen (visuelles Steuerelement und RDS) verwendet werden kann **. DataControl**).  
  
-   Änderungen am **Recordset** -Objekt werden zurück an den Server gesendet und zum Aktualisieren der Datenquelle (RDS) verwendet **. DataControl** oder **RDSServer. DataFactory**).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zusammenfassung des RDS-Objektmodells](./rds-object-model-summary.md)   
 [DataControl-Objekt (RDS)](../../reference/rds-api/datacontrol-object-rds.md)   
 [DataFactory-Objekt (RDSServer)](../../reference/rds-api/datafactory-object-rdsserver.md)   
 [DataSpace-Objekt (RDS)](../../reference/rds-api/dataspace-object-rds.md)   
 [RDS-Szenario](./rds-scenario.md)   
 [RDS-Tutorial](./rds-tutorial.md)   
 [Recordset-Objekt (ADO)](../../reference/ado-api/recordset-object-ado.md)   
 [Verwendung und Sicherheit von RDS](./rds-usage-and-security.md)