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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef6334f6fe4671f2563add857f6dd58ce67a2840
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63237848"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen
  Die folgenden OLE DB-APIs unterstützen die erweiterten Funktionen für Datum und Uhrzeit.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|In der DBBINDING-Struktur wird ein Flag hinzugefügt, so dass Anwendungen zwischen den Werten `datetime`, `datetime2` und `smalldatetime` unterscheiden können. Weitere Informationen finden Sie unter [Parameter und Rowset-Metadaten](metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Weitere Informationen finden Sie unter [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeit Typen &#40;OLE DB und ODBC-&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Weitere Informationen finden Sie unter[Parameter und Rowset-Metadaten](metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Weitere Informationen finden Sie unter[Parameter und Rowset-Metadaten](metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Weitere Informationen finden Sie unter[Parameter und Rowset-Metadaten](metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Weitere Informationen finden Sie unter[Parameter und Rowset-Metadaten](metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Details zu den betroffenen Schemarowsets finden Sie unter[Datums-und Uhrzeit-und Schemarowsets](../native-client-ole-db-rowsets/rowsets.md).|  
|IRowsetFastLoad|Diese Schnittstelle unterstützt ohne Änderungen die neuen Datums-/Uhrzeit-Typen.|  
|ITableDefinition::CreateTable|Weitere Informationen finden Sie [unter Datentyp Unterstützung für OLE DB Datums-und Uhrzeit Verbesserungen](data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datums-und Uhrzeit Verbesserungen &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  
