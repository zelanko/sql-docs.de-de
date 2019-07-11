---
title: Lesezeichen mit fester Länge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21af6ef1be21e000d25582151650f274fe3561a4
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793373"
---
# <a name="fixed-length-bookmarks"></a>Textmarke mit fester Länge
Wenn eine ODBC *3.x* Treiber sollte funktionieren mit einer ODBC- *2.x* Anwendung, dass verwendet Lesezeichen mit fester Länge, der Treiber die folgenden unterstützen müssen:  
  
-   SQL_UB_ON als Wert für die SQL_USE_BOOKMARKS-Option-Anweisung. (SQL_UB_ON veraltetes Feature in ODBC *3.x*.)  
  
-   Die Option für den SQL_GET_BOOKMARK-Anweisung.
