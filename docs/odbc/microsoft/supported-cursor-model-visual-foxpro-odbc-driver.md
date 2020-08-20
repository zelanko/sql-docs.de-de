---
description: Unterstütztes Cursormodell (Visual FoxPro-ODBC-Treiber)
title: Unterstütztes Cursor Modell (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
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
ms.openlocfilehash: 789d55a894e66c87fc5773856375757947835b35
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471532"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Unterstütztes Cursormodell (Visual FoxPro-ODBC-Treiber)
Der Visual FoxPro-ODBC-Treiber unterstützt sowohl *Block* (*Rowset*) als auch *statische* Cursor. Statische Cursor werden für jeden Treiber unterstützt, der der ODBC-Konformität der Ebene 1 entspricht. Der Treiber unterstützt keine dynamischen, keysetgesteuerten oder gemischten (Keyset-und Dynamic-Cursor).  
  
 Die Anwendung kann [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) mit einer SQL_CURSOR_TYPE Option SQL_CURSOR_FORWARD_ONLY (Block Cursor) oder SQL_CURSOR_STATIC (statischer Cursor) aufrufen.  
  
> [!NOTE]  
>  Wenn Sie **SQLSetStmtOption** mit einer anderen SQL_CURSOR_TYPE Option als SQL_CURSOR_FORWARD_ONLY oder SQL_CURSOR_STATIC aufrufen, gibt die Funktion SQL_SUCCESS_WITH_INFO mit dem SQLSTATE-Wert 01s02 (Optionswert geändert) zurück. Der Treiber legt alle nicht unterstützten Cursor Modi auf SQL_CURSOR_STATIC fest.  
  
 Weitere Informationen zu Cursor Typen und zu **SQLSetStmtOption**finden Sie in der [ODBC Programmer es Reference](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>Blockcursor  
 Ein Schreib geschütztes Resultset mit vorwärts scrollen, das an den Client zurückgegeben wird und für die Verwaltung des Speichers für die Daten verantwortlich ist.  
  
## <a name="static-cursor"></a>Statischer Cursor  
 Eine Momentaufnahme eines Datasets, das von der Abfrage definiert wird. Statische Cursor entsprechen nicht den Echt Zeit Änderungen der zugrunde liegenden Daten durch andere Benutzer. Der Arbeitsspeicher Puffer des Cursors wird von der ODBC-Cursor Bibliothek verwaltet, die vorwärts-und Rückwärtsscrollen ermöglicht.  
  
## <a name="rowset"></a>Rowset  
 Blöcke der in einem Cursor gespeicherten Daten, die aus einer Datenquelle abgerufene Zeilen darstellen.
