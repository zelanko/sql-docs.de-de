---
title: Schemarowsets, OLE DB Tabellenwert Parameter
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3b79f2b2b87e4a51c71a3c2c89378875810f92fb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283099"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>Schemarowsets für OLE DB-Tabellenwertparameter geändert
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Folgende Schemarowsets wurden zur Unterstützung von Tabellenwertparametern geändert oder hinzugefügt.  
  
|Schemarowset|BESCHREIBUNG|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|Zwei neue Spalten namens SS_TYPE_CATALOG_NAME und SS_TYPE_SCHEMANAME wurden am Ende des Rowsets hinzugefügt. Die folgenden Spalten konnten für zukünftige Typen wiederverwendet werden. Die Spalten TYPE_NAME und LOCAL_TYPE_NAME enthalten in Zukunft den Namen des TABLE-Tabellenwertparametertyps. Die DATA_TYPE-Spalte weist den Wert DBTYPE_TABLE = 143 für Tabellenwertparameter auf.|  
|DBSCHEMA_TABLE_TYPES|Dieses Rowset wurde hinzugefügt, um die Unterstützung von Tabellenwertparametern zu gewährleisten. Es ist mit DBSCHEMA_TABLES nahezu identisch, mit der Ausnahme, dass es Metadaten nur für Tabellentypen, nicht aber für Tabellen, Sichten oder Synonyme zurückgibt. Die TABLE_TYPE-Spalte weist den Wert 'TABLE TYPE' auf.|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|Dieses Rowset wurde hinzugefügt, um die Unterstützung von Tabellenwertparametern zu gewährleisten. Es ist mit DBSCHEMA_PRIMARY_KEYS identisch, mit der Ausnahme, dass es Primärschlüsselmetadaten nur für Tabellentypen, nicht aber für Tabellen zurückgibt.|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|Dieses Rowset wurde hinzugefügt, um die Unterstützung von Tabellenwertparametern zu gewährleisten. Es ist mit DBSCHEMA_COLUMNS identisch, mit der Ausnahme, dass es Spaltenmetadaten nur für Tabellentypen, nicht aber für Tabellen, Sichten oder Synonyme zurückgibt.|  
|||

## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwert Parameter &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
