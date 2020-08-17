---
description: 'Schritt 5: Ausführen eines Commits für die Transaktion'
title: 'Schritt 5: Commit für die Transaktion ausführen | Microsoft-Dokumentation'
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
ms.openlocfilehash: b4cc3a73e5cfc564992795ab6b18759b1066288c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88385896"
---
# <a name="step-5-commit-the-transaction"></a>Schritt 5: Ausführen eines Commits für die Transaktion
Der nächste Schritt besteht darin, ein Commit für die Transaktion durchzusetzen, wie in der folgenden Abbildung dargestellt.  
  
 ![Zeigt, wie ein Commit für eine Transaktion ausgeführt wird](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 Der fünfte Schritt besteht darin, **SQLEndTran** aufzurufen, um einen Commit oder Rollback für die Transaktion auszuführen. Die Anwendung führt diesen Schritt nur aus, wenn der transaktionscommitmodus auf manuelles Commit festgelegt wird. Wenn der transaktionscommitmodus ein automatischer Commit ist (der Standardwert), wird für die Transaktion automatisch ein Commit ausgeführt, wenn die Anweisung ausgeführt wird. Weitere Informationen finden Sie unter [Transaktionen](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Wenn Sie eine-Anweisung in einer neuen Transaktion ausführen möchten, wird die Anwendung in Schritt 3 zurückgegeben. Um die Verbindung mit der Datenquelle zu trennen, fährt die Anwendung mit Schritt 6 fort.
