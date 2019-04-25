---
title: Schemarowsets für OLE DB-Tabellenwertparameter geändert | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6ba38f2a02b97c5fb776f2744a113d4989f0425c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62516072"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>Schemarowsets für OLE DB-Tabellenwertparameter geändert
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Folgende Schemarowsets wurden zur Unterstützung von Tabellenwertparametern geändert oder hinzugefügt.  
  
|Schemarowset|Description|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|Zwei neue Spalten namens SS_TYPE_CATALOG_NAME und SS_TYPE_SCHEMANAME wurden am Ende des Rowsets hinzugefügt. Die folgenden Spalten konnten für zukünftige Typen wiederverwendet werden. Die Spalten TYPE_NAME und LOCAL_TYPE_NAME enthalten in Zukunft den Namen des TABLE-Tabellenwertparametertyps. Die DATA_TYPE-Spalte weist den Wert DBTYPE_TABLE = 143 für Tabellenwertparameter auf.|  
|DBSCHEMA_TABLE_TYPES|Dieses Rowset wurde hinzugefügt, um die Unterstützung von Tabellenwertparametern zu gewährleisten. Es ist mit DBSCHEMA_TABLES nahezu identisch, mit der Ausnahme, dass es Metadaten nur für Tabellentypen, nicht aber für Tabellen, Sichten oder Synonyme zurückgibt. Die TABLE_TYPE-Spalte weist den Wert 'TABLE TYPE' auf.|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|Dieses Rowset wurde hinzugefügt, um die Unterstützung von Tabellenwertparametern zu gewährleisten. Es ist mit DBSCHEMA_PRIMARY_KEYS identisch, mit der Ausnahme, dass es Primärschlüsselmetadaten nur für Tabellentypen, nicht aber für Tabellen zurückgibt.|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|Dieses Rowset wurde hinzugefügt, um die Unterstützung von Tabellenwertparametern zu gewährleisten. Es ist mit DBSCHEMA_COLUMNS identisch, mit der Ausnahme, dass es Spaltenmetadaten nur für Tabellentypen, nicht aber für Tabellen, Sichten oder Synonyme zurückgibt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
