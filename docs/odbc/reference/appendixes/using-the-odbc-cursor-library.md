---
title: Die ODBC-Cursorbibliothek mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], using cursor library
- cursor library [ODBC], using cursor library
ms.assetid: 9653f2f8-ccfc-4220-99ef-601dc0fa641c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9fe19efb2d39e875cdafec76f2c50164f3a66f03
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62735024"
---
# <a name="using-the-odbc-cursor-library"></a>Verwenden der ODBC-Cursorbibliothek
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 So verwenden Sie die ODBC-Cursorbibliothek, eine Anwendung:  
  
1.  Aufrufe **SQLSetConnectAttr** mit einer *Attribut* von SQL_ATTR_ODBC_CURSORS angeben, wie die Cursorbibliothek mit einer bestimmten Verbindung verwendet werden soll. Die Cursorbibliothek immer möglich verwendet (SQL_CUR_USE_ODBC), nur verwendet, wenn Treiber scrollfähige Cursor (SQL_CUR_USE_IF_NEEDED) nicht unterstützt oder noch nie verwendet (SQL_CUR_USE_DRIVER).  
  
2.  Aufrufe **SQLConnect**, **SQLDriverConnect**, oder **SQLBrowseConnect** für die Verbindung mit der Datenquelle.  
  
3.  Aufrufe **SQLSetStmtAttr** zum Angeben der Cursor-Datentyp (SQL_ATTR_CURSOR_TYPE), die Parallelität (SQL_ATTR_CONCURRENCY) und die Rowsetgröße (SQL_ATTR_ROW_ARRAY_SIZE). Die Cursorbibliothek unterstützt Vorwärtscursor und statische Cursor. Vorwärtscursor müssen schreibgeschützt sein, während statische Cursor schreibgeschützt sein können, oder können die Steuerung für optimistische Parallelität Vergleichen von Werten verwenden.  
  
4.  Ordnet eine oder mehrere Rowsets Puffer und Aufrufe **SQLBindCol** einmal oder mehrmals, um diese Puffer zu Spalten führt zu binden.  
  
5.  Generiert ein Resultset, die durch Ausführen einer **wählen** -Anweisung oder Prozedur, oder durch Aufrufen einer Katalogfunktion. Wenn die Anwendung positionierte Update-Anweisungen ausgeführt wird, führen sie eine **wählen Sie für UPDATE** Anweisung, um das Resultset zu generieren.  
  
6.  Aufrufe **SQLFetch** oder **SQLFetchScroll** einmal oder mehrmals, einen Bildlauf durch das Resultset.  
  
 Die Anwendung kann Datenwerte in den Puffern Rowset ändern. Um die Rowset-Puffer mit Daten aus der Cursorbibliothek-Cache zu aktualisieren, eine Anwendung ruft **SQLFetchScroll** mit der *FetchOrientation* -Argument auf SQL_FETCH_RELATIVE festgelegt und die  *FetchOffset* Argument auf 0 festgelegt.  
  
 Zum Abrufen von Daten aus einer ungebundenen Spalte, die Anwendung ruft **SQLSetPos** zur Positionierung des Cursors in der gewünschten Zeile. Es ruft dann **SQLGetData** zum Abrufen der Daten.  
  
 Um die Anzahl der Zeilen zu bestimmen, die aus der Datenquelle abgerufen wurden, ruft die Anwendung **SQLRowCount**.
