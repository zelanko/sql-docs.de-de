---
title: SQL Server, Statistiken für das Broker-TO (Objekt) | Microsoft-Dokumentation
description: Hier lernen Sie das Leistungsobjekt „SQLServer:Statistiken für das Broker-TO“ kennen, das Informationen über Übertragungsobjekte von Service Broker-Anforderungen übermittelt.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: eabaa3854012b747e028babca44c749d1d51206e
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505834"
---
# <a name="sql-server-broker-to-statistics-object"></a>SQL Server, Statistiken für das Broker-TO (Objekt)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Das Leistungsobjekt „SQLServer:Statistiken für das Broker-TO“ übermittelt Informationen darüber, wie oft [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Dialoge Übertragungsobjekte anfordern, und wie oft Übertragungsobjekte in **tempdb** geschrieben werden.  
  
 Übertragungsobjekte zeichnen den Status von Nachrichtenübertragungen für einen [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Dialog auf. Sie werden im Arbeitsspeicher gespeichert. Um Arbeitsspeicher freizugeben, schreibt [!INCLUDE[ssSB](../../includes/sssb-md.md)] regelmäßig Batches inaktiver Übertragungsobjekte in Arbeitstabellen in **tempdb**.  
  
 In der folgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
|Leistungsindikatoren für "Statistiken für das Broker-TO" in SQL Server|BESCHREIBUNG|  
|----------------------------------------------|-----------------|  
|**Mittlere Länge der Batchschreibvorgänge**|Die durchschnittliche Anzahl von Übertragungsobjekten, die in einem Batch gespeichert wurden.|  
|**Mittlere Schreibdauer für Batch (ms)**|Die durchschnittliche Anzahl von Millisekunden, die zur Speicherung eines Batches von Übertragungsobjekten erforderlich waren.|  
|**Mittlere Basis für Schreibdauer für Batch**|Nur zur internen Verwendung.|
|**Mittlere Zeit zwischen Batches (ms)**|Die durchschnittliche Anzahl von Millisekunden, die zwischen Speicherungen der Batches von Übertragungsobjekten verstrichen sind.|  
|**Mittlere Basis für Zeit zwischen Batches**|Nur zur internen Verwendung.| 
|**Übertragungsobjektabrufe/Sekunde**|Gibt an, wie oft pro Sekunde Dialoge Übertragungsobjekte angefordert haben.|  
|**Pro Sekunde als geändert markierte Übertragungsobjekte**|Gibt an, wie oft pro Sekunde Übertragungsobjekte als geändert markiert wurden. Übertragungsobjekte werden als geändert markiert, sobald eine Bearbeitung bewirkt, dass sich die Kopie im Arbeitsspeicher von der in **tempdb** gespeicherten Kopie unterscheidet. Übertragungsobjekte werden geändert, wenn [!INCLUDE[ssSB](../../includes/sssb-md.md)] eine Änderung des Status von Nachrichtenübertragungen für einen Dialog aufzeichnen muss.|  
|**Schreibvorgänge für Übertragungsobjekte/Sekunde**|Gibt an, wie oft pro Sekunde Batches von Übertragungsobjekten in die **tempdb** -Arbeitstabellen geschrieben wurden. Ein große Anzahl von Schreibvorgängen kann darauf hinweisen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Arbeitsspeicher überbeansprucht wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server, Zugriffsmethoden-Objekt](../../relational-databases/performance-monitor/sql-server-access-methods-object.md)   
 [SQL Server, Speicher-Manager-Objekt](../../relational-databases/performance-monitor/sql-server-memory-manager-object.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
