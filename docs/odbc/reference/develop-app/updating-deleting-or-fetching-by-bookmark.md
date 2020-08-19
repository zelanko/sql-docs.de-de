---
description: Aktualisieren, Löschen oder Abrufen durch Textmarke
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
ms.openlocfilehash: 2202e3483e13848ccac7f7e6f21145ba9704a8b7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448947"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Aktualisieren, Löschen oder Abrufen durch Textmarke
Lesezeichen können verwendet werden, um die im Resultset zu aktualisierenden Daten zu identifizieren, aus dem Resultset gelöscht oder aus dem Resultset in die rowsetpuffer abgerufen zu werden. Diese Vorgänge werden durch einen **SQLBulkOperations** -Befehl mit einem *options* Argument von SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK oder SQL_FETCH_BY_BOOKMARK ausgeführt. Die in diesen Vorgängen verwendeten Lesezeichen werden in der Spalte 0 der rowsetpuffer gespeichert. Beim Aktualisieren durch Lesezeichen werden die Daten, auf die Resultset-Spalten aktualisiert werden, aus den rowsetpuffern abgerufen. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
