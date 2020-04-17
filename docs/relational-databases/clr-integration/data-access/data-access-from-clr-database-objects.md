---
title: Datenzugriff von CLR-Datenbankobjekten | Microsoft Docs
description: CLR-Routinen können mithilfe des .NET Framework-Datenanbieters für SQL Server, auch sqlClient genannt, auf Daten innerhalb eines CLR-Datenbankobjekts zugreifen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5fdd552b0954f0eda838743530ab94e73aa27067
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485175"
---
# <a name="data-access-from-clr-database-objects"></a>Data Access from CLR Database Objects
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Eine COMMON Language Runtime (CLR)-Routine kann problemlos [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf Daten zugreifen, die in der Instanz gespeichert sind, in der sie ausgeführt wird, sowie auf Daten, die in Remoteinstanzen gespeichert sind. Auf welche Daten die Routine zugreifen kann, wird durch den Benutzerkontext bestimmt, in dem der Code ausgeführt wird. Greifen Sie mithilfe des .NET Framework Data Provider für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]auf Daten innerhalb eines CLR-Datenbankobjekts **zu.** Dies ist der gleiche Anbieter, den Entwickler zum Zugriff von verwalteten Clientanwendungen und Anwendungen der mittleren Ebene auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Daten verwenden. Aus diesem Grund können Sie Ihr Wissen über ADO.NET und **SqlClient** in Client- und Middle-Tier-Anwendungen nutzen.  
  
> [!NOTE]  
>  Benutzerdefinierten Typmethoden und benutzerdefinierten Funktionen wird nicht ermöglicht, standardmäßig auf Daten zuzugreifen. Sie müssen die **DataAccess-Eigenschaft** von **SqlMethodAttribute** oder **SqlFunctionAttribute** auf **DataAccessKind.Read** festlegen, um den schreibgeschützten Datenzugriff von benutzerdefinierten Typmethoden (UDT) oder benutzerdefinierten Funktionen zu aktivieren. Datenänderungsvorgänge von UDTs oder benutzerdefinierten Funktionen ausgehend sind nicht zulässig. Ein solcher Versuch löst zur Ausführungszeit eine Ausnahme aus.  
  
 In diesem Abschnitt werden nur die spezifischen Unterschiede der Funktionen und Verhaltensweisen beim Datenzugriff von einem CLR-Datenbankobjekt ausgehend beschrieben. Weitere Informationen zu Funktionen und Funktionalität von ADO.NET finden Sie in der ADO.NET-Dokumentation im .NET Framework SDK.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [Kontextverbindung](../../../relational-databases/clr-integration/data-access/context-connection.md)  
 Beschreibt die Kontextverbindung zu SQL Server.  
  
 [Identitätswechsel und Anmeldeinformationen für Verbindungen](../../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
 Beschreibt die Annahme der Identität von Verbindungen und Verbindungsanmeldeinformationen.  
  
 [Von SQL Server verwendete prozessinterne spezifische Erweiterungen für ADO.NET](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 Erläutert die prozessspezifischen **SqlPipe**-, **SqlContext**-, **SqlTriggerContext**- und **SqlDataRecord-Objekte.**  
  
 [CLR-Integration und Transaktionen](../../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
 Beschreibt wie das neue vom System.Transactions-Namespace bereitgestellte Transaktionsframework in ADO.NET und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-CLRIntegration einbezogen wird.  
  
 [XML-Serialisierung auf Grundlage von CLR-Datenbankobjekten](https://msdn.microsoft.com/library/ac84339b-9384-4710-bebc-01607864a344)  
 Erklärt, wie XML-Serialisierungsszenarien von CLR-Datenbankobjekten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aktiviert werden.  
  
  
