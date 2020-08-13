---
title: API-Unterstützung für Datums- und Uhrzeiterweiterungen (OLE DB-Treiber)
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
ms.openlocfilehash: 3003ed2de3b3c732ac9ef57e21ed5d6cf9415ec7
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244883"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die folgenden OLE DB-APIs unterstützen die erweiterten Funktionen für Datum und Uhrzeit.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Ein Flag wird zur DBBINDING-Struktur hinzugefügt, damit Anwendungen zwischen den Werten **datetime**, **datetime2** und **smalldatetime** unterscheiden können. Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Weitere Informationen finden Sie unter [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB&#41; (Massenkopieränderungen für verbesserte Datums- und Uhrzeittypen &#40;OLE DB&#41;)](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md).|  
|ICommandWithParameters::GetParameterInfo|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Ausführliche Informationen zu den betroffenen Schemarowsets finden Sie unter [Date and Time and Schema Rowsets (Datum, Uhrzeit und Schemarowsets)](../../oledb/ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md).|  
|IRowsetFastLoad|Diese Schnittstelle unterstützt ohne Änderungen die neuen Datums-/Uhrzeit-Typen.|  
|ITableDefinition::CreateTable|Weitere Informationen finden Sie unter [Data Type Support for OLE DB Date and Time Improvements (Datentypunterstützung für Verbesserungen von Datum und Uhrzeit in OLE DB)](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
