---
title: SQLGetData (Cursor Library) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Cursor Library
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1e3009b4e3bed6fc871ecfd1aab4e2af2f1f1c86
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853998"
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLGetData** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLGetData**, finden Sie unter [SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
 Die Cursorbibliothek implementiert **SQLGetData** indem zuerst ein **wählen** -Anweisung mit einer **, in denen** -Klausel, die in seinem Cache für jede Grenze gespeicherten Werte zählt die Spalte in der aktuellen Zeile. Dann wird die **wählen** Anweisung, um die Zeile und ruft erneut auswählen **SQLGetData** im Treiber zum Abrufen der Daten aus der Datenquelle (im Gegensatz zu den Cache).  
  
> [!CAUTION]  
>  Die **, in denen** Klausel erstellt, die von der Cursorbibliothek zum Identifizieren der aktuellen Zeile kann möglicherweise keine Zeilen zu identifizieren, identifizieren eine andere Zeile oder mehr als eine Zeile zu identifizieren. Weitere Informationen finden Sie unter [durchsucht-Anweisungen konstruieren](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Wenn das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE, festgelegt ist **SQLGetData** aufgerufen werden kann, auf die Spalte 0 Lesezeichen Daten zurückgeben.  
  
 Aufrufe von **SQLGetData** gelten die folgenden Einschränkungen:  
  
-   **SQLGetData** kann nicht für Vorwärtscursor aufgerufen werden.  
  
-   **SQLGetData** kann nur aufgerufen, wenn die folgenden Bedingungen erfüllt sind: eine **wählen** -Anweisung generiert das Resultset auf; die **wählen** Anweisung enthielt keine Verknüpfung eine  **UNION** -Klausel oder eine **GROUP BY** -Klausel; und alle Spalten, die einen Alias oder ein Ausdruck in der select-Liste verwendet wurden nicht mit gebunden **SQLBindCol**.  
  
-   Wenn der Treiber nur eine aktive Anweisung unterstützt, ruft die Cursorbibliothek den Rest des Resultsets vor dem Ausführen der **wählen** -Anweisung ab, und rufen **SQLGetData**.
