---
description: Abrufen einer Datenzeile
title: Abrufen einer Daten Zeile | Microsoft-Dokumentation
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
ms.openlocfilehash: 71ced7d7df30f1bb4f784317b76f7b42553951df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499890"
---
# <a name="fetching-a-row-of-data"></a>Abrufen einer Datenzeile
Zum Abrufen einer Daten Zeile Ruft eine Anwendung **SQLFetch**auf. **SQLFetch** kann mit jeder Art von Cursor aufgerufen werden, aber der rowsetcursor wird nur in Vorwärtsrichtung verschoben. **SQLFetch** verschiebt den Cursor auf die nächste Zeile und gibt die Daten für alle Spalten zurück, die mit Aufrufen von **SQLBindCol**gebunden wurden. Wenn der Cursor das Ende des Resultsets erreicht, gibt **SQLFetch** SQL_NO_DATA zurück. Beispiele zum Aufrufen von **SQLFetch**finden [Sie unter Verwenden von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 Die Implementierung von **SQLFetch** ist Treiber spezifisch, aber das allgemeine Muster besteht darin, dass der Treiber die Daten für alle gebundenen Spalten aus der Datenquelle abruft, diese gemäß den Typen der gebundenen Variablen konvertiert und die konvertierten Daten in diese Variablen platziert. Wenn der Treiber keine Daten konvertieren kann, gibt **SQLFetch** einen Fehler zurück. Die Anwendung kann das Abrufen von Zeilen fortsetzen, aber die Daten für die aktuelle Zeile gehen verloren. Was mit den Daten für ungebundene Spalten passiert, hängt vom Treiber ab, aber die meisten Treiber rufen Sie ab und verwerfen Sie, oder Sie werden überhaupt nie abgerufen.  
  
 Der Treiber legt auch die Werte aller Längen-/Indikatorpuffer fest, die gebunden wurden. Wenn der Datenwert für eine Spalte NULL ist, legt der Treiber den entsprechenden Längen-/Indikatorpuffer auf SQL_NULL_DATA fest. Wenn der Datenwert nicht NULL ist, legt der Treiber den Längen-/Indikatorpuffer auf die Byte Länge der Daten nach der Konvertierung fest. Wenn diese Länge nicht bestimmt werden kann, wie es manchmal bei langen Daten der Fall ist, die von mehr als einem Funktions aufgerufenen abgerufen werden, legt der Treiber den Längen-/Indikatorpuffer auf SQL_NO_TOTAL fest. Für Datentypen mit fester Länge, wie z. b. ganze Zahlen und Datums Strukturen, entspricht die Byte Länge der Größe des Datentyps.  
  
 Bei Daten variabler Länge (z. b. Zeichen-und Binärdaten) überprüft der Treiber die Byte Länge der konvertierten Daten anhand der Byte Länge des an die Spalte gebundenen Puffers. die Länge des Puffers wird im *BufferLength* -Argument in **SQLBindCol**angegeben. Wenn die Byte Länge der konvertierten Daten größer als die Byte Länge des Puffers ist, verkürzt der Treiber die Daten so, dass Sie in den Puffer passen, gibt die nicht gekürzte Länge im Längen-/Indikatorpuffer zurück, gibt SQL_SUCCESS_WITH_INFO zurück und platziert SQLSTATE 01004 (abgeschnittene Daten) in der Diagnose. Die einzige Ausnahme besteht darin, dass ein Lesezeichen variabler Länge abgeschnitten wird, wenn es von **SQLFetch**zurückgegeben wird, das SQLSTATE 22001 (Zeichen folgen Daten, rechts abgeschnitten) zurückgibt.  
  
 Daten fester Länge werden nie abgeschnitten, da der Treiber annimmt, dass die Größe des gebundenen Puffers die Größe des Datentyps angibt. Das Abschneiden von Daten ist tendenziell selten, da die Anwendung in der Regel einen Puffer bindet, der für den gesamten Datenwert groß genug ist. Es bestimmt die erforderliche Größe aus den Metadaten. Allerdings kann die Anwendung einen zu kleinen Puffer explizit binden. Beispielsweise können die ersten 20 Zeichen einer Teilebeschreibung oder die ersten 100 Zeichen einer langen Text Spalte abgerufen und angezeigt werden.  
  
 Zeichendaten müssen vom Treiber NULL-terminiert werden, bevor Sie an die Anwendung zurückgegeben werden, auch wenn Sie abgeschnitten wurden. Das NULL-Terminierungs Zeichen ist nicht in der zurückgegebenen Byte Länge enthalten, erfordert jedoch Platz im gebundenen Puffer. Angenommen, eine Anwendung verwendet Zeichen folgen, die aus Zeichendaten im ASCII-Zeichensatz bestehen, ein Treiber hat 50 Zeichen von Daten, die zurückgegeben werden sollen, und der Puffer der Anwendung ist 25 Bytes lang. Im Puffer der Anwendung gibt der Treiber die ersten 24 Zeichen gefolgt von einem NULL-Terminierungs Zeichen zurück. Im Längen-/Indikatorpuffer wird eine Byte Länge von 50 zurückgegeben.  
  
 Die Anwendung kann die Anzahl der Zeilen im Resultset einschränken, indem das SQL_ATTR_MAX_ROWS Anweisungs Attribut festgelegt wird, bevor die Anweisung ausgeführt wird, mit der das Resultset erstellt wird. Der Vorschaumodus in einer Anwendung, die zum Formatieren von Berichten verwendet wird, benötigt z. b. nur genügend Daten, um die erste Seite des Berichts anzuzeigen. Durch Einschränkung der Größe des Resultsets würde eine solche Funktion schneller ausgeführt werden. Dieses Anweisungs Attribut dient dazu, den Netzwerk Datenverkehr zu reduzieren, und wird möglicherweise nicht von allen Treibern unterstützt.
