---
title: DISCOVER_TRACE_COLUMNS-Rowset | Microsoft-Dokumentation
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
ms.assetid: 02baf401-52b0-4a73-8a7b-3b5b5e568626
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f07c4d548022ae12ab44e9c2772c13a0ffff574
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210020"
---
# <a name="discovertracecolumns-rowset"></a>DISCOVER_TRACE_COLUMNS-Rowset
  Gibt ein XML-Dokument mit einer Beschreibung der in einer Ablaufverfolgung verfügbaren Spalten zurück.  
  
 **Gilt für:** tabellarische und mehrdimensionale Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_TRACE_COLUMNS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Einschränkung|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`Data`|`DBTYPE_WSTR`|ja|Enthält eine codierte XML-Zeichenfolge, die Informationen zu den Ablaufverfolgungsspalten beschreibt, die vom Ablaufverfolgungsanbieter bereitgestellt wurden.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|a07ccd18-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|TraceColumns|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
