---
description: Fehlerprotokolle des SQL Server-Agents konfigurieren (Seite Allgemein)
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
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 85ae0e4833a1f17f2bd4a795886be8453d61bafd
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482241"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a>Fehlerprotokolle des SQL Server-Agents konfigurieren (Seite Allgemein)

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Verwenden Sie diese Seite zum Anzeigen und Aktualisieren der Einstellungen für die Fehlerprotokolle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents.  
  
## <a name="options"></a>Optionen  
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
  
**Information**  
Schreibt nur Informationsmeldungen in die Protokolldatei.  
  
## <a name="see-also"></a>Weitere Informationen  
[SQL Server-Agent-Fehlerprotokoll](../../ssms/agent/sql-server-agent-error-log.md)  
