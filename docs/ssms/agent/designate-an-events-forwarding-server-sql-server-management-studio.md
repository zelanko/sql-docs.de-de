---
title: Bestimmen eines Ereignisweiterleitungsserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e220c071e9f33dabff11a05d93359dc4179da135
ms.sourcegitcommit: 57e20b7d02853ec9af46b648106578aed133fb45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69552940"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a>Designate an Events Forwarding Server (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie einen Server bestimmen, auf den von [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ereignisse in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Ereignisweiterleitung gilt für Ereignisse, die zwischen Servern weitergeleitet werden, und nicht für Ereignisse, die zwischen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weitergeleitet werden, die auf einem einzelnen Computer gehostet werden. Beachten Sie außerdem, dass zum Empfangen weitergeleiteter Ereignisse der Warnungsverwaltungsserver eine Standardinstanz von SQL Server sein muss.  
  
## <a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="Security"></a>Sicherheit  
  
#### <a name="Permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-designate-an-events-forwarding-server"></a>So bestimmen Sie einen Ereignisweiterleitungsserver  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, von dem aus Sie Ereignisse an andere Server weiterleiten möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent** , und wählen Sie **Eigenschaften**aus.  
  
3.  Klicken Sie im Dialogfeld **Eigenschaften des SQL Server-Agents >** _Servername_ unter **Seite auswählen** auf **Erweitert**.  
  
4.  Aktivieren Sie unter **SQL Server-Ereignisweiterleitung**das Kontrollkästchen **Ereignisse an anderen Server weiterleiten** .  
  
5.  Klicken Sie in der Liste **Server** auf einen Server, und wählen Sie dann unter **Ereignisse**eine der folgenden Aktionen aus:  
  
    -   Klicken Sie auf **Ereignisse ohne Behandlung** , um nur Ereignisse weiterzuleiten, die noch nicht von lokalen Warnungen verarbeitet wurden.  
  
    -   Klicken Sie auf **Alle Ereignisse** , um alle Ereignisse unabhängig davon weiterzuleiten, ob sie von lokalen Warnungen verarbeitet wurden.  
  
6.  Klicken Sie in der Liste **Bei diesem Schweregrad des Ereignisses oder darüber** auf den Schweregrad, bei dem Ereignisse an den ausgewählten Server weitergeleitet werden.  
  
7.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
