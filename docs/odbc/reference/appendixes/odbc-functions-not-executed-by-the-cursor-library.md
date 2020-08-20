---
description: ODBC-Funktionen, die nicht von der Cursorbibliothek ausgeführt werden
title: ODBC-Funktionen, die von der Cursor Bibliothek nicht ausgeführt werden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], functions
- functions [ODBC], cursor library
- ODBC functions [ODBC], cursor library
- ODBC cursor library [ODBC], functions
ms.assetid: f2941522-75eb-4db9-9468-4800b884dac2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e9855bcf92373af085ac7ba8eb10f63afef6c5c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466102"
---
# <a name="odbc-functions-not-executed-by-the-cursor-library"></a>ODBC-Funktionen, die nicht von der Cursorbibliothek ausgeführt werden
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Die Cursor Bibliothek führt die folgenden Funktionen nicht aus. Wenn eine Anwendung eine dieser Funktionen aufruft, ruft der Treiber-Manager den Treiber auf, nicht die Cursor Bibliothek.  
  
|||  
|-|-|  
|**SQLFetch**|**SQLGetEnvAttr**|  
|**SQLGetConnectAttr**|**SQLSetDescRec**|  
|**SQLGetDiagField**|**SQLSetEnvAttr**|  
|**SQLGetDiagRec**||
