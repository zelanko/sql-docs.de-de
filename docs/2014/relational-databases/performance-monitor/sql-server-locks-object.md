---
title: SQL Server, Sperren-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Locks object
- SQLServer:Locks
ms.assetid: ace04f0d-3993-4444-8317-ca39d7087e49
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cd7773177f6ec9d02df9d3d669abf561919ffe0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250612"
---
# <a name="sql-server-locks-object"></a>SQL Server, Sperren-Objekt
  Das **SQLServer: Locks** -Objekt in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Microsoft stellt Informationen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu Sperren für einzelne Ressourcentypen bereit. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressourcen, wie etwa Zeilen, die während einer Transaktion gelesen oder geändert werden, werden mit Sperren belegt, um die zeitgleiche Verwendung der Ressourcen durch verschiedene Transaktionen zu verhindern. Wenn beispielsweise eine Zeile in einer Tabelle von einer Transaktion mit einer exklusiven Sperre (X) belegt wird, kann diese Zeile erst dann von einer anderen Transaktion geändert werden, wenn die Sperre aufgehoben wird. Durch die Reduzierung der Anzahl von Sperren kann die Parallelität erhöht werden, wodurch sich die Leistung verbessert. Es können mehrere Instanzen des **Sperren** -Objekts gleichzeitig überwacht werden, wobei jede Instanz eine Sperre für einen Ressourcentyp darstellt.  
  
 In dieser Tabelle werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Sperren** beschrieben.  
  
|Sperren-Leistungsindikatoren von SQL Server|BESCHREIBUNG|  
|-------------------------------|-----------------|  
|**Durchschnittliche Wartezeit (MS)**|Die durchschnittliche Länge der Wartezeit (in Millisekunden) für jede Sperranforderung, die nicht sofort erfüllt werden konnte.|  
|**Sperr Anforderungen/Sekunde**|Anzahl von neuen Sperren und Sperrkonvertierungen pro Sekunde, die vom Sperren-Manager angefordert wurden.|  
|**Sperr Timeouts (Timeout > 0)/Sek.**|Die Anzahl von Sperranforderungen pro Sekunde, für die ein Timeout eingetreten ist. Interne Anforderungen für NOWAIT-Sperren sind darin nicht eingeschlossen.|  
|**Sperr Timeouts/Sekunde**|Die Anzahl von Sperranforderungen pro Sekunde, für die ein Timeout eingetreten ist. Dies umfasst auch Anforderungen für NOWAIT-Sperren.|  
|**Sperr Wartezeit (MS)**|Gesamtwartezeit (in Millisekunden) für Sperren in der vergangenen Sekunde.|  
|**Sperr warte Vorgänge/Sek.**|Anzahl von Sperranforderungen pro Sekunde, bei denen der aufrufende Prozess warten musste.|  
|**Anzahl von Deadlocks/Sek.**|Anzahl von Sperranforderungen pro Sekunde, die zu einem Deadlock geführt haben.|  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann die folgenden Ressourcen sperren.  
  
|Element|BESCHREIBUNG|  
|----------|-----------------|  
|**_Total**|Informationen für alle Sperren.|  
|**Zuordnung**|Eine Sperre für eine Zuweisungseinheit.|  
|**Anwendung**|Eine Sperre für eine anwendungsspezifische Ressource.|  
|**Datenbank**|Eine Sperre für eine Datenbank, einschließlich aller Objekte in der Datenbank.|  
|**Ausdehnung**|Eine Sperre für eine zusammenhängende Gruppe von 8 Seiten.|  
|**Datei**|Eine Sperre für eine Datenbankdatei.|  
|**Heap/BTREE**|Heap oder BTree (HOBT). Eine Sperre für einen Heap von Datenseiten oder für die BTree-Struktur eines Indexes.|  
|**Schlüssel**|Eine Sperre für eine Zeile in einem Index.|  
|**Metadaten**|Eine Sperre für eine Kataloginformationskomponente, die auch als Metadaten bezeichnet wird.|  
|**Object**|Eine Sperre für eine Tabelle, gespeicherte Prozedur, Sicht usw., einschließlich aller Daten und Indizes. Hierbei kann es sich um ein beliebiges Objekt handeln, das einen Eintrag in **sys.all_objects**aufweist.|  
|**Seite**|Eine Sperre für eine 8-KB-Seite in einer Datenbank.|  
|**Gesagt**|Zeilen-ID. Eine Sperre für eine einzelne Zeile in einem Heap.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
