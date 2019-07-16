---
title: Desktop Datenbankleistungsprobleme der Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], performance
- desktop database drivers [ODBC], performance
- Jet-based ODBC drivers [ODBC], performance
ms.assetid: 1a4c4b7e-9744-411f-9b6e-06dfdad92cf7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 660b7c123d0ddd0a3f1b972fa3b1dc153b15ed50
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071929"
---
# <a name="desktop-database-driver-performance-issues"></a>Leistungsprobleme bei Desktop-Datenbanktreibern
Um Kompatibilität mit vorhandenen ANSI-Anwendungen zu gewährleisten, werden die Datentypen SQL_WCHAR, SQL_WVARCHAR und SQL_WLONGVARCHAR als SQL_CHAR und SQL_VARCHAR, SQL_LONGVARCHAR für Microsoft Access 4.0 oder höher Datenquellen verfügbar gemacht. Die Datenquellen keine WIDE-CHAR-Datentypen zurückgeben aber die Daten noch müssen gesendet werden Jet im Formular Wide-Char. Es ist wichtig zu verstehen, dass die Konvertierung erfolgt, wenn eine Spalte des Typs SQL_C_CHAR, Parameter oder ein Ergebnis in eine SQL_CHAR-Datentyp in eine ANSI-Anwendung gebunden ist.  
  
 Diese Konvertierung kann insbesondere im Hinblick auf Arbeitsspeicher ineffizient sein, wenn ein Typ SQL_C_CHAR an einen Parameter vom Typ LONGVARCHAR gebunden ist. Da die Jet 4.0 Engine Stream LONGTEXT Parameterdaten kann, muss ein Unicode-Konvertierung Puffer zugeordnet werden, der zweimal der Größe des Puffers SQL_C_CHAR ANSI ist. Die effizienteste Methode ist für die Anwendung die UNICODE-Konvertierung durchführen, und binden Sie den Parameter als SQL_C_WCHAR-Typ. Wenn ein Parameter als Data-at-Execution-markiert ist, und die Daten in mehreren Aufrufen SQLPutData angegeben werden, wird ein Longtext Datenpuffer. Eine Möglichkeit, um die Kosten für die wachsende dies zu vermeiden "Put" Datenpuffer ist eine optionale Länge über SQL_DATA_AT_EXEC_LEN(x), angeben, in denen *x* ist die erwartete Länge des Bytes. Dies wird die Größe eines internen Puffers PutData zum Initialisieren *x* Bytes.  
  
> [!NOTE]  
>  Eine effiziente Möglichkeit zum Einfügen oder Aktualisieren von long-Daten kann erreicht werden, mithilfe von **SQLBulkOperations()** oder **SQLSetPos()** und die langen Daten auf SQL_DATA_AT_EXEC festlegen. (EXEC_LEN wird in diesem Fall ignoriert). Daten können in Blöcken gestreamt werden, durch den Aufruf **SQLPutData** mehrere Male, die effektiv fügt der das der Tabelle.  
  
 Wenn eine Anwendung mit einer Jet-3.5-Datenbank über den Microsoft ODBC Desktop-Datenbanktreiber, Version 4.0 aktualisiert wird, können es sich um eine leistungsbeeinträchtigung und eine höhere Größe des Workingsets auftreten. Grund hierfür ist, wenn eine Version 3. *x* Datenbank geöffnet wird, verwenden die neue Version 4.0-Treiber, lädt er Jet 4.0. Wenn Jet 4.0 wird die Datenbank geöffnet und angezeigt werden, ist die Datenbank eine 3. *x* Version geladen installierbare ISAM-Treiber, die zum Laden der Jet-3.5-Engine entspricht. So entfernen Sie die Leistung und Größe Leistungseinbußen, die Jet-3. *x* Datenbank in eine Datenbank Jet 4.0-Format komprimiert werden soll. Dies vermeiden, laden die zwei düsentriebwerken und Minimieren der Codepfad auf die Daten.  
  
 Darüber hinaus ist die Jet 4.0-Engine eine Unicode-Engine. Alle Zeichenfolgen gespeichert und im Unicode-Format bearbeitet. Wenn eine ANSI-Anwendung ein Jet-3 zugreift. *x* Datenbank durch das Jet 4.0-Modul, die Daten wird von ANSI in Unicode und zurück zu ANSI konvertiert. Wenn die Datenbank in das Versionsformat 4.0 aktualisiert wird, werden die Zeichenfolgen in Unicode, entfernen eine Ebene der zeichenfolgenkonvertierung sowie zum Minimieren der Codepfad auf die Daten mithilfe nur ein Jet-Modul konvertiert.
