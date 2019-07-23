---
title: OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen | Microsoft-Dokumentation
description: OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: c2671b3df6432e63c0e0b36a24bade60286f72a7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015682"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die folgenden OLE DB-APIs unterstützen die erweiterten Funktionen für Datum und Uhrzeit.  
  
|Funktion|und Beschreibung|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Ein Flag wird in der DBBINDING-Struktur hinzugefügt, damit Anwendungen zwischen **DateTime**-, **datetime2**-und **smalldatetime** -Werten unterscheiden können. Weitere Informationen finden Sie unter [Parameter und Rowset-Metadaten](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Weitere Informationen finden Sie unter [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeit &#40;Typen&#41;OLE DB](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md).|  
|ICommandWithParameters::GetParameterInfo|Weitere Informationen finden Sie unter[Parameter und Rowset-Metadaten](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Weitere Informationen finden Sie unter[Parameter und Rowset-Metadaten](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Weitere Informationen finden Sie unter[Parameter und Rowset-Metadaten](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Weitere Informationen finden Sie unter[Parameter und Rowset-Metadaten](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Details zu den betroffenen Schemarowsets finden Sie unter[Datums-und Uhrzeit-und Schemarowsets](../../oledb/ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md).|  
|IRowsetFastLoad|Diese Schnittstelle unterstützt ohne Änderungen die neuen Datums-/Uhrzeit-Typen.|  
|ITableDefinition::CreateTable|Weitere Informationen finden Sie [unter Datentyp Unterstützung für OLE DB Datums-und Uhrzeit Verbesserungen](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
