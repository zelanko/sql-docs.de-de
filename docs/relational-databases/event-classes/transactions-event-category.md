---
description: Transaktionen-Ereigniskategorie
title: Transaktionen-Ereigniskategorie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0d2aff2dd3d5dc601c4b07d01d69a093f92f67d2
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97483462"
---
# <a name="transactions-event-category"></a>Transaktionen-Ereigniskategorie
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
  Die **Transaktionen** -Ereigniskategorie kann zum Überwachen des Status von Transaktionen verwendet werden. Die Ereignisklassennamen mit dem Präfix **TM:** werden zum Nachverfolgen von transaktionsbezogenen Vorgängen verwendet, die über die Schnittstelle zur Transaktionsverwaltung gesendet werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[DTCTransaction (Ereignisklasse)](../../relational-databases/event-classes/dtctransaction-event-class.md)|Verfolgt Transaktionen nach, die vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) koordiniert werden. Hierbei handelt es sich um Transaktionen, die zwischen mindestens zwei Datenbanken oder Instanzen von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]verteilt werden.|  
|[SQLTransaction-Ereignisklasse](../../relational-databases/event-classes/sqltransaction-event-class.md)|Verfolgt die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen BEGIN TRAN, COMMIT TRAN, SAVE TRAN und ROLLBACK TRAN nach.|  
|[TM: Begin Tran Completed (Ereignisklasse)](../../relational-databases/event-classes/tm-begin-tran-completed-event-class.md)|Gibt an, dass eine BEGIN TRANSACTION-Anforderung abgeschlossen wurde.|  
|[TM: Begin Tran Starting (Ereignisklasse)](../../relational-databases/event-classes/tm-begin-tran-starting-event-class.md)|Gibt an, dass eine BEGIN TRANSACTION-Anforderung gestartet wird.|  
|[TM: Commit Tran Completed (Ereignisklasse)](../../relational-databases/event-classes/tm-commit-tran-completed-event-class.md)|Gibt an, dass eine COMMIT TRANSACTION-Anforderung abgeschlossen wurde.|  
|[TM: Commit Tran Starting (Ereignisklasse)](../../relational-databases/event-classes/tm-commit-tran-starting-event-class.md)|Gibt an, dass eine COMMIT TRANSACTION-Anforderung gestartet wird.|  
|[TM: Promote Tran Completed (Ereignisklasse)](../../relational-databases/event-classes/tm-promote-tran-completed-event-class.md)|Gibt an, dass eine PROMOTE TRANSACTION-Anforderung abgeschlossen wurde.|  
|[TM: Promote Tran Starting (Ereignisklasse)](../../relational-databases/event-classes/tm-promote-tran-starting-event-class.md)|Gibt an, dass eine PROMOTE TRANSACTION-Anforderung gestartet wird.|  
|[TM: Rollback Tran Completed (Ereignisklasse)](../../relational-databases/event-classes/tm-rollback-tran-completed-event-class.md)|Gibt an, dass eine ROLLBACK TRANSACTION-Anforderung abgeschlossen wurde.|  
|[TM: Rollback Tran Starting (Ereignisklasse)](../../relational-databases/event-classes/tm-rollback-tran-starting-event-class.md)|Gibt an, dass eine ROLLBACK TRANSACTION-Anforderung gestartet wird.|  
|[TM: Save Tran Completed (Ereignisklasse)](../../relational-databases/event-classes/tm-save-tran-completed-event-class.md)|Gibt an, dass eine SAVE TRANSACTION-Anforderung abgeschlossen wurde.|  
|[TM: Save Tran Starting (Ereignisklasse)](../../relational-databases/event-classes/tm-save-tran-starting-event-class.md)|Gibt an, dass eine SAVE TRANSACTION-Anforderung gestartet wird.|  
|[TransactionLog-Ereignisklasse](../../relational-databases/event-classes/transactionlog-event-class.md)|Verfolgt nach, wenn Transaktionen in das Transaktionsprotokoll einer Datenbank geschrieben werden.|  
  
  
