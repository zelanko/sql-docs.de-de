---
title: Cursormodell (Visual FoxPro-ODBC-Treiber) unterstützt | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e623c0ce5135a4b2e558be9c405ec2757e605ceb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68080716"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Unterstütztes Cursormodell (Visual FoxPro-ODBC-Treiber)
Der Visual FoxPro-ODBC-Treiber unterstützt beide *Block* (*Rowset*) und *statische* Cursor. Statische Cursor werden für alle Treiber unterstützt, die ODBC-Ebene-1-Kompatibilität entspricht. Der Treiber unterstützt keine dynamischen, keysetgesteuerten oder gemischt (Keyset- und Dynamic) Cursor.  
  
 Ihre Anwendung aufrufen kann [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) mit einer Option SQL_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY (Blockcursor) oder SQL_CURSOR_STATIC (statische Cursor).  
  
> [!NOTE]  
>  Wenn Sie aufrufen **SQLSetStmtOption** mit einer als SQL_CURSOR_FORWARD_ONLY oder SQL_CURSOR_STATIC SQL_CURSOR_TYPE-Option, die Funktion gibt SQL_SUCCESS_WITH_INFO mit einem SQLSTATE 01 s 02 (der Optionswert wurde geändert). Der Treiber setzt alle nicht unterstützten Cursor-Modi zu SQL_CURSOR_STATIC.  
  
 Weitere Informationen zu Cursortypen und etwa **SQLSetStmtOption**, finden Sie unter den [ODBC Programmer's Reference](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>Blockcursor  
 Ein Bildlauf vorwärts, schreibgeschützt zurückgegebene Resultset an den Client, der zum Verwalten von Speicher für die Daten verantwortlich ist.  
  
## <a name="static-cursor"></a>Statischer Cursor  
 Eine Momentaufnahme eines Datasets, die von der Abfrage definiert. Statische Cursor spiegeln sich nicht auf Änderungen der zugrunde liegenden Daten von anderen Benutzern in Echtzeit aus. Speicherpuffer des Cursors wird von der ODBC-Cursorbibliothek beibehalten, wodurch Bildlauf vorwärts und rückwärts.  
  
## <a name="rowset"></a>Rowset  
 Blöcke von Daten in einem Cursor, die aus einer Datenquelle abgerufene Zeilen darstellt.
