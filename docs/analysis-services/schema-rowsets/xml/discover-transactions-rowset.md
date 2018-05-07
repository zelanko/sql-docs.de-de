---
title: DISCOVER_TRANSACTIONS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4084d4a964a901c7f4fc78114f596ef9d6708dc3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="discovertransactions-rowset"></a>DISCOVER_TRANSACTIONS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt den aktuellen Satz von ausstehenden Transaktionen auf dem System zurück.  
  
 **Gilt für:** tabellarische und mehrdimensionale Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_TRANSACTIONS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Description|  
|-----------------|--------------------|-----------------|  
|**TRANSACTION_ID**|**DBTYPE_WSTR**|Der eindeutige Bezeichner der Transaktion als GUID.|  
|**TRANSACTION_SESSION_ID**|**DBTYPE_WSTR**|Die eindeutige Sitzungs-ID der Transaktion als GUID.|  
|**TRANSACTION_START_TIME**|**DBTYPE_DBTIMESTAMP**|UTC-Datum und -Zeit des Servers, zu denen die Transaktion gestartet wurde.|  
|**TRANSACTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|Die seit dem Start der Transaktion verstrichene Zeit in Millisekunden.|  
|**TRANSACTION_CPU_TIME_MS**|**DBTYPE_I8**|Die CPU-Zeit in Millisekunden, die seit dem Beginn der Transaktion von allen Anforderungen beansprucht wurde.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_TRANSACTIONS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|**Spaltenname**|**Typindikator**|**Einschränkungsstatus**|  
|---------------------|------------------------|---------------------------|  
|**ID**|**DBTYPE_WSTR**|Optional.|  
|**SESSION_ID**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|Wert|  
|--------------|-----------|  
|GUID|a07ccd28-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRANSACTIONS|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
