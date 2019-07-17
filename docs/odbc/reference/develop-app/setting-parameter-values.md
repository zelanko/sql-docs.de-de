---
title: Festlegen von Parameterwerten | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0bb1115290f53c19fae1aacb0a976cfcef63e086
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094236"
---
# <a name="setting-parameter-values"></a>Festlegen von Parameterwerten
Um den Wert eines Parameters festlegen, wird die Anwendung einfach der Wert der an den Parameter gebundenen Variablen. Es ist nicht wichtig, wenn dieser Wert festgelegt ist, solange sie festgelegt ist, bevor die Anweisung ausgeführt wird. Die Anwendung kann den Wert festlegen, vor oder nach der Bindung der Variablen, und kann den Wert so oft wie sollen sich ändern. Wenn die Anweisung ausgeführt wird, ruft der Treiber einfach den aktuellen Wert der Variablen ab. Dies ist besonders nützlich, wenn mehr als einmal eine vorbereitete Anweisung ausgeführt wird; die Anwendung legt neue Werte für einige oder alle Variablen jedes Mal, wenn die Anweisung ausgeführt wird. Ein Beispiel hierfür finden Sie unter [vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md)weiter oben in diesem Abschnitt.  
  
 Wenn im Aufruf an ein Längen-/Indikatorpuffer gebunden war **SQLBindParameter**, es muss auf einen der folgenden Werte festgelegt werden, bevor die Anweisung ausgeführt wird:  
  
-   Die Bytelänge der Daten in die gebundene Variable. Der Treiber überprüft diese Länge nur dann, wenn die Variable Zeichen- oder Binärdatentyp ist (*ValueType* ist SQL_C_CHAR oder sql_c_binary angegeben).  
  
-   SQL_NTS. Die Daten sind ein Null-terminierte Zeichenfolge.  
  
-   SQL_NULL_DATA. Der Datenwert NULL ist, und der Treiber ignoriert den Wert der gebundenen Variablen.  
  
-   SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC Makros. Der Wert des Parameters mit gesendet werden **SQLPutData**. Weitere Informationen finden Sie unter [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md)weiter unten in diesem Abschnitt.  
  
 Die folgende Tabelle zeigt die Werte für die gebundene Variable und den Längen-/Indikatorpuffer, den die Anwendung für eine Vielzahl von Parameterwerten festlegt.  
  
|Parameter<br /><br /> Wert|Parameter<br /><br /> (SQL)<br /><br /> Datentyp|Variable (C)<br /><br /> Datentyp|Wert in<br /><br /> Gebunden<br /><br /> variable|Wert in<br /><br /> Längenindikator /<br /><br /> Puffer [d]|  
|-------------------------|-----------------------------------------|----------------------------------|-------------------------------------|----------------------------------------------------|  
|"ABC"|SQL_CHAR|SQL_C_CHAR|ABC\0[a]|SQL_NTS lauten oder 3|  
|10|SQL_INTEGER|SQL_C_SLONG|10|--|  
|10|SQL_INTEGER|SQL_C_CHAR|10\0 [a]|SQL_NTS lauten oder 2|  
|UM 13 UHR|SQL_TYPE_TIME|SQL_C_TYPE_TIME|13,0,0 [b]|--|  
|UM 13 UHR|SQL_TYPE_TIME|SQL_C_CHAR|{t ' 13: 00:00'} \0 [a], [c]|SQL_NTS lauten oder 14|  
|NULL|SQL_SMALLINT|SQL_C_SSHORT|--|SQL_NULL_DATA|  
  
 [a] "\0" stellt einen Null-Terminierungszeichen dar. Die Null-Terminierungszeichen ist erforderlich, nur dann, wenn der Wert in den Längen-/Indikatorpuffer SQL_NTS ist.  
  
 [b] die Zahlen in dieser Liste sind die Zahlen in den Feldern der TIME_STRUCT Struktur gespeichert.  
  
 [c] die Zeichenfolge, verwendet der ODBC-Datum-Escape-Klausel. Weitere Informationen finden Sie unter [Date, Time und Timestamp-Literale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 [d] Treiber müssen immer überprüfen Sie diesen Wert, um festzustellen, ob es sich um einen speziellen Wert, z. B. SQL_NULL_DATA ist.  
  
 Funktionsweise von ein Treiber mit einem Parameterwert zum Zeitpunkt der Ausführung ist treiberabhängig. Bei Bedarf konvertiert der Treiber den Wert aus der C-Typ und die Byte Datenlänge die gebundene Variable in der SQL-Datentyp, Genauigkeit und Dezimalstellen des Parameters an. In den meisten Fällen sendet der Treiber klicken Sie dann den Wert mit der Datenquelle verwendet wird. In einigen Fällen es formatiert den Wert als Text und fügt sie in der SQL-Anweisung vor dem Senden der Anweisung an die Datenquelle ein.
