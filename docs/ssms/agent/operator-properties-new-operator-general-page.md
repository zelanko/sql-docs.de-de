---
description: Operatoreigenschaften – Neuer Operator (Seite „Allgemein“)
title: Neue Operatoreigenschaften (Seite „Allgemein“)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.operator.general.f1
ms.assetid: c036d1c9-83d1-4a95-b67e-29d283b1a046
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d2ecbd048c1aaca2ac5bfd9d3f025d2e4588d822
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492114"
---
# <a name="operator-properties---new-operator-general-page"></a>Operatoreigenschaften – Neuer Operator (Seite „Allgemein“)

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die allgemeinen Eigenschaften von [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agentoperatoren anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
**Name**  
Ändern Sie den Namen des Operators.  
  
**Enabled**  
Aktiviert den Operator. Bei fehlender Aktivierung werden keine Benachrichtigungen an den Operator gesendet.  
  
**E-Mail-Name**  
Gibt die E-Mail-Adresse des Operators an.  
  
**NET SEND-Adresse**  
Gibt die für **NET SEND**zu verwendende Adresse an.  
  
**Pager-E-Mail-Name**  
Gibt die E-Mail-Adresse für den Pager des Operators an.  
  
**Pager empfangsbereit am**  
Legt fest, zu welchen Zeiten der Pager aktiv ist.  
  
**Montag - Sonntag**  
Wählen Sie die Tage aus, an denen der Pager aktiv ist.  
  
**Arbeitstag - Beginn**  
Wählen Sie die Tageszeit aus, nach deren Eintreten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent Meldungen an den Pager sendet.  
  
**Arbeitstag - Ende**  
Wählen Sie die Tageszeit aus, nach deren Eintreten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent keine weiteren Meldungen an den Pager sendet.  
  
## <a name="see-also"></a>Weitere Informationen  
[Operatoren](../../ssms/agent/operators.md)  
  
