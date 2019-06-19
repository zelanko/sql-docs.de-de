---
title: Auftragseigenschaften – Neuer Auftrag (Seite „Zeitpläne“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.schedules.f1
ms.assetid: 0b03585b-a510-484d-8a63-9b32459def9c
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b0444310b6c0d226fefe093c281cf9e96c2ca0c4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65095817"
---
# <a name="job-properties---new-job-schedules-page"></a>Auftragseigenschaften – Neuer Auftrag (Seite „Zeitpläne“)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie Zeitpläne für einen [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentauftrag anzeigen und verwalten.  
  
## <a name="options"></a>enthalten  
**Zeitplanliste**  
Führt die Zeitpläne für diesen Auftrag auf.  
  
**Neu**  
Erstellt einen neuen Zeitplan. Nachdem Sie den Zeitplan erstellt haben, wird er dem Auftrag hinzugefügt.  
  
**Auswählen**  
Wählt einen Zeitplan aus den vorhandenen Zeitplänen aus. Da ein Auftrag und ein Zeitplan denselben Besitzer haben müssen, können Sie mit dieser Option nur unter Zeitplänen auswählen, deren Besitzer Sie sind.  
  
**Bearbeiten**  
Bearbeitet den ausgewählten Zeitplan, um die Eigenschaften des Auftragszeitplans zu ändern.  
  
**Entfernen**  
Entfernt den ausgewählten Zeitplan aus der Liste für den Auftrag. Wenn keine anderen Aufträge diesen Zeitplan verwenden, wird der Zeitplan aus der Datenbank gelöscht.  
  
## <a name="see-also"></a>Weitere Informationen  
[Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)  
  
