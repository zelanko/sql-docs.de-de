---
description: 'Schritt 2: Initialisieren der Anwendung'
title: 'Schritt 2: Initialisieren der Anwendung | Microsoft-Dokumentation'
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
ms.openlocfilehash: 26d20a5b10ee7b414b9285a388359b3a93029f16
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482883"
---
# <a name="step-2-initialize-the-application"></a>Schritt 2: Initialisieren der Anwendung
Der zweite Schritt besteht darin, die Anwendung zu initialisieren, wie in der folgenden Abbildung dargestellt. Genau was ist hier zu tun, hängt von der Anwendung ab.  
  
 ![Zeigt das Initialisieren einer ODBC-Anwendung](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 An diesem Punkt wird häufig **SQLGetInfo** verwendet, um die Funktionen des Treibers zu ermitteln. Weitere Informationen finden Sie unter [Überprüfen der zu verwendenden Datenbankfunktionen](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Alle Anwendungen müssen ein Anweisungs Handle mit **SQLAllocHandle**zuordnen, und viele Anwendungen legen Anweisungs Attribute, z. b. den Cursortyp, mit **SQLSetStmtAttr**fest. Weitere Informationen finden Sie unter [Zuordnen eines Anweisungs Handles](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) und [Anweisungs Attributen](../../../odbc/reference/develop-app/statement-attributes.md).
