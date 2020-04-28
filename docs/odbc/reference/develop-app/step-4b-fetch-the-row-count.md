---
title: 'Schritt 4B: Abrufen der Zeilen Anzahl | Microsoft-Dokumentation'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31ccbd15ae435165ea007fa9f3c0505c1dcc5aa0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302961"
---
# <a name="step-4b-fetch-the-row-count"></a>Schritt 4b: Abrufen der Zeilenanzahl
Der nächste Schritt ist das Abrufen der Zeilen Anzahl, wie in der folgenden Abbildung dargestellt.  
  
 ![Zeigt das Abrufen der Zeilenanzahl](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Wenn die in Schritt 3 ausgeführte Anweisung eine **Update**-, **Delete**-oder **Insert** -Anweisung ist, ruft die Anwendung die Anzahl der betroffenen Zeilen mit **SQLRowCount**ab. Weitere Informationen finden Sie unter [bestimmen der Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 Die Anwendung kehrt nun zu Schritt 3 zurück, um eine weitere Anweisung in derselben Transaktion auszuführen, oder fährt mit Schritt 5 fort, um einen Commit oder Rollback für die Transaktion auszuführen.
