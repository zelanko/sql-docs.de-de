---
title: 'Schritt 5: Commit der Transaktion | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e348ce697e512f30db46d14535cf19bd6d530f61
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283350"
---
# <a name="step-5-commit-the-transaction"></a>Schritt 5: Ausführen eines Commits für die Transaktion
Der nächste Schritt besteht darin, die Transaktion zu übertragen, wie in der folgenden Abbildung gezeigt.  
  
 ![Zeigt, wie ein Commit für eine Transaktion ausgeführt wird](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 Der fünfte Schritt besteht darin, **SQLEndTran** aufzurufen, um die Transaktion festzuschreiben oder zurückzusetzen. Die Anwendung führt diesen Schritt nur aus, wenn sie den Transaktionscommit-Modus auf manuellen Commit festgelegt hat. Wenn der Transaktionscommitmodus Auto-Commit ist, was der Standardwert ist, wird die Transaktion automatisch festgeschrieben, wenn die Anweisung ausgeführt wird. Weitere Informationen finden Sie unter [Transaktionen](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Um eine Anweisung in einer neuen Transaktion auszuführen, kehrt die Anwendung zu Schritt 3 zurück. Um die Verbindung zur Datenquelle zu trennen, fährt die Anwendung mit Schritt 6 fort.
