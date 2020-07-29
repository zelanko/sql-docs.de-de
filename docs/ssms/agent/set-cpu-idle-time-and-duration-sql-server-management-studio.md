---
title: Festlegen der Leerlaufzeit und Leerlaufdauer der CPU
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f1ec4e6af0da5c218eb217986d3f20079d78394d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85644633"
---
# <a name="set-cpu-idle-time-and-duration"></a>Festlegen der Leerlaufzeit und Leerlaufdauer der CPU

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird erläutert, wie Sie die CPU-Leerlaufbedingung für den Server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]definieren. Die CPU-Leerlaufdefinition beeinflusst die Reaktion des [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents auf Ereignisse. Nehmen wir beispielsweise an, dass Sie die CPU als im Leerlauf befindlich definieren, wenn die durchschnittliche CPU-Auslastung unter 10 Prozent fällt und für 10 Minuten auf dieser Stufe bleibt. Wenn Sie Aufträge definiert haben, die immer dann ausgeführt werden sollen, wenn die Server-CPU eine Leerlaufbedingung erfüllt, wird der Auftrag gestartet, wenn die CPU-Auslastung unter 10 Prozent fällt und für 10 Minuten auf dieser Stufe bleibt. Wenn es sich dabei um einen Auftrag handelt, der sich spürbar auf die Serverleistung auswirkt, ist die Art wichtig, wie Sie die CPU-Leerlaufbedingung definieren.  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>So legen Sie die Leerlaufzeit und die Leerlaufdauer der CPU fest  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, klicken Sie auf **Eigenschaften**, und wählen Sie dann die Seite **Erweitert** aus.  
  
3.  Führen Sie unter **Bedingung für 'CPU im Leerlauf'** eine der folgenden Aktionen aus :  
  
    -   Aktivieren Sie **Bedingung für 'CPU im Leerlauf' definieren**.  
  
    -   Geben Sie einen Prozentsatz für das Feld **Bei durchschnittlicher CPU-Nutzung unter** (für alle CPUs) an. Damit wird die Auslastungsgrenze festgelegt, unterhalb der die CPU als im Leerlauf befindlich angesehen wird.  
  
    -   Geben Sie einen Wert für Sekunden im Feld **und Verbleiben unterhalb dieser Stufe für** an. Damit wird die Dauer der minimalen CPU-Auslastung angegeben, bevor die CPU als im Leerlauf befindlich angesehen wird.  
  
