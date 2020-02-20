---
title: Resize the Job History Log
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 45f53291d70d08fa75ab158db3911c058fdba5c7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253534"
---
# <a name="resize-the-job-history-log"></a>Resize the Job History Log
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md.md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie Größenbeschränkungen für Auftragsverlaufsprotokolle von [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] festlegen.
  
-   **Vorbereitungen:**  
  
    [Security](#Security)  
  
-   **So legen Sie Größenbeschränkungen für den Auftragsverlauf fest mit**  
  
    [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="Security"></a>Sicherheit  
Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Verwenden von SQL Server Management Studio  
  
*So ändern Sie die Größe des Auftragsverlaufsprotokolls basierend auf der Basisgröße:*
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wählen Sie die Seite **Verlauf** aus, und bestätigen Sie dann, dass **Größe des Auftragsverlaufsprotokolls beschränken** aktiviert ist.  
  
4.  Geben Sie im Feld **Maximale Länge des Auftragsverlaufsprotokolls** die Anzahl von Zeilen ein, die maximal für das Auftragsverlaufsprotokoll zulässig sind.  
  
5.  Geben Sie im Feld **Maximale Zeilenanzahl pro Auftrag in Auftragsverlauf** die Anzahl von Zeilen ein, die maximal für das Auftragsverlaufsprotokoll eines Auftrags zulässig sind.  
  
**So ändern Sie die Größe des Auftragsverlaufsprotokolls basierend auf der Zeit:**
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung zu einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wählen Sie die Seite **Verlauf** aus, und klicken Sie dann auf **Agentverlauf automatisch entfernen**.  
  
4.  Wählen Sie die entsprechende Anzahl der **Tage**, **Wochen** oder **Monate** aus.  
  
