---
title: Festlegen der SQL Server-Verbindung für den SQL Server-Agent-Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b2857e00a9892922d69a41a293382e77d3d2c49f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634778"
---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie die Verbindung zwischen dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent und [!INCLUDE[ssDE](../../includes/ssde_md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]festlegen. Mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts kann eine Verbindung mit einer lokalen Instanz von SQL Server mit der Windows-Authentifizierung hergestellt werden.  
  
**In diesem Thema**  
  
-   **Vorbereitungen:**  
  
    [Einschränkungen](#Restrictions)  
  
    [Sicherheit](#Security)  
  
-   **Festlegen der SQL Server-Verbindung für den SQL Server-Agent mit:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="Restrictions"></a>Einschränkungen  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten wird nur im Objekt-Explorer angezeigt, wenn Sie die Berechtigung besitzen, ihn zu verwenden.  
  
-   Seit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]unterstützt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung. Diese Option ist nur beim Verwalten früherer Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verfügbar.  
  
### <a name="Security"></a>Sicherheit  
  
#### <a name="Permissions"></a>Berechtigungen  
Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss zur Verwendung der Anmeldeinformationen eines Kontos konfiguriert werden, das Mitglied der festen Serverrolle **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist, um seine Funktionen ausführen zu können. Das Konto muss über die folgenden Windows-Berechtigungen verfügen:  
  
-   Anmelden als Dienst (SeServiceLogonRight)  
  
-   Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
-   Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
-   Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
Weitere Informationen zu den Windows-Berechtigungen, die für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstkonto erforderlich sind, finden Sie unter [Auswählen eines Kontos für den SQL Server-Agent-Dienst](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) und [Einrichten von Windows-Dienstkonten](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-set-the-sql-server-connection"></a>So legen Sie die SQL Server-Verbindung fest  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, für den Sie eine Verbindung mit dem SQL Server-Agent-Dienst einrichten möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent** , und wählen Sie **Eigenschaften**aus.  
  
3.  Klicken Sie im Dialogfeld **SQL Server-Agent-Eigenschaften***Servername* unter **Seite auswählen** auf **Verbindung**.  
  
4.  Wählen Sie unter **SQL Server-Verbindung**die Option **Windows-Authentifizierung verwenden** aus, damit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent beim Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde_md.md)] die [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows-Authentifizierung verwenden kann. Für Verbindungen mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher muss die Windows-Authentifizierung verwendet werden.  
  
