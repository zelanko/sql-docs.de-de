---
title: Zeile Status | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ce45314cef92404fe14a43e033c14d6a272e1bf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765788"
---
# <a name="row-status"></a>Zeilenstatus
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Die Cursorbibliothek erstellt einen Puffer in den Cache für den Zeilenstatus. Die Cursorbibliothek Ruft Werte für die zeilenstatusarray (angegeben mit der SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut) aus diesen Puffer ab. Für jede Zeile wird die Cursorbibliothek auf diesen Puffer festgelegt:  
  
-   SQL_ROW_DELETED, die beim Ausführen einer positionierte delete-Anweisung in der Zeile.  
  
-   SQL_ROW_ERROR beim Auftreten eines Fehlers beim Abrufen der zeilenupdates aus der Datenquelle mit **SQLFetch**.  
  
-   SQL_ROW_SUCCESS, wenn sie die Zeile wurde erfolgreich aus der Datenquelle mit abruft **SQLFetch**.  
  
-   SQL_ROW_UPDATED, wenn es eine positioniertes Update-Anweisung, in der Zeile ausführt.
