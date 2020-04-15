---
title: Festlegen von Parameterwerten | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- parameter values [ODBC]
ms.assetid: 13e5da79-b60c-48d0-b467-773f481ef2a4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 923fd57f4308fb72aca2f829ccb9d7b884c12546
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299830"
---
# <a name="setting-parameter-values"></a>Festlegen von Parameterwerten
Um den Wert eines Parameters festzulegen, legt die Anwendung einfach den Wert der variablen gebundenen Variablen an den Parameter fest. Es ist nicht wichtig, wenn dieser Wert festgelegt wird, solange er festgelegt wird, bevor die Anweisung ausgeführt wird. Die Anwendung kann den Wert vor oder nach dem Binden der Variablen festlegen und den Wert beeinent, und sie kann den Wert beeinen mannsmäßig ändern. Wenn die Anweisung ausgeführt wird, ruft der Treiber einfach den aktuellen Wert der Variablen ab. Dies ist besonders nützlich, wenn eine vorbereitete Anweisung mehr als einmal ausgeführt wird. Die Anwendung legt bei jeder Ausführung der Anweisung neue Werte für einige oder alle Variablen fest. Ein Beispiel hierfür finden Sie unter [Vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md)weiter oben in diesem Abschnitt.  
  
 Wenn ein Längen-/Indikatorpuffer im Aufruf von **SQLBindParameter**gebunden wurde, muss er auf einen der folgenden Werte festgelegt werden, bevor die Anweisung ausgeführt wird:  
  
-   Die Bytelänge der Daten in der gebundenen Variable. Der Treiber überprüft diese Länge nur, wenn die Variable Zeichen oder Binärwert ist *(ValueType* ist SQL_C_CHAR oder SQL_C_BINARY).  
  
-   SQL_NTS. Die Daten sind eine null-terminierte Zeichenfolge.  
  
-   SQL_NULL_DATA. Der Datenwert ist NULL, und der Treiber ignoriert den Wert der gebundenen Variablen.  
  
-   SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros. Der Wert des Parameters soll mit **SQLPutData**gesendet werden. Weitere Informationen finden Sie unter [Senden langer Daten](../../../odbc/reference/develop-app/sending-long-data.md)weiter unten in diesem Abschnitt.  
  
 Die folgende Tabelle zeigt die Werte der gebundenen Variablen und den Längen-/Indikatorpuffer, den die Anwendung für eine Vielzahl von Parameterwerten festlegt.  
  
|Parameter<br /><br /> value|Parameter<br /><br /> (SQL)<br /><br /> Datentyp|Variable (C)<br /><br /> Datentyp|Wert in <br /><br /> Gebunden<br /><br /> Variable|Wert in <br /><br /> Länge/Indikator<br /><br /> buffer[d]|  
|-------------------------|-----------------------------------------|----------------------------------|-------------------------------------|----------------------------------------------------|  
|"ABC"|SQL_CHAR|SQL_C_CHAR|ABC-0[a]|SQL_NTS oder 3|  
|10|SQL_INTEGER|SQL_C_SLONG|10|--|  
|10|SQL_INTEGER|SQL_C_CHAR|10-0[a]|SQL_NTS oder 2|  
|13.00 Uhr|SQL_TYPE_TIME|SQL_C_TYPE_TIME|13,0,0[b]|--|  
|13.00 Uhr|SQL_TYPE_TIME|SQL_C_CHAR|'t '13:00:00'''0[a], [c]|SQL_NTS oder 14|  
|NULL|SQL_SMALLINT|SQL_C_SSHORT|--|SQL_NULL_DATA|  
  
 [a] "-0" steht für ein Null-Beendigungszeichen. Das Null-Terminierungszeichen ist nur erforderlich, wenn der Wert im Längen-/Indikatorpuffer SQL_NTS ist.  
  
 [b] Die Zahlen in dieser Liste sind die Zahlen, die in den Feldern der TIME_STRUCT-Struktur gespeichert sind.  
  
 [c] Die Zeichenfolge verwendet die ODBC-Datumsescapeklausel. Weitere Informationen finden Sie unter [Datum, Uhrzeit und Zeitstempelliterale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 [d] Treiber müssen diesen Wert immer überprüfen, um festzustellen, ob es sich um einen speziellen Wert handelt, z. B. SQL_NULL_DATA.  
  
 Was ein Treiber mit einem Parameterwert zur Ausführungszeit macht, ist treiberabhängig. Bei Bedarf konvertiert der Treiber den Wert aus dem Datentyp C und der Bytelänge der gebundenen Variablen in den SQL-Datentyp, die Genauigkeit und den Maßstab des Parameters. In den meisten Fällen sendet der Treiber dann den Wert an die Datenquelle. In einigen Fällen formatiert er den Wert als Text und fügt ihn in die SQL-Anweisung ein, bevor die Anweisung an die Datenquelle gesendet wird.
