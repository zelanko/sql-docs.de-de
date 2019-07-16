---
title: 'Schritt 4b: Die Anzahl der Zeilen abrufen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- fetches [ODBC], fetching row count
- row count [ODBC]
- application process [ODBC], fetching row count
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9455c6589ed93a51e404f3e50d1cb86a0c0c8476
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114161"
---
# <a name="step-4b-fetch-the-row-count"></a>Schritt 4b: Abrufen der Zeilenanzahl
Der nächste Schritt ist zum Abrufen der Zeilenanzahl liegt, wie in der folgenden Abbildung dargestellt.  
  
 ![Zeigt das Abrufen der Anzahl der Zeilen](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Wenn die Anweisung ausgeführt, die in Schritt 3 eine **UPDATE**, **löschen**, oder **einfügen** -Anweisung, die Anwendung ruft die Anzahl der betroffenen Zeilen mit  **SQLRowCount**. Weitere Informationen finden Sie unter [bestimmen die Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 Die Anwendung jetzt gibt Sie zurück zu Schritt 3, um eine weitere Anweisung in derselben Transaktion ausführen oder fährt Sie fort mit Schritt 5, um einen commit oder Rollback der Transaktions.
