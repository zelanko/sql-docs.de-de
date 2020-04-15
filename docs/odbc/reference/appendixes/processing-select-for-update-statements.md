---
title: Verarbeiten von SELECT FOR UPDATE-Anweisungen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 904028cd7b3798fcac8f9e5afa6186fae3e9fa29
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81308011"
---
# <a name="processing-select-for-update-statements"></a>Verarbeiten von SELECT FOR UPDATE-Anweisungen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Für maximale Interoperabilität sollten Anwendungen Resultsets generieren, die mit einer positionierten Updateanweisung aktualisiert werden, indem eine **SELECT FOR UPDATE-Anweisung** ausgeführt wird. Obwohl die Cursorbibliothek dies nicht erfordert, wird sie von den meisten Datenquellen benötigt, die positionierte Aktualisierungsanweisungen unterstützen.  
  
 Die Cursorbibliothek ignoriert die Spalten in der **FOR UPDATE-Klausel** einer **SELECT FOR UPDATE-Anweisung;** Diese Klausel wird entfernt, bevor die Anweisung an den Treiber übergeben wird. In der Cursorbibliothek steuert das Attribut SQL_ATTR_CONCURRENCY-Anweisung zusammen mit den im vorherigen Abschnitt erwähnten Einschränkungen, ob die Spalten in einer Ergebnismenge aktualisiert werden können.
