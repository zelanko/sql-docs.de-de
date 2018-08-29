---
title: Unterstützung für verteilte Abfragen in Schemarowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f9cc4aaa6792e1876a833cbe1fdff5575d4446d7
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43075983"
---
# <a name="schema-rowsets---distributed-query-support"></a>Schemarowsets: Verteilte Abfrageunterstützung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Zur Unterstützung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verteilte Abfragen, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter **IDBSchemaRowset** Schnittstelle gibt Metadaten auf Verbindungsservern zurück.  
  
 Wenn die DBPROPSET_SQLSERVERSESSION-Eigenschaft SSPROP_QUOTEDCATALOGNAMES auf VARIANT_TRUE festgelegt wurde, kann für den Katalognamen ein Bezeichner in Anführungszeichen angegeben werden (beispielsweise "my.catalog"). Bei der Ausgabe eines Schemarowsets angegeben von Catalog, beschränken die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erkennt einen zweiteiligen Namen mit dem verknüpften Server und Katalog-Namen. Für die Schemarowsets in der Tabelle unten wird durch die Angabe eines zweiteiligen Katalognamens in Form von *linked_server ***.*** catalog* die Ausgabe auf den betreffenden Katalog des genannten Verbindungsservers beschränkt.  
  
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
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter definiert das Schemarowset LINKEDSERVERS, Rückgabe einer Liste von OLE DB-Datenquellen, die als Verbindungsserver registriert.  
  
## <a name="see-also"></a>Siehe auch  
 [Schema Rowset Support &#40;OLE DB&#41; (Schemarowset-Unterstützung &#40;OLE DB&#41;)](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)   
 [LINKEDSERVERS-Rowset &#40;OLE-DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  
