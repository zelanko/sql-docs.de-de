---
title: 'Schritt 4b: Abrufen der Zeilenanzahl | Microsoft Docs'
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302961"
---
# <a name="step-4b-fetch-the-row-count"></a>Schritt 4b: Abrufen der Zeilenanzahl
Der nächste Schritt besteht darin, die Zeilenanzahl abzurufen, wie in der folgenden Abbildung gezeigt.  
  
 ![Zeigt das Abrufen der Zeilenanzahl](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Wenn es sich bei der in Schritt 3 ausgeführten Anweisung um eine **UPDATE-,** **DELETE-** oder **INSERT-Anweisung** handelte, ruft die Anwendung die Anzahl der betroffenen Zeilen mit **SQLRowCount**ab. Weitere Informationen finden Sie unter [Ermitteln der Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 Die Anwendung kehrt nun zu Schritt 3 zurück, um eine andere Anweisung in derselben Transaktion auszuführen, oder fährt mit Schritt 5 fort, um die Transaktion zu übertragen oder zurückzusetzen.
