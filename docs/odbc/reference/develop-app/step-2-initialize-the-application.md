---
title: 'Schritt 2: Initialisieren der Anwendung | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 843155ba6b641ea26717e63af55c8774f963a800
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288266"
---
# <a name="step-2-initialize-the-application"></a>Schritt 2: Initialisieren der Anwendung
Der zweite Schritt besteht darin, die Anwendung zu initialisieren, wie in der folgenden Abbildung gezeigt. Genau das, was hier getan wird, variiert mit der Anwendung.  
  
 ![Zeigt das Initialisieren einer ODBC-Anwendung](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 An diesem Punkt ist es üblich, **SQLGetInfo** zu verwenden, um die Funktionen des Treibers zu ermitteln. Weitere Informationen finden Sie unter Berücksichtigen von [Datenbankfeatures zur Verwendung](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Alle Anwendungen müssen ein Anweisungshandle mit **SQLAllocHandle**zuweisen, und viele Anwendungen legen Anweisungsattribute fest, z. B. den Cursortyp, mit **SQLSetStmtAttr**. Weitere Informationen finden Sie unter [Zuweisen eines Anweisungshandles](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) und [von Anweisungsattributen](../../../odbc/reference/develop-app/statement-attributes.md).
