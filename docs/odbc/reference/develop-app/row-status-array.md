---
title: Zeile Statusarray | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 1d2a04f5052a0b686d3669c976ec7c4bee09e52b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468627"
---
# <a name="row-status-array"></a>Zeilenstatusarray
Zusätzlich zu den Daten **SQLFetch** und **SQLFetchScroll** kann ein Array, das den Status der einzelnen Zeilen im Rowset kann zurückgeben. Dieses Array wird durch das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR angegeben. Dieses Array muss wird von der Anwendung zugeordnet und so viele Elemente, die von dem SQL_ATTR_ROW_ARRAY_SIZE-Attribut-Anweisung angegeben werden. Die Werte im Array werden durch festgelegt **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, und **SQLSetPos.** Die Werte werden den Status der Zeile und gibt an, ob diese Status geändert hat, seit dem letzten Abruf beschrieben.  
  
|Array-Statuswert Zeile|Description|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|Die Zeile wurde erfolgreich abgerufen und seit dem letzten Abruf nicht geändert werden.|  
|SQL_ROW_SUCCESS_WITH_INFO|Die Zeile wurde erfolgreich abgerufen und seit dem letzten Abruf nicht geändert werden. Allerdings wurde eine Warnung zur Zeile zurückgegeben.|  
|SQL_ROW_ERROR|Fehler beim Abrufen der Zeile.|  
|SQL_ROW_UPDATED|Die Zeile wurde erfolgreich abgerufen und wurde aktualisiert, seit sie zuletzt abgerufen wurde. Wenn die Zeile erneut abgerufen oder, indem aktualisiert **SQLSetPos**, seinen Status zu den neuen Status geändert wird.<br /><br /> Einige Treiber können keine Änderungen an Daten erkennen und aus diesem Grund können dieser Wert zurückgeben. Um zu bestimmen, ob ein Treiber, Updates von Zeilen erneut abgerufen erkennen kann, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_ROW_UPDATES.|  
|SQL_ROW_DELETED|Die Zeile wurde seit dem letzten Abruf wurde gelöscht.|  
|SQL_ROW_ADDED|Die Zeile eingefügt wurde, indem **SQLBulkOperations**. Wenn die Zeile erneut abgerufen oder, indem aktualisiert wird **SQLSetPos**, dessen Status ist SQL_ROW_SUCCESS.<br /><br /> Dieser Wert ist nicht festgelegt, indem **SQLFetch** oder **SQLFetchScroll**.|  
|SQL_ROW_NOROW|Das Rowset überlappende das Ende des Resultsets und keine Zeile zurückgegeben wurde, dass, die für dieses Element von der zeilenstatusarray entsprach.|
