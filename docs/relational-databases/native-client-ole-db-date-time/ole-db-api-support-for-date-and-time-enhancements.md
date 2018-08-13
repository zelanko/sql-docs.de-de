---
title: OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a609834711e6fe90337b9cb430d1987f8f6d9e79
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39562604"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die folgenden OLE DB-APIs unterstützen die erweiterten Funktionen für Datum und Uhrzeit.  
  
|Funktion|Description|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Ein Flag wurde in der DBBINDING-Struktur zum Aktivieren von Anwendungen zur Unterscheidung zwischen **"DateTime"**, **datetime2**, und **Smalldatetime** Werte. Weitere Informationen finden Sie unter [Parameter und Rowsets Metadata](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Weitere Informationen finden Sie unter [Massenkopieränderungen für verbesserte Datums- und Uhrzeittypen &#40;OLEDB- und ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Weitere Informationen finden Sie unter[Parameter und Rowsets Metadata](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Weitere Informationen finden Sie unter[Parameter und Rowsets Metadata](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Weitere Informationen finden Sie unter[Parameter und Rowsets Metadata](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Weitere Informationen finden Sie unter[Parameter und Rowsets Metadata](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Einzelheiten zu den betroffenen Schemarowsets finden Sie unter[Datums- und Uhrzeit- sowie Schemarowsets](../../relational-databases/native-client-ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md).|  
|IRowsetFastLoad|Diese Schnittstelle unterstützt ohne Änderungen die neuen Datums-/Uhrzeit-Typen.|  
|ITableDefinition::CreateTable|Weitere Informationen finden Sie unter [Datentypunterstützung für OLE DB-Datum und Uhrzeit-Verbesserungen](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
