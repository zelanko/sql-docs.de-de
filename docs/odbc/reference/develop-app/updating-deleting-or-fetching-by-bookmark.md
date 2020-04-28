---
title: Aktualisieren, löschen oder Abrufen von Lesezeichen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286150"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Aktualisieren, Löschen oder Abrufen durch Textmarke
Lesezeichen können verwendet werden, um die im Resultset zu aktualisierenden Daten zu identifizieren, aus dem Resultset gelöscht oder aus dem Resultset in die rowsetpuffer abgerufen zu werden. Diese Vorgänge werden durch einen **SQLBulkOperations** -Befehl mit einem *options* Argument von SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK oder SQL_FETCH_BY_BOOKMARK ausgeführt. Die in diesen Vorgängen verwendeten Lesezeichen werden in der Spalte 0 der rowsetpuffer gespeichert. Beim Aktualisieren durch Lesezeichen werden die Daten, auf die Resultset-Spalten aktualisiert werden, aus den rowsetpuffern abgerufen. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
