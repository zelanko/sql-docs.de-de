---
title: Abrufen einer Zeile von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetch function [ODBC], fetching a row of data
- cursors [ODBC], fetching rows
- result sets [ODBC], fetching
- fetches [ODBC], row of data
ms.assetid: 16d4a380-0d83-456b-aeee-f10738944e86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 012e454d03a0eb4ad16095353351d67e50d9586a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63061518"
---
# <a name="fetching-a-row-of-data"></a>Abrufen einer Datenzeile
Um eine Datenzeile abzurufen, eine Anwendung ruft **SQLFetch**. **SQLFetch** kann mit jeder Art von Cursors aufgerufen werden, es wird nur des Rowsetcursors in eine Richtung Vorwärtscursor jedoch. **SQLFetch** setzt den Cursor in die nächste Zeile und gibt die Daten für alle Spalten, die mit Aufrufen von gebunden waren **SQLBindCol**. Wenn sich der Cursor auf das Ende des Resultsets erreicht festgelegt, **SQLFetch** SQL_NO_DATA zurückgibt. Beispiele für die aufrufende **SQLFetch**, finden Sie unter [mithilfe von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 Genau wie **SQLFetch** implementiert treiberspezifische, jedoch die allgemeine Muster ist für den Treiber zum Abrufen der Daten für alle Spalten aus der Datenquelle gebundenen, konvertieren Sie ihn entsprechend den von der gebundenen Variablen, und platzieren Sie die konvertiert Daten in diesen Variablen. Wenn der Treiber nicht, alle Daten konvertieren kann, **SQLFetch** gibt einen Fehler zurück. Die Anwendung kann weiterhin Abrufen von Zeilen, die Daten für die aktuelle Zeile geht jedoch verloren. Was geschieht, um die Daten für ungebundene Spalten, hängt davon ab, die Treiber, aber die meisten Treiber entweder abzurufen und ihn verwerfen oder überhaupt nicht mehr abgerufen werden.  
  
 Der Treiber setzt auch die Werte der keine Längenindikator /-Puffer, die gebunden wurden. Wenn der Datenwert für eine Spalte NULL ist, legt der Treiber die entsprechenden Längen-/Indikatorpuffers auf SQL_NULL_DATA fest. Wenn der Wert nicht NULL ist, legt der Treiber den Längen-/Indikatorpuffers auf die Bytelänge der Daten nach der Konvertierung an. Wenn diese Länge nicht bestimmt werden kann wie in einigen Fällen die long-Daten, die von mehr als ein Funktionsaufruf abgerufen, wird der Treiber den Längen-/Indikatorpuffers auf SQL_NO_TOTAL an. Bei fester Länge-Datentypen wie Ganzzahlen und der Datenstrukturen ist die Bytelänge der Größe des Datentyps.  
  
 Für Daten mit variabler Länge, wie z. B. Zeichen- und Binärdaten überprüft der Treiber die Bytelänge der konvertierten Daten mit der Bytelänge des Puffers an die Spalte gebunden. der Länge des Puffers wird angegeben, der *Pufferlänge* -Argument in **SQLBindCol**. Wenn die Bytelänge der konvertierten Daten größer als die Bytelänge des Puffers ist, schneidet die Daten in den Puffer zu passen, gibt zurück, die ungekürzten Länge in den Längen-/Indikatorpuffer gibt SQL_SUCCESS_WITH_INFO zurück, und platziert SQLSTATE 01004 (Daten, die der Treiber abgeschnitten) bei der Diagnose. Die einzige Ausnahme hierbei ist, wenn ein Lesezeichen variabler Länge abgeschnitten wird, wenn vom **SQLFetch**, womit SQLSTATE 22001 (Zeichenfolgendaten, rechts abgeschnitten).  
  
 Daten fester Länge werden nie abgeschnitten, da der Treiber wird davon ausgegangen, dass die Größe des gebundenen Puffer die Größe des Datentyps. Abschneiden von Daten eher gering sein, da die Anwendung in der Regel einen Puffer, der groß genug für den gesamten Datenwert gebunden; Es bestimmt die erforderliche Größe aus den Metadaten. Allerdings kann die Anwendung explizit einen Puffer Binden dieser weiß, dass die um zu klein. Beispielsweise kann es abrufen und eine Beschreibung für die ersten 20 Zeichen oder die ersten 100 Zeichen einer langen Text-Spalte angezeigt werden.  
  
 Zeichendaten müssen Null-terminiert sein vom Treiber vor der Rückgabe an die Anwendung, auch wenn es abgeschnitten wurde. Die Null-Terminierungszeichen erfordert, dass Speicherplatz in der gebundenen Puffer jedoch nicht in die zurückgegebene Bytelänge enthalten ist. Nehmen wir beispielsweise an eine Anwendung verwendet die Zeichenfolge mit Zeichendaten im ASCII-Zeichensatz, ein Treiber ist 50 Zeichen mit Daten zurückgegeben und im Puffer der Anwendung ist 25 Byte lang. In der Anwendung Puffer kehrt der Treiber die ersten 24 Zeichen, gefolgt von einer Null-Terminierungszeichen zurück. In den Längen-/Indikatorpuffer wird eine Bytelänge von 50 zurückgegeben.  
  
 Die Anwendung kann die Anzahl der Zeilen im Resultset durch Festlegen der SQL_ATTR_MAX_ROWS-Anweisungsattribut, vor dem Ausführen der Anweisung, die das Ergebnis erstellt beschränken. Die Vorschau-Modus in einer Anwendung, die zum Formatieren von Berichten benötigt beispielsweise nur genügend Daten für die erste Seite des Berichts anzuzeigen. Beschränken die Größe des Resultsets, würde diese Funktion schneller ausgeführt. Dieses Anweisungsattribut dient zur Reduzierung des Netzwerkverkehrs und möglicherweise nicht von allen Treibern unterstützt.
