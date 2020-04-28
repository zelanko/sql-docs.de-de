---
title: Festlegen von Parameter Werten | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299830"
---
# <a name="setting-parameter-values"></a>Festlegen von Parameterwerten
Um den Wert eines Parameters festzulegen, legt die Anwendung einfach den Wert der Variablen fest, die an den-Parameter gebunden ist. Es ist nicht wichtig, wenn dieser Wert festgelegt wird, solange er festgelegt wird, bevor die-Anweisung ausgeführt wird. Die Anwendung kann den Wert vor oder nach dem Binden der Variablen festlegen, und Sie kann den Wert beliebig oft ändern. Wenn die-Anweisung ausgeführt wird, ruft der Treiber einfach den aktuellen Wert der Variablen ab. Dies ist besonders nützlich, wenn eine vorbereitete Anweisung mehrmals ausgeführt wird. bei jeder Ausführung der Anweisung werden von der Anwendung neue Werte für einige oder alle Variablen festgelegt. Ein Beispiel hierfür finden Sie weiter oben in diesem Abschnitt unter [vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
 Wenn beim Aufrufen von **SQLBindParameter**ein Längen-/Indikatorpuffer gebunden wurde, muss dieser vor der Ausführung der Anweisung auf einen der folgenden Werte festgelegt werden:  
  
-   Die Byte Länge der Daten in der gebundenen Variablen. Der Treiber prüft diese Länge nur, wenn die Variable den Wert "Character" oder "Binary" aufweist (*ValueType* ist SQL_C_CHAR oder SQL_C_BINARY).  
  
-   SQL_NTS. Die Daten sind eine NULL terminierte Zeichenfolge.  
  
-   SQL_NULL_DATA. Der Datenwert ist NULL, und der Treiber ignoriert den Wert der gebundenen Variablen.  
  
-   SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros. Der Wert des-Parameters muss mit **SQLPutData**gesendet werden. Weitere Informationen finden Sie weiter unten in diesem Abschnitt unter [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md).  
  
 In der folgenden Tabelle werden die Werte der gebundenen Variablen und der Längen-/Indikatorpuffer angezeigt, der von der Anwendung für eine Vielzahl von Parameterwerten festgelegt wird.  
  
|Parameter<br /><br /> value|Parameter<br /><br /> SQL<br /><br /> Datentyp|Variable (C)<br /><br /> Datentyp|Wert in <br /><br /> binden<br /><br /> Variable|Wert in <br /><br /> Länge/Indikator<br /><br /> Puffer [d]|  
|-------------------------|-----------------------------------------|----------------------------------|-------------------------------------|----------------------------------------------------|  
|"ABC"|SQL_CHAR|SQL_C_CHAR|Abc\0 [a]|SQL_NTS oder 3|  
|10|SQL_INTEGER|SQL_C_SLONG|10|--|  
|10|SQL_INTEGER|SQL_C_CHAR|10 \ 0 [a]|SQL_NTS oder 2|  
|1 Uhr|SQL_TYPE_TIME|SQL_C_TYPE_TIME|13, 0, 0 [b]|--|  
|1 Uhr|SQL_TYPE_TIME|SQL_C_CHAR|{t ' 13:00:00 '} \ 0 [a], [c]|SQL_NTS oder 14|  
|NULL|SQL_SMALLINT|SQL_C_SSHORT|--|SQL_NULL_DATA|  
  
 [a] "\ 0" stellt ein NULL-Terminierungs Zeichen dar. Das NULL-Terminierungs Zeichen ist nur erforderlich, wenn der Wert im Längen-/Indikatorpuffer SQL_NTS ist.  
  
 [b] die Zahlen in dieser Liste sind die Zahlen, die in den Feldern der TIME_STRUCT Struktur gespeichert werden.  
  
 [c] die Zeichenfolge verwendet die ODBC Date Escape-Klausel. Weitere Informationen finden Sie unter [Date-, Time-und Timestamp-Literale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 [d] Treiber müssen diesen Wert immer überprüfen, um festzustellen, ob es sich um einen speziellen Wert handelt, z. b. SQL_NULL_DATA.  
  
 Ein Treiber, der zur Ausführungszeit einen Parameterwert verwendet, ist Treiber abhängig. Falls erforderlich, konvertiert der Treiber den Wert des C-Datentyps und die Byte Länge der gebundenen Variablen in den SQL-Datentyp, die Genauigkeit und die Dezimal Größe des Parameters. In den meisten Fällen sendet der Treiber den Wert an die Datenquelle. In einigen Fällen wird der Wert als Text formatiert und in die SQL-Anweisung eingefügt, bevor die Anweisung an die Datenquelle gesendet wird.
