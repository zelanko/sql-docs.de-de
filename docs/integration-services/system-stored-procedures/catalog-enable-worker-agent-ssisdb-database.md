---
title: catalog.enable_worker_agent (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c6e5266b-c32d-49ff-aa69-f09664009fb4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 18ae5a5f9dd36f8ee39ae431bbb20c07dcb78a2d
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913030"
---
# <a name="catalogenable_worker_agent-ssisdb-database"></a>catalog.enable_worker_agent (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Aktivieren Sie einen Scale Out-Worker für einen Scale Out-Master, der mit diesem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog arbeitet.

## <a name="syntax"></a>Syntax

```sql
catalog.enable_worker_agent [ @WorkerAgentId = ] WorkerAgentId
```
## <a name="arguments"></a>Argumente
[@WorkerAgentId =] *WorkerAgentId* Die Worker-Agent-ID für den Scale Out-Worker. Das Argument *WorkerAgentId* ist vom Typ **uniqueidentifier**.

## <a name="example"></a>Beispiel
In diesem Beispiel wird der Scale Out-Worker auf „MachineA“ aktiviert.

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  

## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin** 

## <a name="errors-and-warnings"></a>Fehler und Warnungen
Wenn die Worker-Agent-ID ungültig ist, gibt die gespeicherte Prozedur einen Fehler zurück.
