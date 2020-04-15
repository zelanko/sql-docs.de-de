---
title: Konvertierungen von C in SQL | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC], C to SQL
ms.assetid: 7ac098db-9147-4883-8da9-a58ab24a0d31
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9f8161ea07e394192e972caf4f772d9e7def36e5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301779"
---
# <a name="datetime-data-type-conversions-from-c-to-sql"></a>datetime-Datentypkonvertierungen von C in SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In diesem Thema werden Probleme aufgeführt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die beim Konvertieren von C-Typen in Datums-/Uhrzeittypen zu berücksichtigen sind.  
  
 Die in der folgenden Tabelle beschriebenen Konvertierungen gelten für auf dem Client ausgeführte Konvertierungen. In Fällen, in denen der Client eine Sekundengenauigkeit für einen Parameter angibt, der sich von dem auf dem Server definierten unterscheidet, kann die Clientkonvertierung erfolgreich sein, aber der Server gibt einen Fehler zurück, wenn **SQLExecute** oder **SQLExecuteDirect** aufgerufen wird. OdBC behandelt insbesondere jede Abschneidung von Bruchsekunden als Fehler, während das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verhalten zu runden ist; Die Rundung erfolgt z. B., wenn Sie von **datetime2(6)** zu **datetime2(2)** wechseln. Werte der Datetime-Spalte werden auf 1/300 einer Sekunde gerundet, und für smalldatetime -Spalten werden Sekunden vom Server auf null festgelegt.  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
||SQL_TYPE_DATE|SQL_TYPE_TIME|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_SS_TIMSTAMPOFFSET|SQL_CHAR|SQL_WCHAR|  
|SQL_C_DATE|1|-|-|1,6|1,5,6|1,13|1,13|  
|SQL_C_TIME|-|1|1|1,7|1,5,7|1,13|1,13|  
|SQL_C_SS_TIME2|-|1,3|1,10|1,7|1,5,7|1,13|1,13|  
|SQL_C_BINARY(SQL_SS_TIME2_STRUCT)|–|–|1,10,11|–|–|–|–|  
|SQL_C_TYPE_TIMESTAMP|1,2|1,3,4|1,4,10|1,10|1,5,10|1,13|1,13|  
|SQL_C_SS_TIMESTAMPOFFSET|1,2,8|1,3,4,8|1,4,8,10|1,8,10|1,10|1,13|1,13|  
|SQL_C_BINARY(SQL_SS_TIMESTAMPOFFSET_STRUCT)|–|–|–|–|1,10,11|–|–|  
|SQL_C_CHAR/SQL_WCHAR (date)|9|9|9|9,6|9,5,6|–|–|  
|SQL_C_CHAR/SQL_WCHAR (time2)|9|9,3|9,10|9,7,10|9,5,7,10|–|–|  
|SQL_C_CHAR/SQL_WCHAR (datetime)|9,2|9,3,4|9,4,10|9,10|9,5,10|–|–|  
|SQL_C_CHAR/SQL_WCHAR (datetimeoffset)|9,2,8|9,3,4,8|9,4,8,10|9,8,10|9,10|–|–|  
|SQL_C_BINARY(SQL_DATE_STRUCT)|1,11|–|–|–|–|–|–|  
|SQL_C_BINARY(SQL_TIME_STRUCT)|–|–|–|–|–|–|–|  
|SQL_C_BINARY(SQL_TIMESTAMP_STRUCT)|–|–|–|–|–|–|–|  
  
## <a name="key-to-symbols"></a>Aufschlüsselung der Symbole  
  
-   **-**: Es wird keine Konvertierung unterstützt. Es wird ein Diagnosedatensatz mit SQLSTATE 07006 und der Meldung "Attributverletzung beschränkter Datentypen" generiert.  
  
-   **1**: Wenn die angegebenen Daten ungültig sind, wird ein Diagnosedatensatz mit SQLSTATE 22007 und der Meldung "Ungültiges Datumszeitformat" generiert.  
  
-   **2**: Zeitfelder müssen Null sein, oder ein Diagnosedatensatz wird mit SQLSTATE 22008 und der Meldung "Fractional abschneide" generiert.  
  
-   **3**: Bruchsekunden müssen Null sein, oder ein Diagnosedatensatz wird mit SQLSTATE 22008 und der Meldung "Fractional abschneide" generiert.  
  
-   **4**: Die Datumskomponente wird ignoriert.  
  
-   **5**: Die Zeitzone wird auf die Zeitzoneneinstellung des Clients festgelegt.  
  
-   **6**: Die Zeit ist auf Null eingestellt.  
  
-   **7**: Das Datum wird auf das aktuelle Datum festgelegt.  
  
-   **8**: Die Zeit wird von der Zeitzone des Clients in UTC konvertiert. Tritt während dieser Konvertierung ein Fehler auf, wird ein Diagnosedatensatz mit SQLSTATE 22008 und der Meldung "Überlauf im Datetime-Feld" generiert.  
  
-   **9**: Die Zeichenfolge wird analysiert und in einen Datums-, Datums-, Datumszeit- oder Zeitwert konvertiert, abhängig vom ersten gefundenen Satzzeichen und dem Vorhandensein der verbleibenden Komponenten. Die Zeichenfolge wird dann in den Zieltyp konvertiert. Dabei wird nach den Regeln in der vorangehenden Tabelle für den Quelltyp vorgegangen, der von diesem Prozess ermittelt wird. Wenn bei der Analyse der Daten ein Fehler ermittelt wird, wird ein Diagnosedatensatz mit SQLSTATE 22018 und der Meldung "Ungültiger Zeichenwert für Konvertierungsangabe" generiert. Wenn die Jahresangabe außerhalb des vom datetime- und smalldatetime-Parameter unterstützten Bereichs liegt, wird ein Diagnosedatensatz mit SQLSTATE 22007 und der Meldung "Ungültiges datetime-Format" generiert.  
  
     Der Wert für datetimeoffset muss nach der Konvertierung in das UTC-Format innerhalb des gültigen Bereichs liegen und zwar selbst dann, wenn keine Konvertierung in UTC angefordert wird. Der Grund dafür ist, dass der TDS und der Server das Datum stets in datetimeoffset-Werte für UTC normalisieren, weshalb der Client prüfen muss, ob die Zeitkomponenten innerhalb des nach Konvertierung in UTC unterstützten Bereichs liegen. Wenn der Wert nicht innerhalb des unterstützten UTC-Bereichs liegt, wird ein Diagnosedatensatz mit SQLSTATE 22007 und der Meldung "Ungültiges datetime-Format" generiert.  
  
-   **10**: Wenn ein Abschneiden mit Datenverlust auftritt, wird ein Diagnosedatensatz mit SQLSTATE 22008 und der Meldung "Ungültiges Zeitformat" generiert. Dieser Fehler tritt auch dann auf, wenn der Wert außerhalb des Bereichs liegt, der vom UTC-Bereich, den der Server verwendet, dargestellt werden kann.  
  
-   **11**: Wenn die Bytelänge der Daten nicht der Größe der Struktur entspricht, die für den SQL-Typ erforderlich ist, wird ein Diagnosedatensatz mit SQLSTATE 22003 und der Meldung "Numerischer Wert aout of range" generiert.  
  
-   **12**: Wenn die Bytelänge der Daten 4 oder 8 beträgt, werden die Daten im Unformat TDS smalldatetime oder datetime an den Server gesendet. Wenn die Bytelänge der Daten exakt mit der Größe von SQL_TIMESTAMP_STRUCT übereinstimmt, werden die Daten in das TDS-Format für datetime2 konvertiert.  
  
-   **13**: Wenn ein Abschneiden mit Datenverlust auftritt, wird ein Diagnosedatensatz mit SQLSTATE 22001 und der Meldung "String-Daten, rechts abgeschnitten" generiert.  
  
     Die Anzahl der Bruchsekundenziffern (die Skala) wird anhand der Größe der Zielspalte gemäß der folgenden Tabelle ermittelt:  
  
    ||||  
    |-|-|-|  
    |type|Implizierte Dezimalstellen<br /><br /> 0|Implizierte Dezimalstellen<br /><br /> 1..9|  
    |SQL_C_TYPE_TIMESTAMP|19|21..29|  
  
     Wenn die Sekundenbruchteile für SQL_C_TYPE_TIMESTAMP mit drei Ziffern ohne Datenverlust dargestellt werden können und die Spaltengröße 23 oder größer ist, werden genau drei Dezimalstellen für Sekundenbruchteile generiert. Dieses Verhalten stellt die Abwärtskompatibilität für Anwendungen sicher, die mit älteren ODBC-Treibern entwickelt wurden.  
  
     Für Spaltengrößen, die den Bereich in der Tabelle übersteigen, werden 9 Dezimalstellen impliziert. Diese Konvertierung sollte bis zu neun Dezimalstellen für Sekundenbruchteile ermöglichen, das von ODBC zugelassene Maximum.  
  
     Eine Spaltengröße von 0 (null) impliziert unendliche Größe für Zeichentypen mit variabler Länge in ODBC (9 Ziffern, sofern die 3-Ziffern-Regel für SQL_C_TYPE_TIMESTAMP nicht gilt). Die Angabe einer Spaltengröße von 0 (null) mit einem Zeichentyp fester Länge ist ein Fehler.  
  
-   **N/A**: [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Vorhandenes und früheres Verhalten wird beibehalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datums- und Uhrzeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
