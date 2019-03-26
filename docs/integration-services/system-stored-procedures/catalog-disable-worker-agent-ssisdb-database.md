---
title: catalog.disable_worker_agent (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3f19dc4c-a000-4318-8fe1-e80d56720e66
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 908b0fa8c26d14026ead162a94b44af2664ea4e5
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58279804"
---
# <a name="catalogdisableworkeragent-ssisdb-database"></a>catalog.disable_worker_agent (SSISDB-Datenbank)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Deaktivieren Sie einen Scale Out-Worker für einen Scale Out-Master, der mit diesem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog arbeitet.

## <a name="syntax"></a>Syntax

```sql
catalog.disable_worker_agent [@WorkerAgentId =] WorkerAgentId
```
## <a name="arguments"></a>Argumente
[@WorkerAgentId =] *WorkerAgentId* Die Worker-Agent-ID für den Scale Out-Worker. Das Argument *WorkerAgentId* ist vom Typ **uniqueidentifier**.

## <a name="example"></a>Beispiel
In diesem Beispiel wird der Worker für horizontales Hochskalieren auf „MachineA“ deaktiviert.

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[disable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 None  

## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin** 

## <a name="errors-and-warnings"></a>Fehler und Warnungen
Wenn die Worker-Agent-ID ungültig ist, gibt die gespeicherte Prozedur einen Fehler zurück.
