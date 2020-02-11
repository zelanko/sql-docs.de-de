---
title: Datenzugriff von CLR-Datenbankobjekten | Microsoft-Dokumentation
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
ms.openlocfilehash: 29110ecb83493ec95fbc594d0f743c3c4cb07a68
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68216401"
---
# <a name="data-access-from-clr-database-objects"></a>Data Access from CLR Database Objects
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Eine Common Language Runtime-Routine (CLR) kann problemlos auf Daten zugreifen, die in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Instanz von gespeichert sind, in der Sie ausgeführt wird, sowie auf Daten, die in Remote Instanzen gespeichert sind. Auf welche Daten die Routine zugreifen kann, wird durch den Benutzerkontext bestimmt, in dem der Code ausgeführt wird. Greifen Sie in einem CLR-Datenbankobjekt auf Daten zu, indem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Sie die .NET Framework Datenanbieter für verwenden. Dies wird auch als **SqlClient**bezeichnet. Dies ist der gleiche Anbieter, den Entwickler zum Zugriff von verwalteten Clientanwendungen und Anwendungen der mittleren Ebene auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Daten verwenden. Aus diesem Grund können Sie Ihre Kenntnisse über ADO.net und **SqlClient** in Client Anwendungen und Anwendungen der mittleren Ebene nutzen.  
  
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
  
 [XML-Serialisierung auf Grundlage von CLR-Datenbankobjekten](https://msdn.microsoft.com/library/ac84339b-9384-4710-bebc-01607864a344)  
 Erklärt, wie XML-Serialisierungsszenarien von CLR-Datenbankobjekten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aktiviert werden.  
  
  
