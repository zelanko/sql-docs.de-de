---
title: Optimieren der automatischen Verwaltung in einem Unternehmen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5434b81708303c1b10f46ff4fc4f4fc1802b91a8
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "42775728"
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Optimieren der automatischen Verwaltung in einem Unternehmen
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Die Multiserververwaltung mit dem Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent nutzt die Selbstoptimierungsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Deshalb ist unter normalen Bedingungen keine zusätzliche Auftragsoptimierung erforderlich. Die Belastung des Netzwerks nimmt jedoch zu, wenn Sie Aufträge ausführen, Warnungen generieren und Operatoren benachrichtigen. Sie können die automatische Administration für ein Unternehmen optimieren, um den Netzwerkverkehr zu minimieren, der durch diese Aktivitäten verursacht wird.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  

  [Überwachen der Leistung der Datenfluss-Engine](../../integration-services/performance/performance-counters.md)  
  
