---
title: Schemarowsets für OLE DB-Tabellenwertparameter geändert | Microsoft-Dokumentation
description: Schemarowsets für OLE DB-Tabellenwertparameter geändert
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: e51fe46871555f01d2dda238515f8f1200b2fa27
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801118"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>Schemarowsets für OLE DB-Tabellenwertparameter geändert
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Folgende Schemarowsets wurden zur Unterstützung von Tabellenwertparametern geändert oder hinzugefügt.  
  
|Schemarowset|und Beschreibung|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|Zwei neue Spalten namens SS_TYPE_CATALOG_NAME und SS_TYPE_SCHEMANAME wurden am Ende des Rowsets hinzugefügt. Die folgenden Spalten konnten für zukünftige Typen wiederverwendet werden. Die Spalten TYPE_NAME und LOCAL_TYPE_NAME enthalten in Zukunft den Namen des TABLE-Tabellenwertparametertyps. Die DATA_TYPE-Spalte weist den Wert DBTYPE_TABLE = 143 für Tabellenwertparameter auf.|  
|DBSCHEMA_TABLE_TYPES|Dieses Rowset wurde hinzugefügt, um die Unterstützung von Tabellenwertparametern zu gewährleisten. Es ist mit DBSCHEMA_TABLES nahezu identisch, mit der Ausnahme, dass es Metadaten nur für Tabellentypen, nicht aber für Tabellen, Sichten oder Synonyme zurückgibt. Die TABLE_TYPE-Spalte weist den Wert 'TABLE TYPE' auf.|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|Dieses Rowset wurde hinzugefügt, um die Unterstützung von Tabellenwertparametern zu gewährleisten. Es ist mit DBSCHEMA_PRIMARY_KEYS identisch, mit der Ausnahme, dass es Primärschlüsselmetadaten nur für Tabellentypen, nicht aber für Tabellen zurückgibt.|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|Dieses Rowset wurde hinzugefügt, um die Unterstützung von Tabellenwertparametern zu gewährleisten. Es ist mit DBSCHEMA_COLUMNS identisch, mit der Ausnahme, dass es Spaltenmetadaten nur für Tabellentypen, nicht aber für Tabellen, Sichten oder Synonyme zurückgibt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
