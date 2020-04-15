---
title: Datums- und Zeitverbesserungen (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 94a9b8517ebd2539250995fea896c53a376fc65d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301755"
---
# <a name="date-and-time-improvements-odbc"></a>Verbesserungen bei Datum und Zeit (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] wurden neue Datums- und Uhrzeitdatentypen eingeführt. In diesem Abschnitt wird beschrieben, wie diese neuen Typen als Erweiterungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verfügbar gemacht werden. Eine Übersicht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über die Native Client-Unterstützung für die neuen Datums- und Uhrzeitdatentypen finden Sie unter [Datums- und Uhrzeitverbesserungen](../../relational-databases/native-client/features/date-and-time-improvements.md). Ein Beispiel zum Nachweis der ODBC-Datums-/Uhrzeitunterstützung finden Sie unter Verwenden von [Datums- und Uhrzeittypen](../../relational-databases/native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Allgemeine Informationen über Datums- und Uhrzeitdatentypen finden Sie unter [datetime &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Datentypunterstützung für ODBC-Verbesserungen bei Datum und Uhrzeit](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Liefert Informationen über ODBC-Typen, die Datums- und Uhrzeitdatentypen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützen.  
  
 [Metadaten &#40;ODBC-&#41;](https://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
 Beschreibt Informationen, die in den Feldern "Implementierungsparameterdeskriptor" (IPD) und "Implementierungszeilendeskriptor" (IRD) zurückgegeben werden, sowie spaltenmetadaten, die von **SQLColumns** und **SQLProcedureColumns**zurückgegeben werden. Beschreibt auch Datentypmetadaten, die von **SQLGetTypeInfo**zurückgegeben werden.  
  
 [datetime Data Type Conversions &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-odbc.md)  
 Beschreibt die Konvertierung zwischen datetime- und datetimeoffset-Werten.  
  
 [sql_variant-Unterstützung für Datum- und Uhrzeit-Typen](../../relational-databases/native-client-odbc-date-time/sql-variant-support-for-date-and-time-types.md)  
 Beschreibt die Unterstützung der SQL_VARIANT-Funktion für die verbesserte Datums- und Uhrzeitfunktionalität.  
  
 [Massenkopieränderungen für erweiterte Datums- und Uhrzeittypen &#40;OLE DB- und ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Beschreibt Datums-/Uhrzeitverbesserungen zur Unterstützung von Massenkopiervorgängen.  
  
 [Verbessertes Datums- und Uhrzeittypverhalten mit früheren SQL Server-Versionen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Beschreibt das erwartete Verhalten, wenn eine Clientanwendung, die erweiterte Datums- und Uhrzeitfeatures verwendet, mit einer älteren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kommuniziert und wenn ein Client, der mit einer älteren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client kompiliert wurde, Befehle an einen Server sendet, der erweiterte Datums- und Uhrzeitfeatures unterstützt.  
  
 [ODBC API-Unterstützung für verbesserte Funktionen für Datum und Uhrzeit](../../relational-databases/native-client-odbc-date-time/odbc-api-support-for-enhanced-date-and-time-features.md)  
 Listet die ODBC-Funktionen auf, die die verbesserte Datums- und Uhrzeitfunktionalität unterstützen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
