---
description: SQLRowCount (Cursorbibliothek)
title: SQLRowCount (Cursor Bibliothek) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02c972d4847ef0736e6f9e9ac91f8f617e1d9df0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424877"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLRowCount** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLRowCount**finden Sie unter [SQLRowCount-Funktion](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Wenn eine Anwendung **SQLRowCount** mit der dem Cursor zugeordneten Anweisung aufruft, gibt die Cursor Bibliothek die Anzahl der Daten Zeilen zurück, die Sie vom Treiber abgerufen hat.  
  
 Wenn eine Anwendung **SQLRowCount** mit der-Anweisung aufruft, die einer positionierten Update-oder DELETE-Anweisung zugeordnet ist, gibt die Cursor Bibliothek die Anzahl der von der Anweisung betroffenen Zeilen zurück.  
  
 Wenn eine Anwendung **SQLRowCount** nach einer **Select** -Anweisung aufruft, gibt die Cursor Bibliothek-1 zurück.
