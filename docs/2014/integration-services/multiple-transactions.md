---
title: Mehrere Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], multiple
- multiple transactions
ms.assetid: c3664a94-be89-40c0-a3a0-84b74a7fedbe
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b6c66d64d7dc7117c5903f1eb3ac2e2ad97178af
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378618"
---
# <a name="multiple-transactions"></a>Mehrere Transaktionen
  Es ist möglich, dass ein Paket nicht miteinander verbundene Transaktionen in einem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket enthält. Immer wenn ein Container in der Mitte einer geschachtelten Hierarchie von Containern keine Transaktionen unterstützt, starten die Container, die sich in der Hierarchie oberhalb oder unterhalb des Containers befinden, separate Transaktionen, wenn sie für die Unterstützung von Transaktionen konfiguriert sind. Die Transaktionen führen einen Commit oder Rollback aus, und zwar nacheinander und beginnend beim innersten Task innerhalb der geschachtelten Containerhierarchie bis zum Paket. Nachdem die innere Transaktion einen Commit ausgeführt hat, erfolgt jedoch kein Rollback, wenn eine äußere Transaktion abgebrochen wird.  
  
## <a name="illustration-of-multiple-transactions"></a>Veranschaulichung mehrerer Transaktionen  
 Ein Paket enthält z. B. einen Sequenzcontainer, der zwei Foreach-Schleifencontainer enthält, und jeder Container enthält zwei SQL Ausführen-Tasks. Der Sequenzcontainer und die Execute SQL-Tasks unterstützen Transaktionen, die Foreach-Schleifencontainer hingegen nicht. In diesem Beispiel startet jeder Execute SQL-Task seine eigene Transaktion und führt keinen Rollback aus, wenn die Transaktion auf dem Sequenztask abgebrochen wurde.  
  
 Die TransactionOption-Eigenschaften des Sequenzcontainers, der Foreach-Schleifencontainer und die Tasks „SQL ausführen“ sind folgendermaßen festgelegt:  
  
-   Die TransactionOption-Eigenschaft des Sequenzcontainers ist auf **Required**festgelegt.  
  
-   Die TransactionOption-Eigenschaften der Foreach-Schleifencontainer sind auf **NotSupported**festgelegt.  
  
-   Die TransactionOption-Eigenschaften der Tasks „SQL ausführen“ sind auf **Required**festgelegt.  
  
 Das folgende Diagramm zeigt die fünf nicht miteinander verbundenen Transaktionen im Paket. Eine Transaktion wird durch den Sequenzcontainer gestartet, und vier Transaktionen werden durch die SQL Ausführen-Tasks gestartet.  
  
 ![Implementierung von mehreren Transaktionen](media/mw-dts-trans2.gif "Implementation of multiple transactions")  
  
## <a name="related-tasks"></a>Related Tasks  
 [Konfigurieren eines Pakets für die Verwendung von Transaktionen](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
