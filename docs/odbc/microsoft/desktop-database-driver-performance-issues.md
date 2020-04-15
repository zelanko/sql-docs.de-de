---
title: Probleme mit der Desktopdatenbanktreiberleistung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a819d99a995fd7b287beb66b94f1df526e05f201
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303501"
---
# <a name="desktop-database-driver-performance-issues"></a>Leistungsprobleme bei Desktop-Datenbanktreibern
Um die Kompatibilität mit vorhandenen ANSI-Anwendungen sicherzustellen, werden die Datentypen SQL_WCHAR, SQL_WVARCHAR und SQL_WLONGVARCHAR als SQL_CHAR, SQL_VARCHAR und SQL_LONGVARCHAR für Microsoft Access 4.0-Datenquellen verfügbar gemacht. Die Datenquellen geben keine WIDE CHAR-Datentypen zurück, aber die Daten müssen weiterhin in Wide Char-Form an Jet gesendet werden. Es ist wichtig zu verstehen, dass die Konvertierung stattfindet, wenn ein SQL_C_CHAR Parameter oder eine Ergebnisspalte an einen SQL_CHAR Datentyp in einer ANSI-Anwendung gebunden ist.  
  
 Diese Konvertierung kann in Bezug auf den Arbeitsspeicher besonders ineffizient sein, wenn ein SQL_C_CHAR Typ an einen Parameter vom Typ LONGVARCHAR gebunden ist. Da das Jet 4.0-Modul keine LONGTEXT-Parameterdaten streamen kann, muss ein UNICODE-Konvertierungspuffer zugewiesen werden, der doppelt so groß ist wie der SQL_C_CHAR ANSI-Puffer. Der effizienteste Mechanismus besteht darin, dass die Anwendung die UNICODE-Konvertierung durchführt und den Parameter als Typ SQL_C_WCHAR bindet. Wenn ein Parameter als Data-at-Execution markiert ist und die Daten in mehreren Aufrufen von SQLPutData bereitgestellt werden, wird ein Longtext-Datenpuffer vergrößert. Eine Möglichkeit, die Kosten für das Wachstum dieses "Put Data"-Puffers zu vermeiden, besteht darin, eine optionale Länge über SQL_DATA_AT_EXEC_LEN(x) anzugeben, wobei *x* die erwartete Länge von Bytes ist. Dadurch wird die Größe eines internen PutData-Puffers in *x* Bytes initialisiert.  
  
> [!NOTE]  
>  Eine effiziente Möglichkeit zum Einfügen oder Aktualisieren langer Daten kann mithilfe von **SQLBulkOperations()** oder **SQLSetPos()** durchgeführt und die langen Daten auf SQL_DATA_AT_EXEC festgelegt werden. (EXEC_LEN wird in diesem Fall ignoriert.) Daten können in Blöcken gestreamt werden, indem **SQLPutData** mehrmals aufgerufen wird, wodurch die Daten effektiv an die Tabelle angehängt werden.  
  
 Wenn eine Anwendung, die eine Jet 3.5-Datenbank über die Microsoft ODBC-Desktopdatenbanktreiber verwendet, auf Version 4.0 aktualisiert wird, kann es zu leistungsbeeinträchtigenden und erhöhten Arbeitssatzgrößen kommen. Dies ist, wenn eine Version 3. *X-Datenbank* wird mit dem neuen Treiber Version 4.0 geöffnet, es lädt Jet 4.0. Wenn Jet 4.0 die Datenbank öffnet und sieht, dass es sich bei der Datenbank um eine 3 handelt. *x-Version* lädt es einen installierbaren ISAM-Treiber, der dem Laden des Jet 3.5-Motors entspricht. Um die Leistungs- und Größenbeschränkung zu entfernen, wird der Jet 3. *x-Datenbank* sollte in eine Jet 4.0-Datenbank komprimiert werden. Dadurch wird das Laden von zwei Jet-Triebwerken eliminiert und der Codepfad zu den Daten minimiert.  
  
 Außerdem ist der Jet 4.0-Motor ein Unicode-Motor. Alle Zeichenfolgen werden in Unicode gespeichert und bearbeitet. Wenn eine ANSI-Anwendung auf einen Jet 3 zugreift. *x-Datenbank* über das Jet 4.0-Modul werden die Daten von ANSI in Unicode und zurück in ANSI konvertiert. Wenn die Datenbank auf das Format Version 4.0 aktualisiert wird, werden die Zeichenfolgen in Unicode konvertiert, wodurch eine Ebene der Zeichenfolgenkonvertierung entfernt wird und der Codepfad zu den Daten minimiert wird, indem nur ein Jet-Modul durchlaufen wird.
