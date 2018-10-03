---
title: Datums- / Uhrzeitverbesserungen (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09677c9fe2ebd023f10176435fffa1d35945f18a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117570"
---
# <a name="date-and-time-improvements-ole-db"></a>Verbesserungen bei Datum und Uhrzeit (OLE DB)
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] führt neue Datums- und Uhrzeitdatentypen ein. In diesem Abschnitt wird beschrieben, wie diese neuen Typen als Erweiterungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verfügbar gemacht werden. Eine Übersicht über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client unterstützten neuen Datums- und Uhrzeitdatentypen finden Sie unter [Datums- / Uhrzeitverbesserungen](../native-client/features/date-and-time-improvements.md). Ein Beispiel finden Sie unter [verwenden erweiterte Datums- und Uhrzeitfunktionen &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Weitere allgemeine Informationen zu Datum und Uhrzeit-Datentypen finden Sie unter ["DateTime" &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Datentypunterstützung für OLE DB-Datum- und Uhrzeit-Verbesserungen](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Enthält Informationen zu OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client), unterstützen Datentypen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datums- und Uhrzeitdatentypen.  
  
 [Metadaten &#40;OLE-DB&#41;](../../database-engine/dev-guide/metadata-ole-db.md)  
 Enthält Informationen über die DBBINDING-Struktur, `ICommandWithParameters::GetParameterInfo`, `ICommandWithParameters::SetParameterInfo`, `IColumnsRowset::GetColumnsRowset` und `ColumnsInfo::GetColumnInfo`. Stellt auch Informationen über Updates auf OLE DB-Schemarowsets bereit.  
  
 [Bindungen und Konvertierungen &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 Beschreibt die Regeln für die Konvertierung sowohl vorhandener als auch neuer Datumstypen zwischen Server und Client.  
  
 [Massenimport der Kopie Änderungen für verbesserte Datums- und Uhrzeittypen &#40;OLE DB- und ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Beschreibt Datums-/Uhrzeitverbesserungen zur Unterstützung von Massenkopiervorgängen.  
  
 [OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen](ole-db-api-support-for-date-and-time-enhancements.md)  
 Beschreibt die OLE DB-APIs, die verbesserte Datums-/Uhrzeitfunktionen unterstützen.  
  
 [Vergleichbarkeit für 'IRowsetFind'](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 Beschreibt Datums-/Uhrzeittypen und `IRowsetFind`.  
  
 [Neue Datums- und Uhrzeitfunktionen bei früheren Versionen von SQL Server &#40;OLE-DB&#41;](new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 Beschreibt das erwartete Verhalten, wenn eine Clientanwendung, die verbesserte Datums- und Uhrzeitfunktionen verwendet, mit einer älteren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kommuniziert und wenn ein Client, der mit einer älteren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client kompiliert wurde, Befehle an einen Server sendet, der verbesserte Datums- und Uhrzeitfunktionen unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
