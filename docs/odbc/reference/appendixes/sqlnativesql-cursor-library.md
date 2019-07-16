---
title: SQLNativeSql (Cursor Library) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0a8c42efbd87296cf7157d75d1848e4655247818
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125711"
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLNativeSql** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLNativeSql**, finden Sie unter [SQLNativeSql-Funktion](../../../odbc/reference/syntax/sqlnativesql-function.md).  
  
 Wenn der Treiber diese Funktion unterstützt wird, ruft die Cursorbibliothek **SQLNativeSql** im Treiber und übergibt sie die SQL-Anweisung. Für positionierte Update positioniert löschen und **wählen Sie für UPDATE** -Anweisungen, die Cursorbibliothek ändert die Anweisung vor der Übergabe an den Treiber.  
  
> [!NOTE]  
>  Die Cursorbibliothek SQLSTATE 34000 (Ungültiger Cursorname) falsch gibt zurück, wenn der Name des Cursors ist ungültig in ein positioniertes Update oder Delete-Anweisung, die übergeben werden die *InStatementText* Argument **SQLNativeSql** . **SQLNativeSql** keine Syntaxfehler, zurückgeben, die nur bei der Vorbereitung der Anweisung oder der Ausführung zurückgegeben werden soll.
