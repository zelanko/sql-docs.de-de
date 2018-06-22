---
title: Transaktionen-Ereigniskategorie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c58f6393cc722eed061e83299bff1e825d47a93
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060272"
---
# <a name="transactions-event-category"></a>Transaktionen-Ereigniskategorie
  Die **Transaktionen** -Ereigniskategorie kann zum Überwachen des Status von Transaktionen verwendet werden. Die Ereignisklassennamen mit dem Präfix **TM:** werden zum Nachverfolgen von transaktionsbezogenen Vorgängen verwendet, die über die Schnittstelle zur Transaktionsverwaltung gesendet werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[DTCTransaction (Ereignisklasse)](dtctransaction-event-class.md)|Verfolgt Transaktionen nach, die vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) koordiniert werden. Hierbei handelt es sich um Transaktionen, die zwischen mindestens zwei Datenbanken oder Instanzen von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]verteilt werden.|  
|[SQLTransaction-Ereignisklasse](sqltransaction-event-class.md)|Verfolgt die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen BEGIN TRAN, COMMIT TRAN, SAVE TRAN und ROLLBACK TRAN nach.|  
|[TM: Begin Tran Completed (Ereignisklasse)](tm-begin-tran-completed-event-class.md)|Gibt an, dass eine BEGIN TRANSACTION-Anforderung abgeschlossen wurde.|  
|[TM: Begin Tran Starting (Ereignisklasse)](tm-begin-tran-starting-event-class.md)|Gibt an, dass eine BEGIN TRANSACTION-Anforderung gestartet wird.|  
|[TM: Commit Tran Completed-Ereignisklasse](tm-commit-tran-completed-event-class.md)|Gibt an, dass eine COMMIT TRANSACTION-Anforderung abgeschlossen wurde.|  
|[TM: Commit Tran Starting (Ereignisklasse)](tm-commit-tran-starting-event-class.md)|Gibt an, dass eine COMMIT TRANSACTION-Anforderung gestartet wird.|  
|[TM: Promote Tran Completed (Ereignisklasse)](tm-promote-tran-completed-event-class.md)|Gibt an, dass eine PROMOTE TRANSACTION-Anforderung abgeschlossen wurde.|  
|[TM: Promote Tran Starting (Ereignisklasse)](tm-promote-tran-starting-event-class.md)|Gibt an, dass eine PROMOTE TRANSACTION-Anforderung gestartet wird.|  
|[TM: Rollback Tran Completed (Ereignisklasse)](tm-rollback-tran-completed-event-class.md)|Gibt an, dass eine ROLLBACK TRANSACTION-Anforderung abgeschlossen wurde.|  
|[TM: Rollback Tran Starting (Ereignisklasse)](tm-rollback-tran-starting-event-class.md)|Gibt an, dass eine ROLLBACK TRANSACTION-Anforderung gestartet wird.|  
|[TM: Save Tran Completed-Ereignisklasse](tm-save-tran-completed-event-class.md)|Gibt an, dass eine SAVE TRANSACTION-Anforderung abgeschlossen wurde.|  
|[TM: Save Tran Starting (Ereignisklasse)](tm-save-tran-starting-event-class.md)|Gibt an, dass eine SAVE TRANSACTION-Anforderung gestartet wird.|  
|[TransactionLog-Ereignisklasse](transactionlog-event-class.md)|Verfolgt nach, wenn Transaktionen in das Transaktionsprotokoll einer Datenbank geschrieben werden.|  
  
  