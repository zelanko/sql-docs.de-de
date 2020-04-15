---
title: Unterstütztes Cursormodell (Visual FoxPro ODBC-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], cursors
- cursors [ODBC], Visual FoxPro ODBC driver
- FoxPro ODBC driver [ODBC], cursors
- static cursors [ODBC]
- block cursors [ODBC]
- rowset cursors [ODBC]
ms.assetid: be95bbb2-6886-491e-a5a7-f58028d19c1e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cf3400f24e20a8fa864404612bf07ea44efce49e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301126"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Unterstütztes Cursormodell (Visual FoxPro-ODBC-Treiber)
Der Visual FoxPro ODBC-Treiber unterstützt sowohl *Block-* *als*auch *statische* Cursor. Statische Cursor werden für alle Treiber unterstützt, die der ODBC-Konformität der Stufe 1 entsprechen. Der Treiber unterstützt keine dynamischen, Keyset-gesteuerten oder gemischten (Keyset- und dynamischen) Cursor.  
  
 Ihre Anwendung kann [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) mit einer SQL_CURSOR_TYPE Option SQL_CURSOR_FORWARD_ONLY (Blockcursor) oder SQL_CURSOR_STATIC (statischer Cursor) aufrufen.  
  
> [!NOTE]  
>  Wenn Sie **SQLSetStmtOption** mit einer anderen SQL_CURSOR_TYPE Option als SQL_CURSOR_FORWARD_ONLY oder SQL_CURSOR_STATIC aufrufen, gibt die Funktion SQL_SUCCESS_WITH_INFO mit einem SQLSTATE von 01S02 zurück (Optionswert geändert). Der Treiber legt alle nicht unterstützten Cursormodi auf SQL_CURSOR_STATIC.  
  
 Weitere Informationen zu Cursortypen und **zu SQLSetStmtOption**finden Sie in der [ODBC-Programmiererreferenz](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>Blockcursor  
 Ein vorwärts scrollendes, schreibgeschütztes Resultset wurde an den Client zurückgegeben, der für die Verwaltung des Speichers für die Daten verantwortlich ist.  
  
## <a name="static-cursor"></a>Statischer Cursor  
 Eine Momentaufnahme eines Datensatzes, der von der Abfrage definiert wird. Statische Cursor spiegeln keine Echtzeitänderungen der zugrunde liegenden Daten durch andere Benutzer wider. Der Speicherpuffer des Cursors wird von der ODBC-Cursorbibliothek verwaltet, die ein Vorwärts- und Rückwärts-Scrollen ermöglicht.  
  
## <a name="rowset"></a>Rowset  
 In einem Cursor gespeicherte Datenblöcke, die Zeilen darstellen, die aus einer Datenquelle abgerufen wurden.
