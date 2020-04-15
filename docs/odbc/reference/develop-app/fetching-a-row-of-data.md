---
title: Abrufen einer Datenzeile | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a702f561b756d5305020df9f015d3ea4b444caa6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305671"
---
# <a name="fetching-a-row-of-data"></a>Abrufen einer Datenzeile
Um eine Datenzeile abzurufen, ruft eine Anwendung **SQLFetch**auf. **SQLFetch** kann mit jeder Art von Cursor aufgerufen werden, aber es verschiebt den Rowset-Cursor nur in eine Vorwärts-Richtung. **SQLFetch** verschiebt den Cursor zur nächsten Zeile und gibt die Daten für alle Spalten zurück, die mit Aufrufen von **SQLBindCol**gebunden wurden. Wenn der Cursor das Ende des Resultsets erreicht, gibt **SQLFetch** SQL_NO_DATA zurück. Beispiele für das Aufrufen von **SQLFetch**finden Sie unter [Verwenden von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 Genau wie **SQLFetch** implementiert wird, ist treiberspezifisch, aber das allgemeine Muster besteht darin, dass der Treiber die Daten für alle gebundenen Spalten aus der Datenquelle abruft, sie entsprechend den Typen der gebundenen Variablen konvertiert und die konvertierten Daten in diesen Variablen platziert. Wenn der Treiber keine Daten konvertieren kann, gibt **SQLFetch** einen Fehler zurück. Die Anwendung kann weiterhin Zeilen abrufen, aber die Daten für die aktuelle Zeile gehen verloren. Was mit den Daten für ungebundene Spalten geschieht, hängt vom Treiber ab, aber die meisten Treiber rufen sie ab und verwerfen sie oder rufen sie nie ab.  
  
 Der Treiber legt auch die Werte aller Längen-/Indikatorpuffer fest, die gebunden wurden. Wenn der Datenwert für eine Spalte NULL ist, legt der Treiber den entsprechenden Längen-Indikator-Puffer auf SQL_NULL_DATA. Wenn der Datenwert nicht NULL ist, legt der Treiber den Längen-/Indikatorpuffer nach der Konvertierung auf die Bytelänge der Daten fest. Wenn diese Länge nicht bestimmt werden kann, wie es manchmal bei langen Daten der Fall ist, die von mehr als einem Funktionsaufruf abgerufen werden, legt der Treiber den Längen-/Indikatorpuffer auf SQL_NO_TOTAL. Bei Datentypen fester Länge, z. B. Ganzzahlen und Datumsstrukturen, ist die Bytelänge die Größe des Datentyps.  
  
 Bei Daten variabler Länge, z. B. Zeichen- und Binärdaten, überprüft der Treiber die Bytelänge der konvertierten Daten mit der Bytelänge des an die Spalte gebundenen Puffers. Die Länge des Puffers wird im *Argument BufferLength* in **SQLBindCol**angegeben. Wenn die Bytelänge der konvertierten Daten größer als die Bytelänge des Puffers ist, kürt der Treiber die Daten, um in den Puffer zu passen, gibt die nicht abgeschnittene Länge im Längen-Indikator-Puffer zurück, gibt SQL_SUCCESS_WITH_INFO zurück und platziert SQLSTATE 01004 (Data abgeschnitten) in der Diagnose. Die einzige Ausnahme besteht darin, dass ein Lesezeichen mit variabler Länge abgeschnitten wird, wenn es von **SQLFetch**zurückgegeben wird, das SQLSTATE 22001 zurückgibt (Zeichenfolgendaten, rechts abgeschnitten).  
  
 Daten fester Länge werden nie abgeschnitten, da der Treiber davon ausgeht, dass die Größe des gebundenen Puffers die Größe des Datentyps ist. Datenkürzungen sind in der Regel selten, da die Anwendung in der Regel einen Puffer bindet, der groß genug ist, um den gesamten Datenwert zu halten. Die erforderliche Größe wird anhand der Metadaten bestimmt. Die Anwendung kann jedoch explizit einen Puffer binden, von dem sie weiß, dass er zu klein ist. Sie kann z. B. die ersten 20 Zeichen einer Teilebeschreibung oder die ersten 100 Zeichen einer langen Textspalte abrufen und anzeigen.  
  
 Zeichendaten müssen vom Treiber null beendet werden, bevor sie an die Anwendung zurückgegeben werden, auch wenn sie abgeschnitten wurden. Das NULL-Beendigungszeichen ist nicht in der zurückgegebenen Bytelänge enthalten, erfordert jedoch Platz im gebundenen Puffer. Angenommen, eine Anwendung verwendet Zeichenfolgen, die aus Zeichendaten im ASCII-Zeichensatz bestehen, ein Treiber hat 50 Zeichen von Daten zurückzugeben, und der Puffer der Anwendung ist 25 Byte lang. Im Puffer der Anwendung gibt der Treiber die ersten 24 Zeichen gefolgt von einem Null-Beendigungszeichen zurück. Im Längen-/Indikatorpuffer gibt er eine Bytelänge von 50 zurück.  
  
 Die Anwendung kann die Anzahl der Zeilen im Resultset einschränken, indem sie das Attribut SQL_ATTR_MAX_ROWS-Anweisung festlegt, bevor die Anweisung ausgeführt wird, die das Resultset erstellt. Beispielsweise benötigt der Vorschaumodus in einer Anwendung, die zum Formatieren von Berichten verwendet wird, nur genügend Daten, um die erste Seite des Berichts anzuzeigen. Durch die Beschränkung der Größe des Resultsets würde eine solche Funktion schneller ausgeführt. Dieses Anweisungsattribut soll den Netzwerkverkehr reduzieren und wird möglicherweise nicht von allen Treibern unterstützt.
