---
title: DISCOVER_COMMANDS-Rowset | Microsoft-Dokumentation
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
- DISCOVER_COMMANDS rowset
ms.assetid: d228f265-05d9-4d2c-a622-44c73eab7a71
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 860645ba09ee294b6421472f235a38d66f54abe8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157321"
---
# <a name="discovercommands-rowset"></a>DISCOVER_COMMANDS-Rowset
  Stellt Ressourcenverwendungs- und Aktivitätsinformationen über die zurzeit ausgeführten oder zuletzt ausgeführten Befehle auf den offenen Verbindungen auf dem Server bereit.  
  
 **Gilt für:** tabellarische und mehrdimensionale Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_COMMANDS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Einschränkung|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`SESSION_SPID`|`DBTYPE_I4`|ja|Die Sitzungs-ID.|  
|`SESSION_COMMAND_COUNT`|`DBTYPE_I4`||Die Anzahl der seit dem Start der Sitzung ausgeführten Befehle.|  
|`COMMAND_START_TIME`|`DBTYPE_DBTIMESTAMP`||Das Datum und die Uhrzeit, zu denen der letzte Befehl gestartet wurde, ausgedrückt als UTC-Zeit auf dem Server.|  
|`COMMAND_ELAPSED_TIME_MS`|`DBTYPE_I8`||Die seit dem Start des Befehls verstrichene Zeit in Millisekunden.|  
|`COMMAND_CPU_TIME_MS`|`DBTYPE_I8`||Die CPU-Zeit in Millisekunden, die seit dem Start der Befehlsausführung von dem Befehl beansprucht wurde.|  
|`COMMAND_READS`|`DBTYPE_I8`||Die akkumulierte Anzahl der seit dem Start des Befehls erfolgten Lesevorgänge auf dem Datenträger.|  
|`COMMAND_READ_KB`|`DBTYPE_I8`||Der akkumulierte Wert der seit dem Start des Befehls vom Datenträger gelesenen Daten in KB.|  
|`COMMAND_WRITES`|`DBTYPE_I8`||Die akkumulierte Anzahl der seit dem Start des Befehls erfolgten Schreibvorgänge auf dem Datenträger.|  
|`COMMAND_WRITE_KB`|`DBTYPE_I8`||Der akkumulierte Wert der seit dem Start des Befehls auf den Datenträger geschriebenen Daten in KB.|  
|`COMMAND_TEXT`|`DBTYPE_WSTR`||Der Befehlstext.|  
|`COMMAND_END_TIME`|`DBTYPE_DBTIMESTAMP`||UTC-Datum und -Zeit des Servers, zu denen der Befehl seine Ausführung beendet.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|a07ccd34-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Befehle|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
