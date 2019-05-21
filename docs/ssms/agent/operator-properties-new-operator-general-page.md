---
title: Operatoreigenschaften – Neuer Operator (Seite „Allgemein“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.operator.general.f1
ms.assetid: c036d1c9-83d1-4a95-b67e-29d283b1a046
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 822bb95a67d3e2916a55d904e47ae0ee6ec15690
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105377"
---
# <a name="operator-properties---new-operator-general-page"></a>Operatoreigenschaften – Neuer Operator (Seite „Allgemein“)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die allgemeinen Eigenschaften von Agentoperatoren in [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzeigen und ändern.  
  
## <a name="options"></a>Optionen  
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
  
