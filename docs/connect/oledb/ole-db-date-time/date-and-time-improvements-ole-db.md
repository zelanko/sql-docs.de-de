---
title: Verbesserungen bei Datum und Uhrzeit (OLE DB) | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie der OLE DB-Treiber für SQL Server neue Datums- und Uhrzeitdatentypen unterstützt. Sehen Sie sich eine Übersicht und Beispiele an.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cd0f564a68f0b296008907f8620cd870c0e5ca7d
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862030"
---
# <a name="date-and-time-improvements-ole-db"></a>Verbesserungen bei Datum und Uhrzeit (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] führt neue Datums- und Uhrzeitdatentypen ein. In diesem Abschnitt wird beschrieben, wie diese neuen Typen als Erweiterungen im OLE DB-Treiber für SQL Server verfügbar gemacht werden. Eine Übersicht über die Unterstützung des OLE DB-Treibers für SQL Server für die neuen Datums- und Uhrzeitdatentypen finden Sie unter [Verbesserungen bei Datum und Uhrzeit](../../oledb/features/date-and-time-improvements.md). Ein Beispiel finden Sie unter [Verwenden von erweiterten Datums- und Uhrzeitfeatures &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Allgemeine Informationen über Datums- und Uhrzeitdatentypen finden Sie unter [datetime &#40;Transact-SQL&#41;](../../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Datentypunterstützung für OLE DB-Datum- und Uhrzeit-Verbesserungen](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Dieser Artikel enthält Informationen über OLE DB-Typen (OLE DB-Treiber für SQL Server), die Datums- und Uhrzeitdatentypen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützen.  
  
 [Metadata &#40;OLE DB&#41;](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)  
 Dieser Artikel enthält Informationen über die DBBINDING-Struktur, **ICommandWithParameters::GetParameterInfo**, **ICommandWithParameters::SetParameterInfo**, **IColumnsRowset::GetColumnsRowset** und **IColumnsInfo::GetColumnInfo**. Stellt auch Informationen über Updates auf OLE DB-Schemarowsets bereit.  
  
 [Bindungen und Konvertierungen &#40;OLE DB&#41;](../../oledb/ole-db-date-time/conversions-ole-db.md)  
 Beschreibt die Regeln für die Konvertierung sowohl vorhandener als auch neuer Datumstypen zwischen Server und Client.  
  
 [Massenkopieränderungen für verbesserte Datums- und Uhrzeittypen &#40;OLE DB&#41;](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md)  
 Beschreibt Datums-/Uhrzeitverbesserungen zur Unterstützung von Massenkopiervorgängen.  
  
 [OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen](../../oledb/ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 Beschreibt die OLE DB-APIs, die verbesserte Datums-/Uhrzeitfunktionen unterstützen.  
  
 [Vergleichbarkeit für 'IRowsetFind'](../../oledb/ole-db-date-time/comparability-for-irowsetfind.md)  
 Dieser Artikel beschreibt Datums- und Uhrzeittypen und **IRowsetFind**.  
 
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Programmierung](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
