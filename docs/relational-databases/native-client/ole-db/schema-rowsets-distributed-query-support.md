---
title: Verteilte Abfrageunterstützung für Schemarowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bd4d2bb25f1f576c83e35fe57de4d3de99cc4bc4
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243840"
---
# <a name="schema-rowsets---distributed-query-support-in-sql-server-native-client"></a>Schemarowsets-Unterstützung verteilter Abfragen in SQL Server Native Client
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Zur Unterstützung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verteilter Abfragen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt die **IDBSchemaRowset** -Schnittstelle von Native Client OLE DB-Anbieter Metadaten auf Verbindungs Servern zurück.  
  
 Wenn die DBPROPSET_SQLSERVERSESSION-Eigenschaft SSPROP_QUOTEDCATALOGNAMES auf VARIANT_TRUE festgelegt wurde, kann für den Katalognamen ein Bezeichner in Anführungszeichen angegeben werden (beispielsweise "my.catalog"). Wenn die Schemarowset-Ausgabe nach Katalog eingeschränkt wird, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erkennt der Native Client OLE DB-Anbieter einen zweiteiligen Namen, der den Verbindungs Server und den Katalognamen enthält. Geben Sie für die Schemarowsets in der folgenden Tabelle einen zweiteiligen Katalognamen als _linked_server_an **.** der _Katalog_ schränkt die Ausgabe in den entsprechenden Katalog des benannten Verbindungs Servers ein.  
  
|Schemarowset|Katalogeinschränkung|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMNS|TABLE_CATALOG|  
|DBSCHEMA_PRIMARY_KEYS|TABLE_CATALOG|  
|DBSCHEMA_TABLES|TABLE_CATALOG|  
|DBSCHEMA_FOREIGN_KEYS|PK_TABLE_CATALOG FK_TABLE_CATALOG|  
|DBSCHEMA_INDEXES|TABLE_CATALOG|  
|DBSCHEMA_COLUMN_PRIVILEGES|TABLE_CATALOG|  
|DBSCHEMA_TABLE_PRIVILEGES|TABLE_CATALOG|  
  
> [!NOTE]  
>  Zur Beschränkung eines Schemarowsets auf alle Kataloge eines Verbindungsservers, verwenden Sie die Syntax *linked_server* (wobei der Punkt als Trennzeichen Teil der Namensangabe ist). Diese Syntax ist gleichbedeutend mit der Angabe von NULL für die Katalognamensbeschränkung und wird auch verwendet, wenn der Verbindungsserver eine Datenquelle angibt, die Kataloge nicht unterstützt.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter definiert das Schemarowset LINKEDSERVERS und gibt eine Liste der OLE DB Datenquellen zurück, die als Verbindungs Server registriert sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schemarowset-Unterstützung &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)   
 [LINKEDSERVERS-Rowset &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  
