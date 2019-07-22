---
title: Fenster „Threads“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: baf2cf64ab638174d3967c33bfa802ed92b2ce31
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68253494"
---
# <a name="transact-sql-debugger---threads-window"></a>Transact-SQL-Debugger – Fenster „Threads“
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Im Fenster **Threads** werden Informationen zu dem [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Thread angezeigt, der von der gerade gedebuggten [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Sitzung verwendet wird. Sie müssen sich im Debugmodus befinden, um die Threadinformationen anzuzeigen.  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Threadfenster zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Fenster**und dann auf **Threads**.  
  
## <a name="columns"></a>Spalte  
 **ID**  
 Ist eine eindeutig kennzeichnende Zahl, die der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger dem Thread zuweist. Um weitere Informationen zum Thread anzuzeigen, wählen Sie in der dynamischen Verwaltungssicht sys.dm_os_threads eine Zeile aus.  
  
 Wenn die Ausführung nicht im Lightweightpooling-Modus erfolgt, wählen Sie die Zeile aus, in der der Wert in „os_thread_id“ mit dem Wert in der Spalte **ID** übereinstimmt. Wenn die Ausführung im Lightweightpooling-Modus erfolgt, wählen Sie die Zeile aus, in der der Wert in „fiber_context_address“ mit dem Wert in der Spalte **ID** übereinstimmt.  
  
 **Name**  
 Zeigt Informationen über die [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Sitzung im Format **ComputerName/InstanceName [SPID]** an.  
  
 **Computername**  
 Der Name des Computers, auf dem die Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] ausgeführt wird, mit der die Abfrage-Editor-Sitzung verbunden ist.  
  
 **InstanceName**  
 Der Name der Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] , mit der die Abfrage-Editor-Sitzung verbunden ist.  
  
 **[SPID]**  
 Die Prozess-ID der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sitzung, die diese Sitzung eindeutig kennzeichnet. Weitere Informationen über die Sitzung können Sie abrufen, indem Sie in der sys.sysprocesses-Sicht die Zeile auswählen, die in der Spalte spid denselben Wert enthält.  
  
 **Speicherort**  
 Zeigt den Namen der Skriptdatei an, die von der gerade gedebuggten Abfrage-Editor-Sitzung verwendet wird.  
  
 **Priority**  
 Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger unterstützt diese Funktion nicht.  
  
 **Angehalten**  
 Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger unterstützt diese Funktion nicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Debugger](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Transact-SQL-Debuggerinformationen](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [sys.dm_os_threads &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)   
 [sys.sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)  
