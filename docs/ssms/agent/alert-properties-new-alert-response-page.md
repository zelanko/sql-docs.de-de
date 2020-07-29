---
title: Warnungseigenschaften – Neue Warnung (Seite „Antwort“)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.alert.response.f1
ms.assetid: 72daf008-f9ea-4077-b217-5048e7759d3e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3266ae4e031088a0db6155d5ee20e792b6d9365c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749222"
---
# <a name="alert-properties---new-alert-response-page"></a>Warnungseigenschaften – Neue Warnung (Seite „Antwort“)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Auf dieser Seite können Sie einen Auftrag festlegen, der ausgeführt werden und eine Liste von Operatoren abrufen soll, die zur Reaktion auf eine [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Warnung benachrichtigt werden sollen.  

## <a name="options"></a>Tastatur  
**Auftrag ausführen**  
Aktiviert die Optionen **Auftragsliste**, **Neuer Auftrag** und **Auftrag anzeigen** .  
  
**Neuer Auftrag**  
Öffnet das Dialogfeld **Neuer Auftrag** . Diese Schaltfläche ist nicht verfügbar, wenn **Auftrag ausführen** nicht ausgewählt ist.  
  
**Auftrag anzeigen**  
Zeigen Sie den ausgewählten Auftrag an oder ändern Sie ihn. Diese Option ist nicht verfügbar, wenn **Auftrag ausführen** nicht ausgewählt ist.  
  
**Operatoren benachrichtigen**  
Aktiviert die Steuerelemente, mit denen Sie Operatoren hinzufügen, entfernen oder ändern können.  
  
**Operatorliste**  
Enthält die Operatoren, die benachrichtigt werden, wenn eine Warnung auftritt. Aktivieren Sie das Kontrollkästchen **E-Mail**, **Pager**oder **NET SEND** hinter dem Operatornamen, um eine Benachrichtigungsmethode festzulegen. Diese Option ist nicht verfügbar, wenn **Operatoren benachrichtigen** nicht ausgewählt ist.  
  
**E-Mail**  
Verwenden Sie E-Mail zum Benachrichtigen des Operators.  
  
**Pager**  
Verwenden Sie die Pager-E-Mail-Adresse zum Benachrichtigen des Operators.  
  
**NET SEND**  
Verwenden Sie zum Benachrichtigen des Operators die Option **NET SEND** .  
  
**Neuer Operator**  
Zeigt das Dialogfeld **Neuer Operator** an, in dem Sie einen neuen Operator erstellen können.  
  
**Operator anzeigen**  
Zeigt das Dialogfeld **Eigenschaften** für den derzeit ausgewählten Operator an. Über das Dialogfeld **Operator-Eigenschaften** können Sie die Operator-Eigenschaften anzeigen und ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
[Warnungen](../../ssms/agent/alerts.md)  
[Create an Alert Using Severity Level](../../ssms/agent/create-an-alert-using-severity-level.md)  
[Warnungen](../../ssms/agent/alerts.md)  
[Edit an Alert](../../ssms/agent/edit-an-alert.md)  
[Delete an Alert](../../ssms/agent/delete-an-alert.md)  
  
