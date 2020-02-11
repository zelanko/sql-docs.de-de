---
title: Commit und Rollback von Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- transactions [ODBC], committing
ms.assetid: 800f2c1a-6f79-4ed1-830b-aa1a62ff5165
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c7c028ca7e89378e959b11f59cad4119cef5086a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083311"
---
# <a name="committing-and-rolling-back-transactions"></a>Ausführen von Commits und Rollbacks von Transaktionen
Um einen Commit oder Rollback einer Transaktion im manuellen Commitmodus auszuführen, ruft eine Anwendung **SQLEndTran**auf. Treiber für DBMSs, die Transaktionen unterstützen, implementieren diese Funktion in der Regel durch Ausführen einer **Commit** -oder **Rollback** -Anweisung. Der Treiber-Manager ruft **SQLEndTran** nicht auf, wenn sich die Verbindung im Autocommit-Modus befindet. Sie gibt einfach SQL_SUCCESS zurück, auch wenn die Anwendung versucht, ein Rollback für die Transaktion auszuführen. Da sich Treiber für DBMSs, die keine Transaktionen unterstützen, immer im Autocommit-Modus befinden, können Sie entweder **SQLEndTran** implementieren, um SQL_SUCCESS zurückzugeben, ohne dies zu tun oder überhaupt nicht zu implementieren.  
  
> [!NOTE]  
>  Anwendungen sollten keine Commit-oder Rollback-Transaktionen ausführen, indem Sie **Commit** -oder **Rollback** -Anweisungen mit **SQLExecute** oder **SQLExecDirect**ausführen. Die Auswirkungen auf diese Weise sind nicht definiert. Mögliche Probleme können darin liegen, dass der Treiber nicht mehr weiß, wann eine Transaktion aktiv ist, und dass diese Anweisungen für Datenquellen fehlschlagen, die keine Transaktionen unterstützen. Diese Anwendungen sollten stattdessen **SQLEndTran** aufruft.  
  
 Wenn eine Anwendung das Umgebungs Handle an **SQLEndTran** übergibt, aber kein Verbindungs Handle übergibt, ruft der Treiber-Manager konzeptionell **SQLEndTran** mit dem Umgebungs Handle für jeden Treiber auf, der über mindestens eine aktive Verbindung in der Umgebung verfügt. Der Treiber führt dann für jede Verbindung in der Umgebung einen Commit für die Transaktionen aus. Es ist jedoch wichtig zu wissen, dass weder der Treiber noch der Treiber-Manager einen Zweiphasencommit für die Verbindungen in der Umgebung ausführt. Dies ist lediglich eine Programmier praktische Möglichkeit, um **SQLEndTran** gleichzeitig für alle Verbindungen in der Umgebung aufzurufen.  
  
 (In der Regel wird ein *Zweiphasencommit* verwendet, um Transaktionen zu übertragen, die über mehrere Datenquellen verteilt sind. In der ersten Phase werden die Datenquellen abgerufen, unabhängig davon, ob Sie einen Commit für ihren Teil der Transaktion durchführen können. In der zweiten Phase wird für die Transaktion tatsächlich ein Commit für alle Datenquellen ausgeführt. Wenn eine Datenquelle in der ersten Phase antwortet, dass Sie keinen Commit für die Transaktion durchführen können, erfolgt die zweite Phase nicht.)
