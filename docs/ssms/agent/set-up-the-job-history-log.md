---
description: Set Up the Job History Log
title: Set Up the Job History Log
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: d00c7cb8ee961dca15a7fcdfe0950963e7dec7b2
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97402486"
---
# <a name="set-up-the-job-history-log"></a>Set Up the Job History Log
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie das Auftragsverlaufsprotokoll des [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents einrichten.  
  
-   **Vorbereitungen:**  [Sicherheit](#Security)  
  
-   **Einrichten des Auftragsverlaufsprotokolls mit:** [SQL Server Management Studio](#SSMS)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="security"></a><a name="Security"></a>Sicherheit  
Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Verwenden von SQL Server Management Studio  
**So richten Sie das Auftragsverlaufsprotokoll ein**  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wählen Sie im Dialogfeld **Eigenschaften des SQL Server-Agents** die Seite **Verlauf** aus.  
  
4.  Sie können zwischen folgenden Optionen wählen:  
  
    1.  Aktivieren Sie die Option **Größe des Auftragsverlaufsprotokolls beschränken**, und geben Sie dann die maximale Anzahl von Zeilen für das Auftragsverlaufsprotokoll sowie die maximale Anzahl von Zeilen je Auftrag ein.  
  
    2.  Aktivieren Sie die Option **Agentverlauf automatisch entfernen**, und geben Sie den Zeitraum an, nach dem ältere Verlaufsdaten aus dem Protokoll gelöscht werden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)  
[Überwachen der Auftragsaktivität](../../ssms/agent/monitor-job-activity.md)  
[Erstellen von Aufträgen](../../ssms/agent/create-jobs.md)  
