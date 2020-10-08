---
title: Datenzugriff von CLR-Datenbankobjekten | Microsoft-Dokumentation
description: CLR-Routinen können mithilfe der .NET Framework Datenanbieter für SQL Server, auch als SqlClient bezeichnet, auf Daten innerhalb eines CLR-Datenbankobjekts zugreifen.
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
ms.openlocfilehash: 606beeaf190dfb4eb24101242ba1a6f2212303fb
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810837"
---
# <a name="data-access-from-clr-database-objects"></a>Data Access from CLR Database Objects
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Eine Common Language Runtime-Routine (CLR) kann problemlos auf Daten zugreifen, die in der Instanz von gespeichert [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sind, in der Sie ausgeführt wird, sowie auf Daten, die in Remote Instanzen gespeichert sind. Auf welche Daten die Routine zugreifen kann, wird durch den Benutzerkontext bestimmt, in dem der Code ausgeführt wird. Greifen Sie in einem CLR-Datenbankobjekt auf Daten zu, indem Sie die .NET Framework Datenanbieter für verwenden. Dies wird [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auch als **SqlClient**bezeichnet. Dies ist der gleiche Anbieter, den Entwickler zum Zugriff von verwalteten Clientanwendungen und Anwendungen der mittleren Ebene auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Daten verwenden. Aus diesem Grund können Sie Ihre Kenntnisse über ADO.net und **SqlClient** in Client Anwendungen und Anwendungen der mittleren Ebene nutzen.  
  
> [!NOTE]  
>  Benutzerdefinierten Typmethoden und benutzerdefinierten Funktionen wird nicht ermöglicht, standardmäßig auf Daten zuzugreifen. Sie müssen die **DataAccess** -Eigenschaft von **SqlMethodAttribute** oder **SqlFunctionAttribute** auf **DataAccessKind. Read** festlegen, um schreibgeschützten Datenzugriff von benutzerdefinierten Typen (User-Defined Type, UDT) oder benutzerdefinierten Funktionen zu aktivieren. Datenänderungsvorgänge von UDTs oder benutzerdefinierten Funktionen ausgehend sind nicht zulässig. Ein solcher Versuch löst zur Ausführungszeit eine Ausnahme aus.  
  
 In diesem Abschnitt werden nur die spezifischen Unterschiede der Funktionen und Verhaltensweisen beim Datenzugriff von einem CLR-Datenbankobjekt ausgehend beschrieben. Weitere Informationen zu Funktionen und Funktionalität von ADO.NET finden Sie in der ADO.NET-Dokumentation im .NET Framework SDK.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [Kontextverbindung](../../../relational-databases/clr-integration/data-access/context-connection.md)  
 Beschreibt die Kontextverbindung zu SQL Server.  
  
 [Identitätswechsel und Anmeldeinformationen für Verbindungen](../../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
 Beschreibt die Annahme der Identität von Verbindungen und Verbindungsanmeldeinformationen.  
  
 [Von SQL Server verwendete prozessinterne spezifische Erweiterungen für ADO.NET](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 Erläutert die Prozess internen spezifischen **SqlPipe**-, **SqlContext**-, **SqlTriggerContext**-und **SqlDataRecord** -Objekte.  
  
 [CLR-Integration und Transaktionen](../../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
 Beschreibt wie das neue vom System.Transactions-Namespace bereitgestellte Transaktionsframework in ADO.NET und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-CLRIntegration einbezogen wird.  
  
 [XML-Serialisierung auf Grundlage von CLR-Datenbankobjekten](/dotnet/standard/serialization/introducing-xml-serialization)  
 Erklärt, wie XML-Serialisierungsszenarien von CLR-Datenbankobjekten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aktiviert werden.  
  
