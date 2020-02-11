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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 57b187bf4f14bd5c05f91a433fa331e954fa0fb9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020370"
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
