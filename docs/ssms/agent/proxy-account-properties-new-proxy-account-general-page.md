---
title: 'Proxyeigenschaften: Neues Proxykonto (Seite „Allgemein“) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.proxy.general.f1
ms.assetid: 5cd81265-bf59-413b-8397-150ddc70d0c7
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 072910b06ed75a5aad53bb6f51f0d62224144459
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65088777"
---
# <a name="proxy-account-properties---new-proxy-account-general-page"></a>Proxyeigenschaften – Neues Proxykonto (Seite „Allgemein“)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die Eigenschaften für ein Proxykonto für den [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent anzeigen und ändern.  
  
## <a name="options"></a>enthalten  
**Proxyname**  
Geben Sie den Namen des Proxys ein.  
  
**Anmeldeinformationsname**  
Geben Sie den Namen der Anmeldeinformationen für den Proxy ein.  
  
> [!NOTE]  
> Der eingegebene Anmeldeinformationsname muss der Name von vorhandenen Anmeldeinformationen sein. Informationen zum Erstellen von Anmeldeinformationen finden Sie unter [How to: Create a Credential (Vorgehensweise: Erstellen von Anmeldeinformationen)](https://msdn.microsoft.com/c1e77e91-2a69-40d9-b8b3-97cffc710586).  
  
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
  
