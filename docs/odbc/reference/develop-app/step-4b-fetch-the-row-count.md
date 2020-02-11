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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9455c6589ed93a51e404f3e50d1cb86a0c0c8476
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114161"
---
# <a name="step-4b-fetch-the-row-count"></a>Schritt 4b: Abrufen der Zeilenanzahl
Der nächste Schritt ist das Abrufen der Zeilen Anzahl, wie in der folgenden Abbildung dargestellt.  
  
 ![Zeigt das Abrufen der Zeilenanzahl](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Wenn die in Schritt 3 ausgeführte Anweisung eine **Update**-, **Delete**-oder **Insert** -Anweisung ist, ruft die Anwendung die Anzahl der betroffenen Zeilen mit **SQLRowCount**ab. Weitere Informationen finden Sie unter [bestimmen der Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 Die Anwendung kehrt nun zu Schritt 3 zurück, um eine weitere Anweisung in derselben Transaktion auszuführen, oder fährt mit Schritt 5 fort, um einen Commit oder Rollback für die Transaktion auszuführen.
