---
title: OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 94bb860df5a9ee2f3b125f6e05c6ff5adb44db99
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773422"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Die folgenden OLE DB-APIs unterstützen die erweiterten Funktionen für Datum und Uhrzeit.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Ein Flag wird zur DBBINDING-Struktur hinzugefügt, damit Anwendungen zwischen den Werten **datetime**, **datetime2** und **smalldatetime** unterscheiden können. Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Weitere Informationen finden Sie unter [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeit Typen &#40;OLE DB und ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Ausführliche Informationen zu den betroffenen Schemarowsets finden Sie unter [Date and Time and Schema Rowsets (Datum, Uhrzeit und Schemarowsets)](../../relational-databases/native-client-ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md).|  
|IRowsetFastLoad|Diese Schnittstelle unterstützt ohne Änderungen die neuen Datums-/Uhrzeit-Typen.|  
|ITableDefinition::CreateTable|Weitere Informationen finden Sie unter [Data Type Support for OLE DB Date and Time Improvements (Datentypunterstützung für Verbesserungen von Datum und Uhrzeit in OLE DB)](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
