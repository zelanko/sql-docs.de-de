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
manager: craigg
ms.openlocfilehash: 3091d379bca6c061437e7767fdf6f99d69dc9861
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149151"
---
# <a name="step-4b-fetch-the-row-count"></a>Schritt 4b: Abrufen der Zeilenanzahl
Der nächste Schritt ist zum Abrufen der Zeilenanzahl liegt, wie in der folgenden Abbildung dargestellt.  
  
 ![Zeigt das Abrufen der Anzahl der Zeilen](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Wenn die Anweisung ausgeführt, die in Schritt 3 eine **UPDATE**, **löschen**, oder **einfügen** -Anweisung, die Anwendung ruft die Anzahl der betroffenen Zeilen mit  **SQLRowCount**. Weitere Informationen finden Sie unter [bestimmen die Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 Die Anwendung jetzt gibt Sie zurück zu Schritt 3, um eine weitere Anweisung in derselben Transaktion ausführen oder fährt Sie fort mit Schritt 5, um einen commit oder Rollback der Transaktions.
