---
title: Konfigurieren von Fehlerprotokollen (Seite „Allgemein“)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1f5c804350a71ae4834a1bbc689a2bc3d6fbc73c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75246079"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a>Fehlerprotokolle des SQL Server-Agents konfigurieren (Seite Allgemein)

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Verwenden Sie diese Seite zum Anzeigen und Aktualisieren der Einstellungen für die Fehlerprotokolle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents.  
  
## <a name="options"></a>Tastatur  
**Fehlerprotokolldatei**  
Gibt die Datei an, in die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent die Fehlerprotokolle schreibt.  
  
**...**  
Mit dieser Schaltfläche können Sie nach der Fehlerprotokolldatei suchen.  
  
**OEM-Fehlerprotokoll schreiben**  
Speichert die Fehlerprotokolldatei als Nicht-Unicode-Datei. Dadurch wird der für die Protokolldatei erforderliche Datenträgerspeicherplatz reduziert. Meldungen, die Unicode enthalten, können jedoch schwieriger lesbar sein, wenn diese Option aktiviert ist.  
  
**Fehler**  
Schreibt nur Fehler und Informationsmeldungen in die Protokolldatei.  
  
**Warnungen**  
Schreibt nur Warnungen und Informationsmeldungen in die Protokolldatei.  
  
**Informationen**  
Schreibt nur Informationsmeldungen in die Protokolldatei.  
  
## <a name="see-also"></a>Weitere Informationen  
[SQL Server-Agent-Fehlerprotokoll](../../ssms/agent/sql-server-agent-error-log.md)  
  
