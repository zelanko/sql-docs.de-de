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
ms.openlocfilehash: 5877a6cb7a99803f854338321e333c87037c2e90
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67913585"
---
# <a name="fixed-length-bookmarks"></a>Textmarke mit fester Länge
Wenn eine ODBC *3.x* Treiber sollte funktionieren mit einer ODBC- *2.x* Anwendung, dass verwendet Lesezeichen mit fester Länge, der Treiber die folgenden unterstützen müssen:  
  
-   SQL_UB_ON als Wert für die SQL_USE_BOOKMARKS-Option-Anweisung. (SQL_UB_ON veraltetes Feature in ODBC *3.x*.)  
  
-   Die Option für den SQL_GET_BOOKMARK-Anweisung.
