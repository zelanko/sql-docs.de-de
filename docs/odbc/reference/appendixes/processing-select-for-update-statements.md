---
title: Verarbeiten von Select for Update-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], select for update statements
- select for update [ODBC]
- SQL statements [ODBC], cursor library
- cursor library [ODBC], select for update statements
- ODBC cursor library [ODBC], select for update statements
- cursor library [ODBC], statement processing
ms.assetid: 8d2e79a4-5daf-458e-a536-d8b6e588753e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8ad9a20ab8abd40123ec4e4d7369373e68699205
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028365"
---
# <a name="processing-select-for-update-statements"></a>Verarbeiten von SELECT FOR UPDATE-Anweisungen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Zur maximalen Interoperabilität sollten Anwendungen Resultsets generieren, die mit einer positionierten Update-Anweisung aktualisiert werden, indem **Sie eine SELECT for Update** -Anweisung ausführen. Die Cursor Bibliothek erfordert dies nicht, aber Sie ist für die meisten Datenquellen erforderlich, die positionierte UPDATE-Anweisungen unterstützen.  
  
 Die Cursor Bibliothek ignoriert die Spalten in der **for Update** -Klausel einer **Select for Update** -Anweisung. Diese Klausel wird entfernt, bevor die-Anweisung an den Treiber übergeben wird. In der Cursor Bibliothek steuert das SQL_ATTR_CONCURRENCY Statement-Attribut zusammen mit den im vorherigen Abschnitt erwähnten Einschränkungen, ob die Spalten in einem Resultset aktualisiert werden können.
