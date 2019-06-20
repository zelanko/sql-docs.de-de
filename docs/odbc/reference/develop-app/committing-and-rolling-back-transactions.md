---
title: Commit und Rollback für Transaktionen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 194a90482946814995ca1963f7c8fc4bce48d223
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63126363"
---
# <a name="committing-and-rolling-back-transactions"></a>Ausführen von Commits und Rollbacks von Transaktionen
Um einen commit oder Rollback für eine Transaktion aus, in den Manualcommit-Modus, eine Anwendung ruft **SQLEndTran**. Treiber für DBMS-Systeme, die Transaktionen, in der Regel unterstützen implementieren Sie diese Funktion durch Ausführen einer **COMMIT** oder **ROLLBACK** Anweisung. Der Treiber-Manager wird nicht aufgerufen. **SQLEndTran** Wenn die Verbindung im Autocommit-Modus ist es einfach gibt SQL_SUCCESS zurück, selbst wenn die Anwendung versucht, ein Rollback der Transaktion auszuführen. Da der Treiber für DBMS-Systeme, die keine Transaktionen unterstützen, immer im Autocommit Modus sind, können sie entweder zuerst **SQLEndTran** SQL_SUCCESS zurück, ohne eine Aktion auszuführen oder gar nicht implementiert.  
  
> [!NOTE]  
>  Anwendungen sollten nicht commit oder Rollback für Transaktionen aus, indem Sie Ausführung **COMMIT** oder **ROLLBACK** -Anweisungen mit **SQLExecute** oder **SQLExecDirect**. Die Auswirkungen auf diese Weise sind nicht definiert. Mögliche Probleme enthalten, der Treiber, die nicht mehr wissen, wenn eine Transaktion aktiv ist und diese Anweisungen, die Fehler für Datenquellen, die keine Transaktionen unterstützen. Diese Anwendungen sollten Aufrufen **SQLEndTran** stattdessen.  
  
 Wenn eine Anwendung das Umgebungshandle, übergibt **SQLEndTran** aber nicht übergeben eines Verbindungshandles, die der Treiber-Manager im Prinzip ruft **SQLEndTran** mit das Umgebungshandle für jeden Treiber, verfügt über eine oder mehrere Verbindungen in der Umgebung. Der Treiber führt dann einen Commit für die Transaktionen für jede Verbindung in der Umgebung. Allerdings ist es wichtig zu wissen, dass weder der Treiber als auch der Treiber-Manager auf den Verbindungen in der Umgebung einen Zweiphasen-Commit ausführt; Dies ist lediglich eine Vereinfachung der Programmierung gleichzeitig aufrufen **SQLEndTran** für alle Verbindungen in der Umgebung.  
  
 (Ein *Zweiphasen-Commit* wird in der Regel verwendet, um Transaktionen zu committen, das über mehrere Datenquellen hinweg verteilt sind. In der ersten Phase werden die Datenquellen abgerufen, gibt an, ob sie ihren Teil der Transaktion ausführen können. In der zweiten Phase wird die Transaktion tatsächlich bei all denjenigen Datenquellen ein Commit ausgeführt. Wenn alle Datenquellen in der ersten Phase zu antworten, dass sie die Transaktion keinen Commit durchführen können, erfolgt die zweite Phase nicht.)
