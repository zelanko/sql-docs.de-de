---
title: Unterstützung für verteilte Abfragen in Schemarowsets | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7f7c5746a34ca40d567886cce6bce4b9b8aceb76
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149883"
---
# <a name="distributed-query-support-in-schema-rowsets"></a>Verteilte Abfrageunterstützung für Schemarowsets
  Zur Unterstützung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verteilte Abfragen, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter **IDBSchemaRowset** Schnittstelle gibt Metadaten zu Verbindungsservern auf.  
  
 Wenn die DBPROPSET_SQLSERVERSESSION-Eigenschaft SSPROP_QUOTEDCATALOGNAMES auf VARIANT_TRUE festgelegt wurde, kann für den Katalognamen ein Bezeichner in Anführungszeichen angegeben werden (beispielsweise "my.catalog"). Wenn die Ausgabe eines Schemarowsets anhand des Katalogs, Einschränken der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erkennt einen zweiteiligen Namen mit dem verknüpften Server und Katalog-Namen. Angeben von für die Schemarowsets in der folgenden Tabelle, eine mit dem zweiteiligen Katalognamens in Form *Linked_server ***.*** Katalog* Ausgabe an den betreffenden Katalog des genannten Verbindungsservers beschränkt.  
  
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
>  Um ein Schemarowset auf alle Kataloge eines Verbindungsservers zu beschränken, verwenden Sie die Syntax *Linked_server* (wobei Punkts als Trennzeichen Teil der namensspezifikation ist). Diese Syntax ist gleichbedeutend mit der Angabe von NULL für die Katalognamensbeschränkung und wird auch verwendet, wenn der Verbindungsserver eine Datenquelle angibt, die Kataloge nicht unterstützt.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter definiert das Schemarowset LINKEDSERVERS, Rückgabe einer Liste von OLE DB-Datenquellen, die als Verbindungsserver registriert.  
  
## <a name="see-also"></a>Siehe auch  
 [Schemarowset-Unterstützung &#40;OLE DB&#41;](schema-rowset-support-ole-db.md)   
 [LINKEDSERVERS-Rowset &#40;OLE DB&#41;](schema-rowsets-linkedservers-rowset.md)  
  
  