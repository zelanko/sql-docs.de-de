---
title: Zeilen Status Array | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304291"
---
# <a name="row-status-array"></a>Zeilenstatusarray
Zusätzlich zu den Daten können **SQLFetch** und **SQLFetchScroll** ein Array zurückgeben, das den Status der einzelnen Zeilen im Rowset zurückgibt. Dieses Array wird über das SQL_ATTR_ROW_STATUS_PTR Statement-Attribut angegeben. Dieses Array wird von der Anwendung zugeordnet und muss über so viele Elemente verfügen, wie vom SQL_ATTR_ROW_ARRAY_SIZE Anweisungs Attribut angegeben werden. Die Werte im Array werden durch **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**und **SQLSetPos** festgelegt. Die Werte beschreiben den Status der Zeile und ob sich der Status seit dem letzten Abruf geändert hat.  
  
|Array Wert für Zeilen Status|BESCHREIBUNG|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|Die Zeile wurde erfolgreich abgerufen und seit der letzten Abruf Vorgang nicht geändert.|  
|SQL_ROW_SUCCESS_WITH_INFO|Die Zeile wurde erfolgreich abgerufen und seit der letzten Abruf Vorgang nicht geändert. Es wurde jedoch eine Warnung zur Zeile zurückgegeben.|  
|SQL_ROW_ERROR|Fehler beim Abrufen der Zeile.|  
|SQL_ROW_UPDATED|Die Zeile wurde erfolgreich abgerufen und wurde seit der letzten abgerufenen Aktualisierung aktualisiert. Wenn die Zeile erneut abgerufen oder von **SQLSetPos**aktualisiert wird, wird Ihr Status in den neuen Status geändert.<br /><br /> Einige Treiber können keine Änderungen an Daten erkennen und können daher diesen Wert nicht zurückgeben. Um zu ermitteln, ob ein Treiber Updates für erneut abgerufene Zeilen erkennen kann, ruft eine Anwendung **SQLGetInfo** mit der SQL_ROW_UPDATES-Option auf.|  
|SQL_ROW_DELETED|Die Zeile wurde gelöscht, seit Sie zuletzt abgerufen wurde.|  
|SQL_ROW_ADDED|Die Zeile wurde von **SQLBulkOperations**eingefügt. Wenn die Zeile erneut abgerufen oder von **SQLSetPos**aktualisiert wird, lautet der Status SQL_ROW_SUCCESS.<br /><br /> Dieser Wert wird nicht von **SQLFetch** oder **SQLFetchScroll**festgelegt.|  
|SQL_ROW_NOROW|Das Rowset hat das Ende des Resultsets überlappen, und es wurde keine Zeile zurückgegeben, die diesem Element des Zeilen Status Arrays entsprach.|
