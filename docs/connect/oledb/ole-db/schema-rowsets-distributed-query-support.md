---
title: Verteilte Abfrageunterstützung für Schemarowsets
description: Verteilte Abfrageunterstützung für Schemarowsets
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], OLE DB Driver for SQL Server
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 085a4424272e4d620c4b36fe9ecf44894cb1a33f
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105826"
---
# <a name="schema-rowsets---distributed-query-support"></a>Schemarowsets: Verteilte Abfrageunterstützung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Zur Unterstützung verteilter Abfragen in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt die **IDBSchemaRowset**-Schnittstelle des OLE DB-Treibers für SQL Server Metadaten über Verbindungsserver zurück.  
  
 Wenn die DBPROPSET_SQLSERVERSESSION-Eigenschaft SSPROP_QUOTEDCATALOGNAMES auf VARIANT_TRUE festgelegt wurde, kann für den Katalognamen ein Bezeichner in Anführungszeichen angegeben werden (beispielsweise "my.catalog"). Wenn eine Katalogeinschränkung für die Ausgabe eines Schemarowsets angegeben wird, erkennt der OLE DB-Treiber für SQL Server zweiteilige Namen, die sich aus dem Namen des Verbindungsservers und dem Katalognamen zusammensetzen. Für die Schemarowsets in der Tabelle unten wird durch die Angabe eines zweiteiligen Katalognamens in Form von *linked_server ***.*** catalog* die Ausgabe auf den betreffenden Katalog des genannten Verbindungsservers beschränkt.  
  
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
  
 Der OLE DB-Treiber für SQL Server definiert das Schemarowset LINKEDSERVERS und gibt eine Liste der OLE DB-Datenquellen zurück, die als Verbindungsserver registriert sind.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Schema Rowset Support &#40;OLE DB&#41; (Schemarowset-Unterstützung &#40;OLE DB&#41;)](../../oledb/ole-db/schema-rowset-support-ole-db.md)   
 [LINKEDSERVERS-Rowset &#40;OLE-DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  
