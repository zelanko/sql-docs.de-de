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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67913585"
---
# <a name="fixed-length-bookmarks"></a>Textmarke mit fester Länge
Wenn ein ODBC *3. x* -Treiber mit einer ODBC *2. x* -Anwendung verwendet werden soll, die Lesezeichen mit fester Länge verwendet, muss der Treiber Folgendes unterstützen:  
  
-   SQL_UB_ON als Wert für die Option SQL_USE_BOOKMARKS Anweisung aus. (SQL_UB_ON in ODBC *3. x*als veraltet markiert.)  
  
-   Die SQL_GET_BOOKMARK Anweisungs Option.
