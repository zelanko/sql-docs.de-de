---
title: DISCOVER_DATASOURCES-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DISCOVER_DATASOURCES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_DATASOURCES rowset
ms.assetid: f3ff26ab-a447-416b-ba54-1716df2283de
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e319b05d1d9aec74b01b73b671f613a2703d900f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185257"
---
# <a name="discoverdatasources-rowset"></a>DISCOVER_DATASOURCES-Rowset
  Gibt eine Liste der XMLA-Anbieterdatenquellen (XML for Analysis) zurück, die auf dem Server oder dem Webdienst verfügbar sind. Die veröffentlichten Datenquellen werden von einer URL des Anwendungswebservers zurückgegeben. Der Client kann eine Verbindung mit einer der Datenquellen in der Liste herstellen.  
  
 Aufrufen der [ermitteln](../../xmla/xml-elements-methods-discover.md) -Methode mit der `DISCOVER_DATASOURCES` Enumerationswert in der [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) -Element, die `Discover` Methode gibt die `DISCOVER_DATASOURCES` Rowset.  
  
 **Gilt für:** tabellarische und mehrdimensionale Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Der Client wählt eine Datenquelle durch Festlegen der `DataSourceInfo` -Eigenschaft in der [Eigenschaften](../../xmla/xml-elements-properties/properties-element-xmla.md) -Element, das zusammen mit gesendet wird die [Befehl](../../xmla/xml-elements-properties/command-element-xmla.md) Element durch den [Execute](../../xmla/xml-elements-methods-execute.md) -Methode. Ein Client sollte den Inhalt der `DataSourceInfo`-Eigenschaft nicht erstellen, um sie an den Server zu senden. Der Client sollte stattdessen die `Discover`-Methode verwenden, um die von dem Anbieter unterstützten Datenquellen zu finden. Der Client sendet anschließend den gleichen Wert für die `DataSourceInfo`-Eigenschaft zurück, die er vom `DISCOVER_DATASOURCES`-Rowset abruft.  
  
 Die `DISCOVER_DATASOURCES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Einschränkung|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DataSourceName`|`DBTYPE_WSTR`|ja|Der Name der Datenquelle, beispielsweise `Adventure Works`.|  
|`DataSourceDescription`|`DBTYPE_WSTR`||Die vom Verleger eingegebene Beschreibung der Datenquelle.<br /><br /> Gelegten `NULL`.|  
|`URL`|`DBTYPE_WSTR`|ja|Der eindeutige Pfad, der angibt, wo die XMLA-Methoden (XML for Analysis) für diese Datenquelle aufgerufen werden.<br /><br /> Gelegten `NULL`.|  
|`DataSourceInfo`|`DBTYPE_WSTR`||Eine Zeichenfolge, die alle zusätzlichen Informationen enthält, die erforderlich sind, um eine Verbindung mit der Datenquelle herzustellen.<br /><br /> Gelegten `NULL`.|  
|`ProviderName`|`DBTYPE_WSTR`|ja|Der Name des Anbieters für die Datenquelle.<br /><br /> Beispiel: `"MSOLAP"`<br /><br /> Gelegten `NULL`.|  
|`ProviderType`|`DBTYPE_WSTR`|ja|Die vom Anbieter unterstützten Datentypen. Dieses Array kann einen oder mehrere der folgenden Typen enthalten:<br /><br /> `MDP`: multidimensionaler Datenanbieter.<br /><br /> `TDP`: tabellarischer Datenanbieter.<br /><br /> `DMP`: Data Mining-Anbieter (implementiert die Spezifikation von OLE für DB für Data Mining).|  
|`AuthenticationMode`|`DBTYPE_WSTR`|ja|Eine Spezifikation, die angibt, welchen Typ des Sicherheitsmodus die Datenquelle verwendet. Folgende Werte sind möglich:<br /><br /> `Unauthenticated`: Es muss weder Benutzer-ID noch Kennwort gesendet werden.<br /><br /> `Authenticated`: In den Informationen, die für die Verbindung mit der Datenbank erforderlich sind, müssen Benutzer-ID und Kennwort enthalten sein.<br /><br /> `Integrated`: Die Datenquelle verwendet die zugrundeliegende Sicherheit, um die Autorisierung zu ermitteln, beispielsweise die von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS) bereitgestellte integrierte Sicherheit.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
> [!IMPORTANT]  
>  Das `DISCOVER_DATASOURCES`-Rowset kann nicht mithilfe von DMV-Abfragen bzw. der SELECT-Befehlssyntax abgefragt werden. Das `DISCOVER_DATASOURCES`-Rowset kann jedoch mithilfe von <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A> abgefragt werden.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|06c03d41-f66d-49f3-b1b8-987f7af4cf18|  
|ADOMDNAME|DataSources|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
