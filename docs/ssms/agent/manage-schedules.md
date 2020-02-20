---
title: Zeitpläne verwalten
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 91521d9e78bdc91b7e05cbb66b5788950d497561
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251103"
---
# <a name="manage-schedules"></a>Zeitpläne verwalten
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Ermöglicht Ihnen das Anzeigen und Ändern von Eigenschaften für Auftragszeitpläne des [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents  
  
## <a name="options"></a>Tastatur  
**Verfügbare Zeitpläne**  
Führt die für diesen Benutzer verfügbaren Zeitpläne auf. Ein Auftrag und ein Zeitplan müssen denselben Besitzer haben. Deshalb enthält die Liste nur Zeitpläne, die dem Besitzer des Auftrags gehören.  
  
**Name**  
Zeigt den Namen des Zeitplans an.  
  
**Aktiviert**  
Wählen Sie diese Option aus, um den Zeitplan zu aktivieren.  
  
**Beschreibung**  
Beschreibt die Bedingungen, unter denen der Zeitplan den Auftrag ausführt.  
  
**Aufträge im Zeitplan**  
Listet die Auftragsnummern auf, die an den Zeitplan angefügt sind. Wenn Sie auf eine Nummer klicken, zeigen Sie die Eigenschaften des Auftrags an.  
  
**Neu**  
Klicken Sie auf diese Schaltfläche, um einen neuen Zeitplan zu erstellen.  
  
**Löschen**  
Klicken Sie auf diese Schaltfläche, um den ausgewählten Zeitplan zu löschen.  
  
**Eigenschaften**  
Klicken Sie auf diese Schaltfläche, um die Eigenschaften des ausgewählten Zeitplans zu ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
[Anlegen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
  
