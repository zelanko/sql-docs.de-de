---
title: Optimieren der automatischen Verwaltung in einem Unternehmen
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b43a1298c16ba1e51459852f8c775dd67b5b4a7b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755036"
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Optimieren der automatischen Verwaltung in einem Unternehmen

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Die Multiserververwaltung mit dem Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent nutzt die Selbstoptimierungsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Deshalb ist unter normalen Bedingungen keine zusätzliche Auftragsoptimierung erforderlich. Die Belastung des Netzwerks nimmt jedoch zu, wenn Sie Aufträge ausführen, Warnungen generieren und Operatoren benachrichtigen. Sie können die automatische Administration für ein Unternehmen optimieren, um den Netzwerkverkehr zu minimieren, der durch diese Aktivitäten verursacht wird.  

## <a name="see-also"></a>Weitere Informationen

[Überwachen der Leistung der Datenfluss-Engine](../../integration-services/performance/performance-counters.md)