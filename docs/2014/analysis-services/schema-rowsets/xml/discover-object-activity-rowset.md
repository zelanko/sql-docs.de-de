---
title: DISCOVER_OBJECT_ACTIVITY-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DISCOVER_OBJECT_ACTIVITY rowset
ms.assetid: 100f7de1-ad5c-4973-b863-3c10df1245c4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8222ba19948adcd65090bfcccaa75b3ddd49a55d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120700"
---
# <a name="discoverobjectactivity-rowset"></a>DISCOVER_OBJECT_ACTIVITY-Rowset
  Stellt die Ressourcenverwendung pro Objekt seit dem Start des Diensts bereit.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_OBJECT_ACTIVITY` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`OBJECT_AGGREGATION_HIT`|`DBTYPE_I8`||Die Häufigkeit, mit der eine Aggregation des Objekts seit dem Start des Diensts getroffen wurde.|  
|`OBJECT_AGGREGATION_MISS`|`DBTYPE_I8`||Die Häufigkeit, mit der eine vorhandene Aggregation des Objekts seit dem Start des Diensts erkannt (d. h. nicht verwendet) wurde.|  
|`OBJECT_CPU_TIME_MS`|`DBTYPE_I8`||Die CPU-Zeit in Millisekunden, die seit dem Beginn des Diensts von dem Objekt beansprucht wurde.|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||Die Herkunftszahl der Daten in dem Objekt, diese Zahl nimmt jedes Mal zu, wenn das Objekt verarbeitet wird.|  
|`OBJECT_HIT`|`DBTYPE_I8`||Die Häufigkeit, mit der das Objekt im Cache seit dem Start des Diensts getroffen wurde.|  
|`OBJECT_ID`|`DBTYPE_WSTR`||Die ID des Objekts, die zur Erstellungszeit definiert wurde.|  
|`OBJECT_MISS`|`DBTYPE_I8`||Die Häufigkeit, mit der das Objekt im Cache seit dem Start des Diensts nicht erkannt wurde.|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`||Der Pfad zu dem übergeordneten Element des aktuellen Objekts.|  
|`OBJECT_READ_KB`|`DBTYPE_I8`||Der akkumulierte Wert der seit dem Start des Diensts von dem Objekt gelesenen Daten in KB.|  
|`OBJECT_READS`|`DBTYPE_I8`||Die akkumulierte Zahl der seit dem Start des Diensts von dem Objekt ausgeführten Lesevorgänge.|  
|`OBJECT_ROWS_RETURNED`|`DBTYPE_I8`||Die Anzahl der seit dem Start des Diensts von dem Objekt an den Aufrufer zurückgegebenen Zeilen.|  
|`OBJECT_ROWS_SCANNED`|`DBTYPE_I8`||Die Anzahl der seit dem Start des Diensts von dem Objekt gescannten Zeilen.|  
|`OBJECT_VERSION`|`DBTYPE_I4`||Die Metadatenversionsnummer des Objekts, diese Nummer ändert sich jedes Mal, wenn das Objekt geändert wird.|  
|`OBJECT_WRITE_KB`|`DBTYPE_I8`||Der akkumulierte Wert der seit dem Start des Diensts von dem Objekt geschriebenen Daten in KB.|  
|`OBJECT_WRITES`|`DBTYPE_I8`||Die akkumulierte Zahl der seit dem Start des Diensts von dem Objekt ausgeführten Schreibvorgänge.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_OBJECT_ACTIVTY` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|OBJECT_PARENT_PATH|DBTYPE_WSTR|Optional.|  
|OBJECT_ID|DBTYPE_WSTR|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
