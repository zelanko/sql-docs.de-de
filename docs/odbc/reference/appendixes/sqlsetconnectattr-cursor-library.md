---
title: SQLSetConnectAttr (Cursor Library) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC], Cursor Library
ms.assetid: 6f70bbd0-a057-49ef-8b05-4c80b58fc6e6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d4023c513ffda04a3cf499110185d3746ca40d9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63299188"
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLSetConnectAttr** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLSetConnectAttr**, finden Sie unter [SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Ruft die Anwendung **SQLSetConnectAttr** mit des Attributs SQL_ATTR_ODBC_CURSORS, um anzugeben, ob die Cursorbibliothek ist immer verwendet, verwendet, wenn der Treiber scrollfähige Cursor nicht unterstützt oder noch nie verwendet. Die Cursorbibliothek wird davon ausgegangen, dass ein Treiber scrollfähige Cursor unterstützt, für den Typ des SQL_STATIC_CURSOR_ATTRIBUTES1-Informationen im SQL_CA1_RELATIVE zurückgegeben **SQLGetInfo**.  
  
 Muss die Anwendung aufrufen **SQLSetConnectAttr** die Cursorverwendung Bibliothek an, nach dem Aufruf **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_DBC auf, um zuordnen die Verbindung und bevor die Verbindung mit der Datenquelle. Wenn eine Anwendung ruft **SQLSetConnectAttr** mit des Attributs SQL_ATTR_ODBC_CURSORS während die Verbindung weiterhin aktiv ist, ist die Cursorbibliothek gibt einen Fehler zurück.  
  
 Um ein Anweisungsattribut unterstützt, die von der Cursorbibliothek für alle Anweisungen im Zusammenhang mit einer Verbindung festzulegen, muss eine Anwendung aufrufen **SQLSetConnectAttr** für dieses Anweisungsattribut, nachdem sie mit der Datenquelle und bevor sie eine Verbindung hergestellt Öffnet den Cursor. Wenn eine Anwendung ruft **SQLSetConnectAttr** mit einer Anweisung-Attribut und einen Cursor geöffnet, in einer Anweisung, die der Verbindung zugeordnet ist, das Anweisungsattribut wird nicht auf die Anweisung angewendet werden, bis der Cursor geschlossen wird und erneut geöffnet.
