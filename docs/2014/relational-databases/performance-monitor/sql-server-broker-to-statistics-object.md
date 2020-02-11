---
title: SQL Server, Statistiken für das Broker-TO (Objekt) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1a8c5bc039e4e6c18680ba4e290ea7e69fa87804
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250783"
---
# <a name="sql-server-broker-to-statistics-object"></a>SQL Server, Statistiken für das Broker-TO (Objekt)
  Das Leistungsobjekt „SQLServer:Statistiken für das Broker-TO“ übermittelt Informationen darüber, wie oft [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Dialoge Übertragungsobjekte anfordern und wie oft Übertragungsobjekte in **tempdb**geschrieben werden.  
  
 Übertragungsobjekte zeichnen den Status von Nachrichtenübertragungen für einen [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Dialog auf. Sie werden im Arbeitsspeicher gespeichert. Um Arbeitsspeicher freizugeben, schreibt [!INCLUDE[ssSB](../../includes/sssb-md.md)] regelmäßig Batches inaktiver Übertragungsobjekte in Arbeitstabellen in **tempdb**.  
  
 In der folgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
|Leistungsindikatoren für "Statistiken für das Broker-TO" in SQL Server|Beschreibung|  
|----------------------------------------------|-----------------|  
|**Mittlere Länge der Batchschreibvorgänge**|Die durchschnittliche Anzahl von Übertragungsobjekten, die in einem Batch gespeichert wurden.|  
|**Mittlere Schreibdauer für Batch (ms)**|Die durchschnittliche Anzahl von Millisekunden, die zur Speicherung eines Batches von Übertragungsobjekten erforderlich waren.|  
|**Durschnittliche Zeit zwischen Batches (ms)**|Die durchschnittliche Anzahl von Millisekunden, die zwischen Speicherungen der Batches von Übertragungsobjekten verstrichen sind.|  
|**Tran-Objekt abruft/Sekunde**|Gibt an, wie oft pro Sekunde Dialoge Übertragungsobjekte angefordert haben.|  
|**Als geändert markierte Tran-Objekte/Sek.**|Gibt an, wie oft pro Sekunde Übertragungsobjekte als geändert markiert wurden. Übertragungsobjekte werden als geändert markiert, sobald eine Bearbeitung bewirkt, dass sich die Kopie im Arbeitsspeicher von der in **tempdb**gespeicherten Kopie unterscheidet. Übertragungsobjekte werden geändert, wenn [!INCLUDE[ssSB](../../includes/sssb-md.md)] eine Änderung des Status von Nachrichtenübertragungen für einen Dialog aufzeichnen muss.|  
|**Tran-Objekt Schreibvorgänge/Sek.**|Gibt an, wie oft pro Sekunde Batches von Übertragungsobjekten in die **tempdb** -Arbeitstabellen geschrieben wurden. Ein große Anzahl von Schreibvorgängen kann darauf hinweisen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Arbeitsspeicher überbeansprucht wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server, Zugriffsmethoden-Objekt](sql-server-access-methods-object.md)   
 [SQL Server, Speicher-Manager-Objekt](sql-server-memory-manager-object.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
