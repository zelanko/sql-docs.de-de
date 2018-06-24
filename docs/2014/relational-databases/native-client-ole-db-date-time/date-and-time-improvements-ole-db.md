---
title: Datum und Uhrzeit-Verbesserungen (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bb9175dca513980ccc770b8e2e80cf9e68b0706f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056471"
---
# <a name="date-and-time-improvements-ole-db"></a>Datum und Uhrzeit-Verbesserungen (OLE DB)
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] führt neue Datums- und Uhrzeitdatentypen ein. In diesem Abschnitt wird beschrieben, wie diese neuen Typen als Erweiterungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verfügbar gemacht werden. Eine Übersicht über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client unterstützten neuen Datums- und Uhrzeitdatentypen finden Sie unter [Datum und Uhrzeit-Verbesserungen](../native-client/features/date-and-time-improvements.md). Ein Beispiel finden Sie unter [erweiterte Verwenden von Datums- und Uhrzeitfunktionen &#40;OLE DB-&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Weitere allgemeine Informationen zu Datum und Uhrzeit-Datentypen finden Sie unter ["DateTime" &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Datentypunterstützung für OLE DB-Datum- und Uhrzeit-Verbesserungen](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Liefert Informationen über OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client), unterstützen Datentypen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datums-und Uhrzeitdatentypen.  
  
 [Metadaten &#40;OLE DB&#41;](../../database-engine/dev-guide/metadata-ole-db.md)  
 Enthält Informationen über die DBBINDING-Struktur, `ICommandWithParameters::GetParameterInfo`, `ICommandWithParameters::SetParameterInfo`, `IColumnsRowset::GetColumnsRowset` und `ColumnsInfo::GetColumnInfo`. Stellt auch Informationen über Updates auf OLE DB-Schemarowsets bereit.  
  
 [Bindungen und Konvertierungen &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 Beschreibt die Regeln für die Konvertierung sowohl vorhandener als auch neuer Datumstypen zwischen Server und Client.  
  
 [Massenkopieren Kopie Änderungen für die verbesserte Datums- und Uhrzeittypen &#40;OLE DB- und ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Beschreibt Datums-/Uhrzeitverbesserungen zur Unterstützung von Massenkopiervorgängen.  
  
 [OLE DB-API-Unterstützung für Datums- und Uhrzeit-Erweiterungen](ole-db-api-support-for-date-and-time-enhancements.md)  
 Beschreibt die OLE DB-APIs, die verbesserte Datums-/Uhrzeitfunktionen unterstützen.  
  
 [Vergleichbarkeit für 'IRowsetFind'](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 Beschreibt Datums-/Uhrzeittypen und `IRowsetFind`.  
  
 [Neue Uhrzeitfunktionen zu Datum und mit früheren Versionen von SQL Server &#40;OLE DB&#41;](new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 Beschreibt das erwartete Verhalten, wenn eine Clientanwendung, die verbesserte Datums- und Uhrzeitfunktionen verwendet, mit einer älteren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kommuniziert und wenn ein Client, der mit einer älteren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client kompiliert wurde, Befehle an einen Server sendet, der verbesserte Datums- und Uhrzeitfunktionen unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
