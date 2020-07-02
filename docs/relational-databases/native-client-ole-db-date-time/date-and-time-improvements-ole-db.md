---
title: Verbesserungen bei Datum und Uhrzeit (OLE DB)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
author: markingmyname
ms.author: maghan
ms.custom: seo-dt-2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b132eb18fd743b692daf50b3a53e56ade5b0e8f9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773454"
---
# <a name="date-and-time-improvements-ole-db"></a>Verbesserungen bei Datum und Uhrzeit (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] führt neue Datums- und Uhrzeitdatentypen ein. In diesem Abschnitt wird beschrieben, wie diese neuen Typen als Erweiterungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verfügbar gemacht werden. Eine Übersicht über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Unterstützung für die neuen Datums-und Uhrzeit Datentypen finden Sie unter [Verbesserungen bei Datum und Uhrzeit](../../relational-databases/native-client/features/date-and-time-improvements.md). Ein Beispiel finden Sie unter [Verwenden von erweiterten Datums- und Uhrzeitfeatures &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Allgemeine Informationen über Datums- und Uhrzeitdatentypen finden Sie unter [datetime &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Datentypunterstützung für OLE DB-Datum- und Uhrzeit-Verbesserungen](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Enthält Informationen über OLE DB ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client)-Typen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datums-und Uhrzeit Datentypen unterstützen.  
  
 [Metadata &#40;OLE DB&#41;](https://msdn.microsoft.com/library/605e3be5-aeea-4573-9847-b866ed3c8bff)  
 Dieser Artikel enthält Informationen über die DBBINDING-Struktur, **ICommandWithParameters::GetParameterInfo**, **ICommandWithParameters::SetParameterInfo**, **IColumnsRowset::GetColumnsRowset** und **IColumnsInfo::GetColumnInfo**. Stellt auch Informationen über Updates auf OLE DB-Schemarowsets bereit.  
  
 [Bindungen und Konvertierungen &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 Beschreibt die Regeln für die Konvertierung sowohl vorhandener als auch neuer Datumstypen zwischen Server und Client.  
  
 [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeittypen &#40;OLE DB und ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Beschreibt Datums-/Uhrzeitverbesserungen zur Unterstützung von Massenkopiervorgängen.  
  
 [OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen](../../relational-databases/native-client-ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 Beschreibt die OLE DB-APIs, die verbesserte Datums-/Uhrzeitfunktionen unterstützen.  
  
 [Vergleichbarkeit für 'IRowsetFind'](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 Dieser Artikel beschreibt Datums- und Uhrzeittypen und **IRowsetFind**.  
  
 [Neue Datums-und Uhrzeit Funktionen mit früheren SQL Server Versionen &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 Beschreibt das erwartete Verhalten, wenn eine Clientanwendung, die verbesserte Datums- und Uhrzeitfunktionen verwendet, mit einer älteren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kommuniziert und wenn ein Client, der mit einer älteren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client kompiliert wurde, Befehle an einen Server sendet, der verbesserte Datums- und Uhrzeitfunktionen unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
