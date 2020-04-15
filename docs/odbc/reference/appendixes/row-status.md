---
title: Zeilenstatus | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4ae4169dc3f2a491663f4a86c564cfee5c2f4d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305099"
---
# <a name="row-status"></a>Zeilenstatus
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Die Cursorbibliothek erstellt einen Puffer im Cache für den Zeilenstatus. Die Cursorbibliothek ruft Werte für das Zeilenstatusarray (mit dem Attribut SQL_ATTR_ROW_STATUS_PTR Anweisung angegeben) aus diesem Puffer ab. Für jede Zeile legt die Cursorbibliothek diesen Puffer auf:  
  
-   SQL_ROW_DELETED, wenn eine positionierte löschanweisung in der Zeile ausgeführt wird.  
  
-   SQL_ROW_ERROR, wenn ein Fehler beim Abrufen der Zeile aus der Datenquelle mit **SQLFetch**auftritt.  
  
-   SQL_ROW_SUCCESS, wenn die Zeile mit **SQLFetch**erfolgreich aus der Datenquelle abgerufen wird.  
  
-   SQL_ROW_UPDATED, wenn eine positionierte Aktualisierungsanweisung in der Zeile ausgeführt wird.
