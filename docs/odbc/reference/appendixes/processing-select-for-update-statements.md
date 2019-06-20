---
title: Wählen Sie für UPDATE-Anweisungen verarbeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], select for update statements
- select for update [ODBC]
- SQL statements [ODBC], cursor library
- cursor library [ODBC], select for update statements
- ODBC cursor library [ODBC], select for update statements
- cursor library [ODBC], statement processing
ms.assetid: 8d2e79a4-5daf-458e-a536-d8b6e588753e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f54d31426773f294a4a23f059c9f906d430056f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63057021"
---
# <a name="processing-select-for-update-statements"></a>Verarbeiten von SELECT FOR UPDATE-Anweisungen
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Für eine optimale Interoperabilität sollten Anwendungen generieren Resultsets, die durch Ausführen von mit einer positioniertes Update-Anweisung aktualisiert werden eine **wählen Sie für UPDATE** Anweisung. Obwohl die Cursorbibliothek dies nicht erforderlich ist, ist es von den meisten Datenquellen erforderlich, die positionierte Update-Anweisungen unterstützen.  
  
 Die Cursorbibliothek ignoriert die Spalten in der **FOR UPDATE** -Klausel einer **SELECT FOR UPDATE** -Anweisung vor der Übergabe der Anweisung an den Treiber wird diese Klausel wird entfernt. In der Cursorbibliothek das SQL_ATTR_CONCURRENCY-Anweisungsattribut, zusammen mit den Einschränkungen, die im vorherigen Abschnitt erwähnten können Steuerelemente, ob die Spalten in einem Resultset aktualisiert werden.
