---
title: Datums-und Uhrzeit Verbesserungen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d56689bb045a6540bfdfbb9c7147dc34db110bde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63207004"
---
# <a name="date-and-time-improvements-odbc"></a>Verbesserungen bei Datum und Zeit (ODBC)
  In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] wurden neue Datums- und Uhrzeitdatentypen eingeführt. In diesem Abschnitt wird beschrieben, wie diese neuen Typen als Erweiterungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verfügbar gemacht werden. Eine Übersicht über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Unterstützung für die neuen Datums-und Uhrzeit Datentypen finden Sie unter [Verbesserungen bei Datum und Uhrzeit](../native-client/features/date-and-time-improvements.md). Ein Beispiel für die ODBC-Datums-/Uhrzeitunterstützung finden Sie unter [Verwenden von Datums-und Uhrzeit Typen](../native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Weitere allgemeine Informationen zu Datums-und Uhrzeit Datentypen finden Sie unter [DateTime &#40;Transact-SQL-&#41;](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Datentypunterstützung für ODBC-Verbesserungen bei Datum und Uhrzeit](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Liefert Informationen über ODBC-Typen, die Datums- und Uhrzeitdatentypen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützen.  
  
 [Metadaten &#40;ODBC-&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
 Beschreibt Informationen, die in den IPD- und IRD-Feldern (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor) zurückgegeben werden, sowie Spaltenmetadaten, die von `SQLColumns` und `SQLProcedureColumns` zurückgegeben werden. Beschreibt auch die von `SQLGetTypeInfo` zurückgegebenen Datentyp-Metadaten.  
  
 [DateTime-Datentyp Konvertierungen &#40;ODBC-&#41;](datetime-data-type-conversions-odbc.md)  
 Beschreibt die Konvertierung zwischen datetime- und datetimeoffset-Werten.  
  
 [sql_variant-Unterstützung für Datums- und Uhrzeittypen](sql-variant-support-for-date-and-time-types.md)  
 Beschreibt die Unterstützung der SQL_VARIANT-Funktion für die verbesserte Datums- und Uhrzeitfunktionalität.  
  
 [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeittypen &#40;OLE DB und ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Beschreibt Datums-/Uhrzeitverbesserungen zur Unterstützung von Massenkopiervorgängen.  
  
 [Verbessertes Verhalten des Datums-und Uhrzeittyps mit früheren Versionen von SQL Server &#40;ODBC&#41;](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Beschreibt das erwartete Verhalten, wenn eine Client Anwendung, die verbesserte Datums-und Uhrzeit Funktionen verwendet, mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]einer älteren Version von kommuniziert und wenn ein Client, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit einer älteren Version von Native Client kompiliert wurde, Befehle an einen Server sendet, der erweiterte Datums-und Uhrzeit Funktionen unterstützt.  
  
 [ODBC-API-Unterstützung für verbesserte Funktionen für Datum und Uhrzeit](odbc-api-support-for-enhanced-date-and-time-features.md)  
 Listet die ODBC-Funktionen auf, die die verbesserte Datums- und Uhrzeitfunktionalität unterstützen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
