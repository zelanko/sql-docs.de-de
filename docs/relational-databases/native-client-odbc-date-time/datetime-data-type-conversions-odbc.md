---
title: DateTime-Datentyp Konvertierungen (ODBC) | Microsoft-Dokumentation
description: Erfahren Sie mehr über Datentyp Konvertierungen in ODBC, die bereits von ODBC definiert sind oder konsistente ODBC-Erweiterungen sind.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 09a018250887ecf88e6a48c49222046699a14763
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967659"
---
# <a name="datetime-data-type-conversions-odbc"></a>datetime-Datentypkonvertierungen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die folgenden Konvertierungen sind entweder bereits von ODBC definiert oder stellen eine konsistente Erweiterung von ODBC dar. Die von den einzelnen Anbietern bereitgestellten Konvertierungen werden vom Benutzerkreis beeinflusst und weisen daher oft Inkonsistenzen untereinander auf. Werte in eckigen Klammern sind optional.  
  
-   Das Format von datetime-Zeichenfolgen ist 'yyyy-mm-dd[hh:mm:ss[.9999999][Plus/Minus hh:mm]]'  
  
-   Das Format von Uhrzeitzeichenfolgen ist 'hh:mm:ss[.9999999]'  
  
-   Das Format von Datumszeichenfolgen ist 'yyyy-mm-dd'.  
  
 Konvertierungen von Zeichenfolgen ermöglichen Flexibilität bei Leerstellen- und Feldbreite. Weitere Informationen finden Sie im Abschnitt "Datenformate: Zeichen folgen und Literale" unter [Datentyp Unterstützung für ODBC-Datums-und Uhrzeit Verbesserungen](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  
  
 Folgende sind allgemeine Konvertierungsregeln:  
  
-   Wenn keine Zeit vorhanden ist, der Empfänger aber Zeit speichern kann, wird die Zeit auf 0 (null) festgelegt.  
  
-   Wenn keine Datumsangabe vorhanden ist, der Empfänger aber das Datum speichern kann, wird das aktuelle Datum verwendet.  
  
-   Wenn in dem vom Client verwendeten Datentyp keine Zeitzone vorhanden ist, der Server aber eine Zeitzone speichern kann, wird das Datum in der Clientzeitzone gespeichert. Beachten Sie, dass dies vom Server Verhalten abweicht.  
  
-   Wenn in dem vom Server verwendeten Datentyp keine Zeitzone vorhanden ist, der Datentyp auf dem Client aber eine Zeitzone aufweist, wird die Zeit in UTC konvertiert, bevor sie auf dem Server gespeichert wird.  
  
-   Wenn die Zeit vorhanden ist, der Empfänger aber keine Zeit speichern kann, wird die Zeitkomponente ignoriert.  
  
-   Wenn ein Datum vorhanden ist, der Empfänger aber kein Datum speichern kann, wird die Datumskomponente ignoriert.  
  
-   Wenn es bei der Konvertierung von C in SQL zum Abschneiden von Sekunden oder Sekundenbruchteilen kommt, wird ein Diagnosedatensatz mit SQLSTATE 22008 und der Meldung "Überlauf im Datetime-Feld" generiert.  
  
-   Wenn es bei der Konvertierung von SQL in C zum Abschneiden von Sekunden oder Sekundenbruchteilen kommt, wird ein Diagnosedatensatz mit SQLSTATE 01S07 und der Meldung "Teilbereiche wurden abgeschnitten" generiert.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Konvertierungen von C in SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)  
 Listet Punkte auf, die bei der Konvertierung von C-Typen in Datum-/Uhrzeit-Typen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu berücksichtigen sind.  
  
 [Konvertierungen von SQL in C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)  
 Listet Punkte auf, die bei der Konvertierung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datum-/Uhrzeit-Typen in C-Typen zu berücksichtigen sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datums-und Uhrzeit Verbesserungen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
