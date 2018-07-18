---
title: DISCOVER_MEMORYGRANT-Rowset | Microsoft-Dokumentation
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
ms.assetid: d254e42d-9918-47ce-b6df-47f1f0b432dd
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3cae85df7e3c76afd9243771032f21f8f91861f7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229990"
---
# <a name="discovermemorygrant-rowset"></a>DISCOVER_MEMORYGRANT-Rowset
  Gibt eine Liste interner Arbeitsspeicherkontingent-Erteilungen zurück, die von Aufträgen in Anspruch genommen werden, die derzeit auf dem Server ausgeführt werden. Um festzustellen, ob ein Auftrag auf dem Server ausgeführt wird, verwenden Sie `Select * from $System.Discover_Jobs`.  
  
 **Gilt für:** tabellarische und mehrdimensionale Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_MEMORYGRANT` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Einschränkung|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`MEMORY_ID`|**DBTYPE_I8**||Eine Zahl, die die Arbeitsspeicherkontingent-Zuweisung identifiziert. Eindeutig innerhalb des Kontexts einer einzelnen DISCOVER_MEMORYGRANT-Anforderung.|  
|`SPID`|`DBTYPE_I4`|Required|Die SPID, die Sie erhalten können, indem Sie `Select * from $System.Discover_Sessions`ausführen.|  
|`CreationTime`|`DBTYPE_I8 DBTYPE_DBTIMESTAMP`||Die Uhrzeit, zu der das Kontingent zugewiesen wurde.|  
|`LastRequestTime`|**DBTYPE_DBTIMESTAMP**||Die Uhrzeit, zu der die Kontingentanforderung zuletzt geändert wurde.|  
|`MemoryUsed`|`DBTYPE_I4`||Der im Zusammenhang mit dem Kontingent verwendete Arbeitsspeicher.|  
|`MemoryGranted`|`DBTYPE_I4`||Der zur Verwendung durch den Auftrag, der das Arbeitsspeicherkontingent abruft, zugewiesene Arbeitsspeicher.|  
|`Blocked`|`DBTYPE_BOOL`||Ein boolescher Wert, der den Blockstatus des Auftrags angibt. True gibt an, dass der Auftrag blockiert wurde, bis ein anderer Auftrag genügend Kontingent freigibt, um seine Kontingentanforderung zu gewähren. False gibt an, dass der Auftrag sein Kontingent empfangen hat und ausgeführt werden kann.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|a07ccd23-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|MemoryGrant|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
