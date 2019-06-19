---
title: Aktualisieren, löschen oder Abrufen nach Lesezeichen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: c5af3cad39739c3b85a0c6298d682d8e75a5918d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63151222"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Aktualisieren, Löschen oder Abrufen durch Textmarke
Lesezeichen können verwendet werden, zum Identifizieren von Daten im Resultset, aus dem Ergebnis festgelegt oder abgerufen, die aus dem Resultset in der Rowset-Puffer gelöscht, aktualisiert werden. Diese Vorgänge werden durch einen Aufruf von **SQLBulkOperations** mit einer *Option* Argument SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK oder SQL_FETCH_BY_BOOKMARK. Lesezeichen verwendet diese Vorgänge werden in Spalte 0, der die Rowset-Puffer gespeichert. Bei der Aktualisierung durch Lesezeichen werden die Daten, die Spalten zu aktualisiert, wird von den Puffern Rowset abgerufen. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
