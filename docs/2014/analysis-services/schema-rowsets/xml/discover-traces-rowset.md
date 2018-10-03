---
title: DISCOVER_TRACES-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 1be6a035-ffc9-489e-9d4d-7391b3e384e2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 26d40f737db108ea2a9f8a9cee05f3ee9503c73c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168241"
---
# <a name="discovertraces-rowset"></a>DISCOVER_TRACES-Rowset
  Stellt Informationen über die derzeit aktiven Ablaufverfolgungen auf dem Server bereit.  
  
 **Gilt für:** tabellarische und mehrdimensionale Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_TRACES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Description|  
|-----------------|--------------------|-----------------|  
|`TraceID`|`DBTYPE_WSTR`|Die Ablaufverfolgungs-ID.|  
|`TraceName`|`DBTYPE_WSTR`|Der Ablaufverfolgungsname.|  
|`LogFileName`|`DBTYPE_WSTR`|Der Name der Ablaufverfolgungsprotokolldatei.|  
|`LogFileSize`|`DBTYPE_I4`|Die Größe der Ablaufverfolgungsprotokolldatei.|  
|`LogFileRollover`|`DBTYPE_BOOL`|true, um anzugeben, dass die Protokolldatei von neuem beginnen soll, andernfalls false.|  
|`AutoRestart`|`DBTYPE_BOOL`|true, um anzugeben, dass die automatische Neustartoption aktiviert ist; andernfalls false.|  
|`CreationTime`|`DBTYPE_TIME`|Datum und Uhrzeit der Erstellung der Ablaufverfolgung.|  
|`StopTime`|`DBTYPE_TIME`|Beendigungszeit der Ablaufverfolgung.|  
|`Type`|`PF_DBTYPE_WSTR`|Der Typ der Ablaufverfolgung.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_TRACES` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**TraceId**|`DBTYPE_I4`|Optional.|  
|`Type`|WSTR|Optional.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|a07ccd1a-8148-11d0-87bb-00c04fc33942|  
|Zeichenfolge|DISCOVER_TRACES|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
