---
title: DISCOVER_OBJECT_MEMORY_USAGE-Rowset | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_OBJECT_MEMORY_USAGE rowset
ms.assetid: 211cfa04-7bd6-43fe-8bd5-bfbff78bdafb
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ae1f26c1bc55c8aa080915a372710e4d59064979
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163224"
---
# <a name="discoverobjectmemoryusage-rowset"></a>DISCOVER_OBJECT_MEMORY_USAGE-Rowset
  Stellt Informationen über von Objekten verwendete Speicherressourcen bereit.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_OBJECT_MEMORY_USAGE` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`||Der Pfad zu dem übergeordneten Element des aktuellen Objekts.|  
|`OBJECT_ID`|`DBTYPE_WSTR`||Die ID des Objekts, die zur Erstellungszeit definiert wurde.|  
|`OBJECT_MEMORY_SHRINKABLE`|`DBTYPE_I8`||Die Gesamtmenge des von allen verkleinerbaren Objekten verwendeten Speichers (Bytes), die sich unmittelbar im Besitz des aktuellen Objekts befinden. Der aktuelle Wert beinhaltet keinen Speicher von Objekten, die sich im Besitz von benannten Objekten befinden, die sich wiederum im Besitz des aktuellen Objekts befinden.|  
|`OBJECT_MEMORY_NONSHRINKABLE`|`DBTYPE_I8`||Die Menge des von allen nicht verkleinerbaren Objekten verwendeten Speichers (Bytes), die sich unmittelbar im Besitz des aktuellen Objekts befinden. Der aktuelle Wert beinhaltet keinen Speicher von Objekten, die sich im Besitz von benannten Objekten befinden, die sich im Besitz des aktuellen Objekts befinden.|  
|`OBJECT_VERSION`|`DBTYPE_I4`||Die Metadatenversionsnummer des Objekts. Diese Nummer ändert sich jedes Mal, wenn das Objekt geändert wird.|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||Die Herkunftszahl der Daten in dem Objekt. Diese Zahl erhöht sich jedes Mal, wenn das Objekt verarbeitet wird.|  
|`OBJECT_TYPE_ID`|`DBTYPE_I4`||Für die interne Verwendung vorgesehen.|  
|`OBJECT_TIME_CREATED`|`DBTYPE_DBTIMESTAMP`||Die UTC-Serverzeit zum Zeitpunkt der Erstellung des Objekts.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_OBJECT_MEMORY_USAGE` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`|Optional.|  
|`OBJECT_ID`|`DBTYPE_WSTR`|Optional|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  