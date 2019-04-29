---
title: 'Schritt 5: Commit für die Transaktion | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], committing transactions
- committing transactions [ODBC]
- transaction commit [ODBC]
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 341f34afa1dbe65f4b83a46f461bb93f4fb4f4c8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63148941"
---
# <a name="step-5-commit-the-transaction"></a>Schritt 5: Committen der Transaktion
Der nächste Schritt ist die Transaktion, wie in der folgenden Abbildung dargestellt.  
  
 ![Zeigt, wie Commit eine Transaktion](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 Der fünfte Schritt besteht darin Aufrufen **SQLEndTran** , einen commit oder Rollback der Transaktion. Die Anwendung führt diesen Schritt nur, wenn der Commit-Transaktionsmodus Manualcommit-festlegen; der Transaktions-Commit-Modus ist automatischer Commit, der die Standardeinstellung ist, der Transaktions automatisch ein Commit ausgeführt, wenn die Anweisung ausgeführt wird. Weitere Informationen finden Sie unter [Transaktionen](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Zum Ausführen einer Anweisung in eine neue Transaktion, gibt die Anwendung mit Schritt 3 zurück. Um Daten aus der Datenquelle zu trennen, wird die Anwendung Schritt 6.
