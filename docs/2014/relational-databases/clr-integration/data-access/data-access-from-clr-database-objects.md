---
title: Datenzugriff von CLR-Datenbankobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 4561c7b8979a919ea144bab6d9b42f722b089e48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62874080"
---
# <a name="data-access-from-clr-database-objects"></a>Data Access from CLR Database Objects
  Eine Routine für common Language Runtime (CLR) kann einfach Zugriff auf Daten in der Instanz von [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] in der er, sowie Daten in Remoteinstanzen ausgeführt wird. Auf welche Daten die Routine zugreifen kann, wird durch den Benutzerkontext bestimmt, in dem der Code ausgeführt wird. Zugriff auf Daten aus einem CLR-Datenbankobjekt mithilfe der .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Daten von verwalteten Clientanwendungen und Anwendungen der mittleren Ebene. Daher können Sie Ihre ADO.NET- und `SqlClient`-Kenntnisse in Clientanwendungen und Anwendungen der mittleren Ebene nutzen.  
  
> [!NOTE]  
>  Benutzerdefinierten Typmethoden und benutzerdefinierten Funktionen wird nicht ermöglicht, standardmäßig auf Daten zuzugreifen. Sie müssen die `DataAccess`-Eigenschaft von `SqlMethodAttribute` oder `SqlFunctionAttribute` auf `DataAccessKind.Read` festlegen, um schreibgeschützten Datenzugriff von benutzerdefinierten Typmethoden (User Defined Type, UDT) oder benutzerdefinierten Funktionen zu aktivieren. Datenänderungsvorgänge von UDTs oder benutzerdefinierten Funktionen ausgehend sind nicht zulässig. Ein solcher Versuch löst zur Ausführungszeit eine Ausnahme aus.  
  
 In diesem Abschnitt werden nur die spezifischen Unterschiede der Funktionen und Verhaltensweisen beim Datenzugriff von einem CLR-Datenbankobjekt ausgehend beschrieben. Weitere Informationen zu Funktionen und Funktionalität von ADO.NET finden Sie in der ADO.NET-Dokumentation im .NET Framework SDK.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [Kontextverbindung](context-connection.md)  
 Beschreibt die Kontextverbindung zu SQL Server.  
  
 [Identitätswechsel und Anmeldeinformationen für Verbindungen](impersonation-and-credentials-for-connections.md)  
 Beschreibt die Annahme der Identität von Verbindungen und Verbindungsanmeldeinformationen.  
  
 [Von SQL Server verwendete prozessinterne spezifische Erweiterungen für ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 Erläutert die prozessinternen spezifischen `SqlPipe`, `SqlContext`, `SqlTriggerContext` und `SqlDataRecord`-Objekte.  
  
 [CLR-Integration und -Transaktionen](../../native-client-ole-db-transactions/transactions.md)  
 Beschreibt wie das neue vom System.Transactions-Namespace bereitgestellte Transaktionsframework in ADO.NET und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-CLRIntegration einbezogen wird.  
  
 [XML-Serialisierung auf Grundlage von CLR-Datenbankobjekten](../../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)  
 Erklärt, wie XML-Serialisierungsszenarien von CLR-Datenbankobjekten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aktiviert werden.  
  
  
