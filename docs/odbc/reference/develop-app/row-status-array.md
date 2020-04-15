---
title: Zeilenstatus-Array | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- row status array [ODBC]
- cursors [ODBC], block
- result sets [ODBC], row status array
- block cursors [ODBC]
- result sets [ODBC], block cursors
- rowset status [ODBC]
ms.assetid: 4b69f189-2722-4314-8a02-f4ffecd6dabd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 60dead23fe0051c05698e094f37ddad96b2b337d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304291"
---
# <a name="row-status-array"></a>Zeilenstatusarray
Zusätzlich zu den Daten können **SQLFetch** und **SQLFetchScroll** ein Array zurückgeben, das den Status jeder Zeile im Rowset angibt. Dieses Array wird über das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut angegeben. Dieses Array wird von der Anwendung zugewiesen und muss über so viele Elemente verfügen, wie durch das Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung angegeben werden. Die Werte im Array werden von **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**und **SQLSetPos festgelegt.** Die Werte beschreiben den Status der Zeile und ob sich dieser Status seit dem letzten Abruf geändert hat.  
  
|Zeilenstatus-Arraywert|Beschreibung|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|Die Zeile wurde erfolgreich abgerufen und hat sich seit dem letzten Abruf nicht geändert.|  
|SQL_ROW_SUCCESS_WITH_INFO|Die Zeile wurde erfolgreich abgerufen und hat sich seit dem letzten Abruf nicht geändert. Es wurde jedoch eine Warnung über die Zeile zurückgegeben.|  
|SQL_ROW_ERROR|Beim Abrufen der Zeile ist ein Fehler aufgetreten.|  
|SQL_ROW_UPDATED|Die Zeile wurde erfolgreich abgerufen und seit dem letzten Abruf aktualisiert. Wenn die Zeile erneut abgerufen oder von **SQLSetPos**aktualisiert wird, wird ihr Status in den neuen Status geändert.<br /><br /> Einige Treiber können keine Änderungen an Daten erkennen und daher diesen Wert nicht zurückgeben. Um zu bestimmen, ob ein Treiber Aktualisierungen für neu abgerufene Zeilen erkennen kann, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_ROW_UPDATES auf.|  
|SQL_ROW_DELETED|Die Zeile wurde gelöscht, seit sie zuletzt abgerufen wurde.|  
|SQL_ROW_ADDED|Die Zeile wurde von **SQLBulkOperations**eingefügt. Wenn die Zeile erneut abgerufen oder von **SQLSetPos**aktualisiert wird, lautet ihr Status SQL_ROW_SUCCESS.<br /><br /> Dieser Wert wird nicht von **SQLFetch** oder **SQLFetchScroll**festgelegt.|  
|SQL_ROW_NOROW|Das Rowset überlappte das Ende des Resultsets, und es wurde keine Zeile zurückgegeben, die diesem Element des Zeilenstatusarrays entsprach.|
