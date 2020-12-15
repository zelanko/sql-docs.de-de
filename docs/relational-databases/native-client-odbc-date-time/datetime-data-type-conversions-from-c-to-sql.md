---
description: datetime-Datentypkonvertierungen von C in SQL
title: Konvertierungen von C in SQL | Microsoft-Dokumentation
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0a65be08afc1a8570c64f7ffabddcb6c2d2d51b1
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438553"
---
# <a name="datetime-data-type-conversions-from-c-to-sql"></a>datetime-Datentypkonvertierungen von C in SQL
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  In diesem Thema werden Probleme aufgeführt, die beim Konvertieren von C-Typen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datums-/Uhrzeittypen berücksichtigt werden müssen  
  
 Die in der folgenden Tabelle beschriebenen Konvertierungen gelten für auf dem Client ausgeführte Konvertierungen. In Fällen, in denen der Client eine Sekundenbruchteile Genauigkeit für einen Parameter angibt, der von der auf dem Server definierten abweicht, kann die Client Konvertierung erfolgreich ausgeführt werden, der Server gibt jedoch einen Fehler zurück, wenn **SQLExecute** oder **SQLExecuteDirect** aufgerufen wird. Insbesondere behandelt ODBC das Abschneiden von Sekundenbruchteilen als Fehler, während das Verhalten bei der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Rundung erfolgt. beispielsweise erfolgt die Rundung, wenn Sie von **datetime2 (6)** zu **datetime2 (2)** wechseln. Werte der Datetime-Spalte werden auf 1/300 einer Sekunde gerundet, und für smalldatetime -Spalten werden Sekunden vom Server auf null festgelegt.  
  
|   | SQL_TYPE_DATE | SQL_TYPE_TIME | SQL_SS_TIME2 | SQL_TYPE_TIMESTAMP | SQL_SS_TIMSTAMPOFFSET | SQL_CHAR | SQL_WCHAR |
| - | ------------- | ------------- | ------------ | ------------------ | --------------------- | -------- | --------- |
| **SQL_C_DATE** |1|-|-|1,6|1,5,6|1,13|1,13|  
| **SQL_C_TIME** |-|1|1|1,7|1, 5, 7|1,13|1,13|  
| **SQL_C_SS_TIME2** |-|1,3|1,10|1,7|1, 5, 7|1,13|1,13|  
| **SQL_C_BINARY(SQL_SS_TIME2_STRUCT)** |–|–|1,10,11|–|–|–|–|  
| **SQL_C_TYPE_TIMESTAMP** |1,2|1,3,4|1,4,10|1,10|1,5,10|1,13|1,13|  
| **SQL_C_SS_TIMESTAMPOFFSET** |1,2,8|1,3,4,8|1,4,8,10|1,8,10|1,10|1,13|1,13|  
| **SQL_C_BINARY(SQL_SS_TIMESTAMPOFFSET_STRUCT)** |–|–|–|–|1,10,11|–|–|  
| **SQL_C_CHAR/SQL_WCHAR (date)** |9|9|9|9,6|9,5,6|–|–|  
| **SQL_C_CHAR/SQL_WCHAR (time2)** |9|9, 3|9,10|9,7,10|9,5,7,10|–|–|  
| **SQL_C_CHAR/SQL_WCHAR (datetime)** |9,2|9, 3, 4|9,4,10|9,10|9,5,10|–|–|  
| **SQL_C_CHAR/SQL_WCHAR (datetimeoffset)** |9,2,8|9, 3, 4, 8|9,4,8,10|9,8,10|9,10|–|–|  
| **SQL_C_BINARY(SQL_DATE_STRUCT)** |1,11|–|–|–|–|–|–|  
| **SQL_C_BINARY(SQL_TIME_STRUCT)** |–|–|–|–|–|–|–|  
| **SQL_C_BINARY(SQL_TIMESTAMP_STRUCT)** |–|–|–|–|–|–|–|  
  
## <a name="key-to-symbols"></a>Aufschlüsselung der Symbole  
  
-   **-**: Es wird keine Konvertierung unterstützt. Es wird ein Diagnosedatensatz mit SQLSTATE 07006 und der Meldung "Attributverletzung beschränkter Datentypen" generiert.  
  
-   **1**: Wenn die bereitgestellten Daten nicht gültig sind, wird ein Diagnosedaten Satz mit SQLSTATE 22007 und der Meldung "Ungültiges datetime-Format" generiert.  
  
-   **2**: Zeitfelder müssen 0 (null) sein, oder es wird ein Diagnosedaten Satz mit SQLSTATE 22008 und der Meldung "Abschneiden von Bruchteilen" generiert.  
  
-   **3**: Sekundenbruchteile müssen 0 (null) sein, oder es wird ein Diagnosedaten Satz mit SQLSTATE 22008 und der Meldung "Bruch Bruchteile" generiert.  
  
-   **4**: die Datums Komponente wird ignoriert.  
  
-   **5**: die Zeitzone wird auf die Zeitzone-Einstellung des Clients festgelegt.  
  
-   **6**: die Uhrzeit wird auf 0 (null) festgelegt.  
  
-   **7**: das Datum wird auf das aktuelle Datum festgelegt.  
  
-   **8**: die Uhrzeit wird von der Zeitzone des Clients in UTC konvertiert. Tritt während dieser Konvertierung ein Fehler auf, wird ein Diagnosedatensatz mit SQLSTATE 22008 und der Meldung "Überlauf im Datetime-Feld" generiert.  
  
-   **9**: die Zeichenfolge wird analysiert und in einen Date-, DateTime-, DateTimeOffset-oder Time-Wert konvertiert, je nach dem ersten Satzzeichen und dem vorhanden sein von verbleibenden Komponenten. Die Zeichenfolge wird dann in den Zieltyp konvertiert. Dabei wird nach den Regeln in der vorangehenden Tabelle für den Quelltyp vorgegangen, der von diesem Prozess ermittelt wird. Wenn bei der Analyse der Daten ein Fehler ermittelt wird, wird ein Diagnosedatensatz mit SQLSTATE 22018 und der Meldung "Ungültiger Zeichenwert für Konvertierungsangabe" generiert. Wenn die Jahresangabe außerhalb des vom datetime- und smalldatetime-Parameter unterstützten Bereichs liegt, wird ein Diagnosedatensatz mit SQLSTATE 22007 und der Meldung "Ungültiges datetime-Format" generiert.  
  
     Der Wert für datetimeoffset muss nach der Konvertierung in das UTC-Format innerhalb des gültigen Bereichs liegen und zwar selbst dann, wenn keine Konvertierung in UTC angefordert wird. Der Grund dafür ist, dass der TDS und der Server das Datum stets in datetimeoffset-Werte für UTC normalisieren, weshalb der Client prüfen muss, ob die Zeitkomponenten innerhalb des nach Konvertierung in UTC unterstützten Bereichs liegen. Wenn der Wert nicht innerhalb des unterstützten UTC-Bereichs liegt, wird ein Diagnosedatensatz mit SQLSTATE 22007 und der Meldung "Ungültiges datetime-Format" generiert.  
  
-   **10**: Wenn eine Kürzung mit Datenverlust auftritt, wird ein Diagnosedaten Satz mit SQLSTATE 22008 und der Meldung "Ungültiges Zeitformat" generiert. Dieser Fehler tritt auch dann auf, wenn der Wert außerhalb des Bereichs liegt, der vom UTC-Bereich, den der Server verwendet, dargestellt werden kann.  
  
-   **11**: Wenn die Byte Länge der Daten nicht der Größe der für den SQL-Typ benötigten Struktur entspricht, wird ein Diagnosedaten Satz mit SQLSTATE 22003 und der Meldung "numerischer Wert außerhalb des gültigen Bereichs" generiert.  
  
-   **12**: Wenn die Byte Länge der Daten 4 oder 8 beträgt, werden die Daten im unformatierten TDS smalldatetime-oder datetime-Format an den Server gesendet. Wenn die Bytelänge der Daten exakt mit der Größe von SQL_TIMESTAMP_STRUCT übereinstimmt, werden die Daten in das TDS-Format für datetime2 konvertiert.  
  
-   **13**: Wenn eine Kürzung mit Datenverlust auftritt, wird ein Diagnosedaten Satz mit SQLSTATE 22001 und der Meldung "String Data, Right truncated" generiert.  
  
     Die Anzahl der Ziffern für Sekundenbruchteile (Dezimalstellen) wird anhand der Größe der Ziel Spalte gemäß der folgenden Tabelle bestimmt:  
  
    |   | Implizierte Dezimalstellen | Implizierte Dezimalstellen |
    | - | ------------- | ------------- |
    | **Typ** | 0 | 1.. 9 |  
    |**SQL_C_TYPE_TIMESTAMP** |19|21..29|  
  
     Wenn die Sekundenbruchteile für SQL_C_TYPE_TIMESTAMP mit drei Ziffern ohne Datenverlust dargestellt werden können und die Spaltengröße 23 oder größer ist, werden genau drei Dezimalstellen für Sekundenbruchteile generiert. Dieses Verhalten stellt die Abwärtskompatibilität für Anwendungen sicher, die mit älteren ODBC-Treibern entwickelt wurden.  
  
     Für Spaltengrößen, die den Bereich in der Tabelle übersteigen, werden 9 Dezimalstellen impliziert. Diese Konvertierung sollte bis zu neun Dezimalstellen für Sekundenbruchteile ermöglichen, das von ODBC zugelassene Maximum.  
  
     Eine Spaltengröße von 0 (null) impliziert unendliche Größe für Zeichentypen mit variabler Länge in ODBC (9 Ziffern, sofern die 3-Ziffern-Regel für SQL_C_TYPE_TIMESTAMP nicht gilt). Die Angabe einer Spaltengröße von 0 (null) mit einem Zeichentyp fester Länge ist ein Fehler.  
  
-   **N/v**: vorhandenes [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und früheres Verhalten wird beibehalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datums-und Uhrzeit Verbesserungen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
