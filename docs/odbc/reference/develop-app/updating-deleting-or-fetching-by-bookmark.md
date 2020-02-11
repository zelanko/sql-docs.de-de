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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce43cb1d5563128e840aa3c0df26190524774a38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091636"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Aktualisieren, Löschen oder Abrufen durch Textmarke
Lesezeichen können verwendet werden, um die im Resultset zu aktualisierenden Daten zu identifizieren, aus dem Resultset gelöscht oder aus dem Resultset in die rowsetpuffer abgerufen zu werden. Diese Vorgänge werden durch einen **SQLBulkOperations** -Befehl mit einem *options* Argument von SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK oder SQL_FETCH_BY_BOOKMARK ausgeführt. Die in diesen Vorgängen verwendeten Lesezeichen werden in der Spalte 0 der rowsetpuffer gespeichert. Beim Aktualisieren durch Lesezeichen werden die Daten, auf die Resultset-Spalten aktualisiert werden, aus den rowsetpuffern abgerufen. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
