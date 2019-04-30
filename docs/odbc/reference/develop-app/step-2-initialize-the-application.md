---
title: 'Schritt 2: Initialisieren Sie die Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0d25173dc8dc14aa1ed41a4a88496ef654e2ff0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149189"
---
# <a name="step-2-initialize-the-application"></a>Schritt 2: Initialisieren der Anwendung
Der zweite Schritt ist zum Initialisieren der Anwendung, wie in der folgenden Abbildung dargestellt. Genau wie hier erfolgt variiert je nach der Anwendung.  
  
 ![Zeigt das Initialisieren einer ODBC-Anwendung](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 An diesem Punkt ist es üblich, verwenden Sie **SQLGetInfo** ermitteln Sie die Funktionen des Treibers. Weitere Informationen finden Sie unter [zu verwendenden Datenbankfunktionen in Betracht ziehen](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Alle Anwendungen müssen ein Anweisungshandle mit zuzuweisen **SQLAllocHandle**, und legen Sie viele Anwendungen Anweisungsattribute, z. B. der Cursortyp mit **SQLSetStmtAttr**. Weitere Informationen finden Sie unter [Zuordnen einer Anweisungshandle](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) und [Anweisungsattribute](../../../odbc/reference/develop-app/statement-attributes.md).
