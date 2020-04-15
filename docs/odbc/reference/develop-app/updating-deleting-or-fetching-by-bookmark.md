---
title: Aktualisieren, Löschen oder Abrufen nach Lesezeichen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e94a98bb577ef906afbb04539761fd07d15f772
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286150"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Aktualisieren, Löschen oder Abrufen durch Textmarke
Lesezeichen können verwendet werden, um Daten zu identifizieren, die im Resultset aktualisiert, aus dem Resultset gelöscht oder aus dem Resultset in die Rowsetpuffer abgerufen werden sollen. Diese Vorgänge werden durch einen Aufruf von **SQLBulkOperations** mit dem *Optionsargument* SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK oder SQL_FETCH_BY_BOOKMARK ausgeführt. Die in diesen Vorgängen verwendeten Lesezeichen werden in Spalte 0 der Rowsetpuffer gespeichert. Beim Aktualisieren nach Lesezeichen werden die Daten, auf die Ergebnissatzspalten aktualisiert werden, aus den Rowsetpuffern abgerufen. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
