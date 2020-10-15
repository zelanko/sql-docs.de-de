---
description: Proxyeigenschaften – Neues Proxykonto (Seite „Allgemein“)
title: Proxyeigenschaften – Neues Proxykonto (Seite „Allgemein“)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.proxy.general.f1
ms.assetid: 5cd81265-bf59-413b-8397-150ddc70d0c7
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a70ba36150771ef90f3cfc9461c018c212da4c73
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037299"
---
# <a name="proxy-account-properties---new-proxy-account-general-page"></a>Proxyeigenschaften – Neues Proxykonto (Seite „Allgemein“)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Auf dieser Seite können Sie die Eigenschaften eines [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Proxykontos aufrufen und ändern.  
  
## <a name="options"></a>Optionen  
**Proxyname**  
Geben Sie den Namen des Proxys ein.  
  
**Name der Anmeldeinformationen**  
Geben Sie den Namen der Anmeldeinformationen für den Proxy ein.  
  
> [!NOTE]  
> Der eingegebene Anmeldeinformationsname muss der Name von vorhandenen Anmeldeinformationen sein. Informationen zum Erstellen von Anmeldeinformationen finden Sie unter [How to: Erstellen von Anmeldeinformationen](../../relational-databases/security/authentication-access/create-a-credential.md).  
  
**...**  
Öffnet das Dialogfeld **Anmeldeinformationen auswählen** .  
  
**Beschreibung**  
Geben Sie die Beschreibung für den Proxy ein.  
  
**Folgenden Subsystemen gegenüber aktiv**  
Wählen Sie die Subsysteme aus, auf die das Proxykonto zugreifen kann.  
  
**Auftragsschritte erneut zuweisen an**  
Wählen Sie den Proxy aus, dem die Auftragsschritte neu zugewiesen werden sollen. Die Liste ist aktiviert, wenn Sie den Zugriff auf ein Subsystem aufheben, auf das der Proxy vorher zugreifen konnte.  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen eines Proxys für den SQL Server-Agent](../../ssms/agent/create-a-sql-server-agent-proxy.md)  
