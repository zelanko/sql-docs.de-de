---
title: Verwenden von Leistungsobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1eb49ac4481320c3d37f2ef8a18b9070a990d47b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679118"
---
# <a name="use-performance-objects"></a>Verwenden von Leistungsobjekten
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent umfasst Leistungsobjekte und -indikatoren zum Überwachen der Leistung des Diensts. Mithilfe dieser Leistungsobjekte können Sie das Windows-Tool Systemmonitor verwenden, um festzustellen, welche Vorgänge vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst im Hintergrund ausgeführt werden. Sie können beispielsweise die Anzahl der aktiven Aufträge feststellen, die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst aktuell ausgeführt werden, um blockierte Aufträge zu identifizieren.  
  
Die Leistungsobjekte und Leistungsindikatoren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts sind für jede Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden, die auf einem Computer installiert ist. Leistungsobjekte sind nach der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benannt, die jedes Objekt repräsentiert.  
  
Die folgende Tabelle veranschaulicht, wie die Leistungsobjekte des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts benannt werden:  
  
|Instanztyp|Objektname|  
|-----------------|---------------|  
|Default|**SQLAgent:**_Objekt_:_Indikator_|  
|Benannt|**SQLAgent$**<br /> **&#42;Instanzname&#42; :**_Objekt_:_Indikator_|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beinhaltet die folgenden Leistungsobjekte für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent.  
  
|Objektname|und Beschreibung|  
|---------------|---------------|  
|[SQLAgent:Aufträge](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|Leistungsinformationen zu gestarteten Aufträgen, Erfolgsrate und aktuellem Status|  
|[SQLAgent:Auftragsschritte](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|Statusinformationen zu Auftragsschritten|  
|[SQLAgent:Warnungen](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|Informationen zur Anzahl der Warnungen und Benachrichtigungen|  
|[SQLAgent:Statistik](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|Allgemeine Leistungsinformationen|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
[Vorgehensweise: Starten des Systemmonitors (Windows)](http://msdn.microsoft.com/5e51bb79-5737-470b-9c47-fac330c001c5)  
  
