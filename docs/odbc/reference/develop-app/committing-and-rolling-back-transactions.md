---
title: Commiting und RollBack von Transaktionen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c272d60242d31622452c4dcb0f6a16c4838768f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299110"
---
# <a name="committing-and-rolling-back-transactions"></a>Ausführen von Commits und Rollbacks von Transaktionen
Um eine Transaktion im manuellen Commit-Modus festzuschreiben oder zurückzusetzen, ruft eine Anwendung **SQLEndTran**auf. Treiber für DBMS, die Transaktionen unterstützen, implementieren diese Funktion in der Regel durch Ausführen einer **COMMIT-** oder **ROLLBACK-Anweisung.** Der Treiber-Manager ruft **SQLEndTran** nicht auf, wenn sich die Verbindung im Autocommit-Modus befindet. Es wird einfach SQL_SUCCESS zurückgegeben, auch wenn die Anwendung versucht, einen Rollback für die Transaktion zu erzielen. Da sich Treiber für DBMS, die Keine Transaktionen unterstützen, immer im Autocommit-Modus befinden, können sie **ENTWEDER SQLEndTran** implementieren, um SQL_SUCCESS zurückzugeben, ohne etwas zu tun, oder sie überhaupt nicht implementieren.  
  
> [!NOTE]  
>  Anwendungen sollten keine Commit- oder Rollbacktransaktionen ausführen, indem **sie COMMIT-** oder **ROLLBACK-Anweisungen** mit **SQLExecute** oder **SQLExecDirect**ausführen. Die Auswirkungen dieser Vorgehensweise sind nicht definiert. Mögliche Probleme sind der Treiber, der nicht mehr weiß, wann eine Transaktion aktiv ist, und diese Anweisungen schlagen für Datenquellen fehl, die Keine Transaktionen unterstützen. Diese Anwendungen sollten stattdessen **SQLEndTran** aufrufen.  
  
 Wenn eine Anwendung das Umgebungshandle an **SQLEndTran** übergibt, aber kein Verbindungshandle übergibt, ruft der Treiber-Manager **SQLEndTran** konzeptionell mit dem Umgebungshandle für jeden Treiber auf, der über eine oder mehrere aktive Verbindungen in der Umgebung verfügt. Der Treiber überträgt dann die Transaktionen für jede Verbindung in der Umgebung. Es ist jedoch wichtig zu erkennen, dass weder der Treiber noch der Treiber-Manager einen zweiphasigen Commit für die Verbindungen in der Umgebung durchführt. Dies ist lediglich ein Programmierkomfort, um gleichzeitig **SQLEndTran** für alle Verbindungen in der Umgebung aufzurufen.  
  
 (Ein *zweiphasiges Commit* wird im Allgemeinen verwendet, um Transaktionen zu übertragen, die über mehrere Datenquellen verteilt sind. In der ersten Phase werden die Datenquellen danach befragt, ob sie ihren Teil der Transaktion festigen können. In der zweiten Phase wird die Transaktion tatsächlich für alle Datenquellen festgeschrieben. Wenn Datenquellen in der ersten Phase antworten, dass sie die Transaktion nicht übertragen können, tritt die zweite Phase nicht auf.)
