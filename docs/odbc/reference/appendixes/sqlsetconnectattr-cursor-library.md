---
description: SQLSetConnectAttr (Cursorbibliothek)
title: SQLSetConnectAttr (Cursor Bibliothek) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b809ad81e9edaca7fbe7d40952673a1698f113e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424892"
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLSetConnectAttr** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLSetConnectAttr**finden Sie unter [SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Eine Anwendung ruft **SQLSetConnectAttr** mit dem SQL_ATTR_ODBC_CURSORS-Attribut auf, um anzugeben, ob die Cursor Bibliothek immer verwendet wird. Sie wird verwendet, wenn der Treiber keine scrollbaren Cursor unterstützt oder nie verwendet wird. Die Cursor Bibliothek geht davon aus, dass ein Treiber scrollfähige Cursor unterstützt, wenn er SQL_CA1_RELATIVE für den SQL_STATIC_CURSOR_ATTRIBUTES1 Informationstyp in **SQLGetInfo**zurückgibt.  
  
 Die Anwendung muss **SQLSetConnectAttr** aufrufen, um die Verwendung der Cursor Bibliothek anzugeben, nachdem **SQLAllocHandle** mit dem Handlertyp SQL_HANDLE_DBC zum Zuordnen der Verbindung und vor dem Herstellen einer Verbindung mit der Datenquelle aufgerufen wurde. *HandleType* Wenn eine Anwendung **SQLSetConnectAttr** mit dem SQL_ATTR_ODBC_CURSORS-Attribut aufruft, während die Verbindung noch aktiv ist, gibt die Cursor Bibliothek einen Fehler zurück.  
  
 Um ein Anweisungs Attribut festzulegen, das von der Cursor Bibliothek für alle einer Verbindung zugeordneten Anweisungen unterstützt wird, muss eine Anwendung **SQLSetConnectAttr** für dieses Anweisungs Attribut aufrufen, nachdem Sie eine Verbindung mit der Datenquelle hergestellt hat und bevor der Cursor geöffnet wird. Wenn eine Anwendung **SQLSetConnectAttr** mit einem Anweisungs Attribut aufruft und ein Cursor in einer mit der Verbindung verknüpften Anweisung geöffnet ist, wird das Anweisungs Attribut erst dann auf diese Anweisung angewendet, wenn der Cursor geschlossen und erneut geöffnet wird.
