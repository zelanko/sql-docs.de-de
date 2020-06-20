---
title: OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: rothja
ms.author: jroth
ms.openlocfilehash: cdb17f0d2104373ea797ff9403cc417dfaa3d868
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056254"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen
  Die folgenden OLE DB-APIs unterstützen die erweiterten Funktionen für Datum und Uhrzeit.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|In der DBBINDING-Struktur wird ein Flag hinzugefügt, so dass Anwendungen zwischen den Werten `datetime`, `datetime2` und `smalldatetime` unterscheiden können. Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Weitere Informationen finden Sie unter [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeit Typen &#40;OLE DB und ODBC-&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Weitere Informationen finden Sie unter [Parameter and Rowset Metadata (Parameter- und Rowsetmetadaten)](metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Ausführliche Informationen zu den betroffenen Schemarowsets finden Sie unter [Date and Time and Schema Rowsets (Datum, Uhrzeit und Schemarowsets)](../native-client-ole-db-rowsets/rowsets.md).|  
|IRowsetFastLoad|Diese Schnittstelle unterstützt ohne Änderungen die neuen Datums-/Uhrzeit-Typen.|  
|ITableDefinition::CreateTable|Weitere Informationen finden Sie unter [Data Type Support for OLE DB Date and Time Improvements (Datentypunterstützung für Verbesserungen von Datum und Uhrzeit in OLE DB)](data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](date-and-time-improvements-ole-db.md)  
  
  
