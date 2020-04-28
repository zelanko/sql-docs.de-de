---
title: Leistungsprobleme bei Desktop-Daten Bank Treibern | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303501"
---
# <a name="desktop-database-driver-performance-issues"></a>Leistungsprobleme bei Desktop-Datenbanktreibern
Um die Kompatibilität mit vorhandenen ANSI-Anwendungen sicherzustellen, werden die Datentypen SQL_WCHAR, SQL_WVARCHAR und SQL_WLONGVARCHAR als SQL_CHAR, SQL_VARCHAR und SQL_LONGVARCHAR für Datenquellen von Microsoft Access 4,0 oder höher verfügbar gemacht. Die Datenquellen geben keine wide char-Datentypen zurück, aber die Daten müssen immer noch an Jet in wide char-Form gesendet werden. Es ist wichtig zu verstehen, dass die Konvertierung stattfindet, wenn ein SQL_C_CHAR Parameter oder eine Ergebnisspalte an einen SQL_CHAR-Datentyp in einer ANSI-Anwendung gebunden ist.  
  
 Diese Konvertierung kann im Hinblick auf den Arbeitsspeicher besonders ineffizient sein, wenn ein SQL_C_CHAR Typ an einen Parameter des Typs LONGVARCHAR gebunden ist. Da die Jet 4,0-Engine keine LONGTEXT-Parameterdaten streamen kann, muss ein Unicode-Konvertierungs Puffer zugeordnet werden, der doppelt so groß ist wie der SQL_C_CHAR ANSI-Puffers. Der effizienteste Mechanismus besteht darin, dass die Anwendung die Unicode-Konvertierung ausführt und den Parameter als Typ SQL_C_WCHAR bindet. Wenn ein Parameter als Data-at-Execution gekennzeichnet ist und die Daten in mehreren Aufrufen von SQLPutData bereitgestellt werden, wird ein LONGTEXT-Datenpuffer vergrößert. Eine Möglichkeit, um den Aufwand für das Vergrößern dieses "Put Data"-Puffers zu vermeiden, besteht darin, eine optionale Länge über SQL_DATA_AT_EXEC_LEN (x) anzugeben, wobei *x* die erwartete Länge von Bytes ist. Dadurch wird die Größe eines internen putdata-Puffers auf *x* Bytes initialisiert.  
  
> [!NOTE]  
>  Eine effiziente Möglichkeit zum Einfügen oder Aktualisieren von Long-Daten kann mithilfe von **SQLBulkOperations ()** oder **SQLSetPos ()** und durch Festlegen der Long-Daten auf SQL_DATA_AT_EXEC erreicht werden. (EXEC_LEN wird in diesem Fall ignoriert.) Daten können in Blöcken gestreamt werden, indem **SQLPutData** mehrmals aufgerufen wird. Dadurch werden die Daten effektiv an die Tabelle angehängt.  
  
 Wenn für eine Anwendung, die eine Jet 3,5-Datenbank über die Microsoft ODBC Desktop-Datenbanktreiber verwendet, ein Upgrade auf Version 4,0 durchgeführt wird, kann es zu Leistungseinbußen und einer verbesserten Workingsetgröße kommen Dies liegt daran, dass bei Version 3. die *x* -Datenbank wird mithilfe des neuen Treibers der Version 4,0 geöffnet. Jet 4,0 wird geladen. Wenn Jet 4,0 die Datenbank öffnet und erkennt, dass die Datenbank 3 ist. *x* -Version wird ein installier barer ISAM-Treiber geladen, der dem Laden der Jet 3,5-Engine entspricht. Um die Leistungs-und Größen Einbußen zu entfernen, wird Jet 3 angezeigt. die *x* -Datenbank sollte in eine Jet 4,0-Format Datenbank komprimiert werden. Dadurch wird das Laden von zwei Jet-Engines vermieden und der Codepfad zu den Daten minimiert.  
  
 Außerdem handelt es sich bei der Jet 4,0-Engine um eine Unicode-Engine. Alle Zeichen folgen werden in Unicode gespeichert und bearbeitet. Wenn eine ANSI-Anwendung auf eine Jet 3-Anwendung zugreift. *x* -Datenbank durch die Jet 4,0-Engine, werden die Daten von ANSI in Unicode und zurück in ANSI konvertiert. Wenn die Datenbank auf das Format Version 4,0 aktualisiert wird, werden die Zeichen folgen in Unicode konvertiert, und es wird eine Ebene der Zeichen folgen Konvertierung entfernt. Außerdem wird der Codepfad zu den Daten minimiert, indem nur eine Jet-Engine durchlaufen wird.
