---
title: Konvertierungen von C-in SQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC], C to SQL
ms.assetid: 7ac098db-9147-4883-8da9-a58ab24a0d31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8179b9452852777bb6d2a06018d0bf86598a5bf8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63207016"
---
# <a name="conversions-from-c-to-sql"></a>Konvertierungen von C in SQL
  In diesem Thema werden Probleme zu berücksichtigen, bei der Konvertierung von C-Typen in aufgelistet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datum/Uhrzeit-Typen.  
  
 Die in der folgenden Tabelle beschriebenen Konvertierungen gelten für auf dem Client ausgeführte Konvertierungen. In Fällen, in denen der Client Bruchsekundengenauigkeit für einen Parameter angibt, die von der auf dem Server definierten abweicht, ist die Clientkonvertierung möglicherweise erfolgreich, jedoch gibt der Server einen Fehler zurück, wenn `SQLExecute` oder `SQLExecuteDirect` aufgerufen wird. Das rührt daher, dass ODBC jedes Abschneiden von Sekundenbruchteilen als Fehler wertet, während [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rundet. Beispielsweise wird gerundet, wenn Sie von `datetime2(6)` zu `datetime2(2)` wechseln. Werte der Datetime-Spalte werden auf 1/300 einer Sekunde gerundet, und für smalldatetime -Spalten werden Sekunden vom Server auf null festgelegt.  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
||SQL_TYPE_DATE|SQL_TYPE_TIME|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_SS_TIMSTAMPOFFSET|SQL_CHAR|SQL_WCHAR|  
|SQL_C_DATE|1|-|-|1,6|1,5,6|1,13|1,13|  
|SQL_C_TIME|-|1|1|1,7|1,5,7|1,13|1,13|  
|SQL_C_SS_TIME2|-|1,3|1,10|1,7|1,5,7|1,13|1,13|  
|SQL_C_BINARY(SQL_SS_TIME2_STRUCT)|Nicht zutreffend|Nicht zutreffend|1,10,11|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|  
|SQL_C_TYPE_TIMESTAMP|1,2|1,3,4|1,4,10|1,10|1,5,10|1,13|1,13|  
|SQL_C_SS_TIMESTAMPOFFSET|1,2,8|1,3,4,8|1,4,8,10|1,8,10|1,10|1,13|1,13|  
|SQL_C_BINARY(SQL_SS_TIMESTAMPOFFSET_STRUCT)|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|1,10,11|Nicht zutreffend|Nicht zutreffend|  
|SQL_C_CHAR/SQL_WCHAR (date)|9|9|9|9,6|9,5,6|Nicht zutreffend|Nicht zutreffend|  
|SQL_C_CHAR/SQL_WCHAR (time2)|9|9,3|9,10|9,7,10|9,5,7,10|Nicht zutreffend|Nicht zutreffend|  
|SQL_C_CHAR/SQL_WCHAR (datetime)|9,2|9,3,4|9,4,10|9,10|9,5,10|Nicht zutreffend|Nicht zutreffend|  
|SQL_C_CHAR/SQL_WCHAR (datetimeoffset)|9,2,8|9,3,4,8|9,4,8,10|9,8,10|9,10|Nicht zutreffend|Nicht zutreffend|  
|SQL_C_BINARY(SQL_DATE_STRUCT)|1,11|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|  
|SQL_C_BINARY(SQL_TIME_STRUCT)|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|  
|SQL_C_BINARY(SQL_TIMESTAMP_STRUCT)|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|  
  
## <a name="key-to-symbols"></a>Aufschlüsselung der Symbole  
  
|Symbol|Bedeutung|  
|------------|-------------|  
|-|Es wird keine Konvertierung unterstützt. Es wird ein Diagnosedatensatz mit SQLSTATE 07006 und der Meldung "Attributverletzung beschränkter Datentypen" generiert.|  
|1|Wenn die bereitgestellten Daten ungültig sind, wird ein Diagnosedatensatz mit SQLSTATE 22007 und der Meldung "Ungültiges datetime-Format" generiert.|  
|2|Time-Felder müssen den Wert null aufweisen, sonst wird ein Diagnosedatensatz mit SQLSTATE 22008 und der Meldung "Teilbereiche wurden abgeschnitten" generiert.|  
|3|Sekundenbruchteile müssen den Wert null aufweisen, sonst wird ein Diagnosedatensatz mit SQLSTATE 22008 und der Meldung "Teilbereiche wurden abgeschnitten" generiert.|  
|4|Die Datumskomponente wird ignoriert.|  
|5|Die Zeitzone wird auf die Zeitzone des Clients festgelegt.|  
|6|Die Uhrzeit wird auf 0 (Null) festgelegt.|  
|7|Das Datum wird auf das aktuelle Datum festgelegt.|  
|8|Die Zeit wird von der Zeitzone des Clients in die UTC konvertiert. Tritt während dieser Konvertierung ein Fehler auf, wird ein Diagnosedatensatz mit SQLSTATE 22008 und der Meldung "Überlauf im Datetime-Feld" generiert.|  
|9|Die Zeichenfolge wird analysiert und je nach dem ersten Satzzeichen und dem Vorhandensein weiterer Komponenten in einen date-, datetime-, datetimeoffset- oder time-Wert konvertiert. Die Zeichenfolge wird dann in den Zieltyp konvertiert. Dabei wird nach den Regeln in der vorangehenden Tabelle für den Quelltyp vorgegangen, der von diesem Prozess ermittelt wird. Wenn bei der Analyse der Daten ein Fehler ermittelt wird, wird ein Diagnosedatensatz mit SQLSTATE 22018 und der Meldung "Ungültiger Zeichenwert für Konvertierungsangabe" generiert. Wenn die Jahresangabe außerhalb des vom datetime- und smalldatetime-Parameter unterstützten Bereichs liegt, wird ein Diagnosedatensatz mit SQLSTATE 22007 und der Meldung "Ungültiges datetime-Format" generiert.<br /><br /> Der Wert für datetimeoffset muss nach der Konvertierung in das UTC-Format innerhalb des gültigen Bereichs liegen und zwar selbst dann, wenn keine Konvertierung in UTC angefordert wird. Der Grund dafür ist, dass der TDS und der Server das Datum stets in datetimeoffset-Werte für UTC normalisieren, weshalb der Client prüfen muss, ob die Zeitkomponenten innerhalb des nach Konvertierung in UTC unterstützten Bereichs liegen. Wenn der Wert nicht innerhalb des unterstützten UTC-Bereichs liegt, wird ein Diagnosedatensatz mit SQLSTATE 22007 und der Meldung "Ungültiges datetime-Format" generiert.|  
|10|Wenn es zum Abschneiden von Daten kommt, wird ein Diagnosedatensatz mit SQLSTATE 22008 und der Meldung "Ungültiges Zeitformat" generiert. Dieser Fehler tritt auch dann auf, wenn der Wert außerhalb des Bereichs liegt, der vom UTC-Bereich, den der Server verwendet, dargestellt werden kann.|  
|11|Wenn die Bytelänge der Daten nicht mit der Größe der Struktur übereinstimmt, die vom SQL-Typ benötigt wird, wird ein Diagnosedatensatz mit SQLSTATE 22003 und der Meldung "Numerischer Wert außerhalb des Gültigkeitsbereichs" generiert.|  
|12|Wenn die Bytelänge der Daten 4 oder 8 beträgt, werden die Daten im TDS-Rohformat smalldatetime oder datetime an den Server gesendet. Wenn die Bytelänge der Daten exakt mit der Größe von SQL_TIMESTAMP_STRUCT übereinstimmt, werden die Daten in das TDS-Format für datetime2 konvertiert.|  
|13|Wenn es zum Abschneiden von Daten kommt, wird ein Diagnosedatensatz mit SQLSTATE 22001 und der Meldung "Die Zeichenfolgedaten wurden rechts abgeschnitten" generiert.<br /><br /> Die Anzahl der Ziffern für Sekundenbruchteile (Dezimalstellen) wird von der Größe der Zielspalte gemäß dem folgenden bestimmt:<br /><br /> **Typ:** SQL_C_TYPE_TIMESTAMP<br /><br /> Implizierte Dezimalstellen<br /><br /> 0<br /><br /> 19<br /><br /> Implizierte Dezimalstellen<br /><br /> 1..9<br /><br /> 21..29<br /><br /> Wenn die Sekundenbruchteile für SQL_C_TYPE_TIMESTAMP mit drei Ziffern ohne Datenverlust dargestellt werden können und die Spaltengröße 23 oder größer ist, werden genau drei Dezimalstellen für Sekundenbruchteile generiert. Dieses Verhalten stellt die Abwärtskompatibilität für Anwendungen sicher, die mit älteren ODBC-Treibern entwickelt wurden.<br /><br /> Für Spaltengrößen, die den Bereich in der Tabelle übersteigen, werden 9 Dezimalstellen impliziert. Diese Konvertierung sollte bis zu neun Dezimalstellen für Sekundenbruchteile ermöglichen, das von ODBC zugelassene Maximum.<br /><br /> Eine Spaltengröße von 0 (null) impliziert unendliche Größe für Zeichentypen mit variabler Länge in ODBC (9 Ziffern, sofern die 3-Ziffern-Regel für SQL_C_TYPE_TIMESTAMP nicht gilt). Die Angabe einer Spaltengröße von 0 (null) mit einem Zeichentyp fester Länge ist ein Fehler.|  
|Nicht zutreffend|Das Verhalten von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und früheren Versionen ist beibehalten worden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](date-and-time-improvements-odbc.md)  
  
  
