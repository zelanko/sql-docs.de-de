---
title: DISCOVER_COMMAND_OBJECTS-Rowset | Microsoft Docs
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
- DISCOVER_COMMAND_OBJECTS rowset
ms.assetid: 325114ee-3a50-4504-9782-dbf7c1a44778
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c53fccdecc824bd123312a881c1ddcdbcae6060a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060828"
---
# <a name="discovercommandobjects-rowset"></a>DISCOVER_COMMAND_OBJECTS-Rowset
  Stellt Ressourcenverwendungs- und Aktivitätsinformationen über die Objekte bereit, die durch den Befehl, auf den verwiesen wird, verwendet werden.  
  
 **Gilt für:** tabellarische und mehrdimensionale Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_COMMAND_OBJECTS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Einschränkung|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`SESSION_SPID`|`DBTYPE_I4`|ja|Die Sitzungs-ID.|  
|`SESSION_ID`|`DBTYPE_WSTR`|ja|Die eindeutige Sitzungs-ID als GUID.|  
|`SESSION_COMMAND_COUNT`|`DBTYPE_I4`||Die Sequenznummer des Befehls.|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`|ja|Der Pfad zu dem übergeordneten Element des aktuellen Objekts.|  
|`OBJECT_ID`|`DBTYPE_WSTR`|ja|Die ID des Objekts, die bei dessen Erstellung definiert wurde.|  
|`OBJECT_VERSION`|`DBTYPE_I4`||Die Metadatenversionsnummer des Objekts, diese Nummer ändert sich jedes Mal, wenn das Objekt geändert wird.|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||Die Herkunftszahl der Daten in dem Objekt. Diese Zahl erhöht sich jedes Mal, wenn das Objekt verarbeitet wird.|  
|`OBJECT_CPU_TIME_MS`|`DBTYPE_I8`||Die CPU-Zeit in Millisekunden, die seit dem Start des Befehls vom Objekt beansprucht wurde.|  
|`OBJECT_READ_KB`|`DBTYPE_I8`||Der akkumulierte Wert der seit dem Start des Befehls von dem Objekt gelesenen Daten in KB.|  
|`OBJECT_READS`|`DBTYPE_I8`||Die akkumulierte Zahl der seit dem Start des Befehls von dem Objekt ausgeführten Lesevorgänge.|  
|`OBJECT_WRITE_KB`|`DBTYPE_I8`||Der akkumulierte Wert der seit dem Start des Befehls von dem Objekt geschriebenen Daten in KB.|  
|`OBJECT_WRITES`|`DBTYPE_I8`||Die akkumulierte Zahl der seit dem Start des Befehls von dem Objekt ausgeführten Schreibvorgänge.|  
|`OBJECT_ROWS_RETURNED`|`DBTYPE_I8`||Die Anzahl der seit dem Start des Befehls von dem Objekt an den Aufrufer zurückgegebenen Zeilen.|  
|`OBJECT_ROWS_SCANNED`|`DBTYPE_I8`||Die Anzahl der seit dem Start des Befehls von dem Objekt gescannten Zeilen.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
> [!IMPORTANT]  
>  Das DISCOVER_COMMAND_OBJECTS-Schemarowset meldet keine Aktivitäten durch DMV-Abfragen.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|a07ccd44-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|CommandObjects|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  