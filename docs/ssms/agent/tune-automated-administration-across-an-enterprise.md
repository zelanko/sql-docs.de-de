---
description: Optimieren der automatischen Verwaltung in einem Unternehmen
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
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 37f5647c83c7355566561b5d65ecb67f7d668b7d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97422775"
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Optimieren der automatischen Verwaltung in einem Unternehmen

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Die Multiserververwaltung mit dem Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent nutzt die Selbstoptimierungsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Deshalb ist unter normalen Bedingungen keine zusätzliche Auftragsoptimierung erforderlich. Die Belastung des Netzwerks nimmt jedoch zu, wenn Sie Aufträge ausführen, Warnungen generieren und Operatoren benachrichtigen. Sie können die automatische Administration für ein Unternehmen optimieren, um den Netzwerkverkehr zu minimieren, der durch diese Aktivitäten verursacht wird.  

## <a name="see-also"></a>Weitere Informationen

[Überwachen der Leistung der Datenfluss-Engine](../../integration-services/performance/performance-counters.md)