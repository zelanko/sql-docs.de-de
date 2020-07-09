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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc3aae082a59cf122971798739e5add2b1886689
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053694"
---
# <a name="catalogdisable_worker_agent-ssisdb-database"></a>catalog.disable_worker_agent (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Deaktivieren Sie einen Scale Out-Worker für einen Scale Out-Master, der mit diesem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog arbeitet.

## <a name="syntax"></a>Syntax

```sql
catalog.disable_worker_agent [ @WorkerAgentId = ] WorkerAgentId
```
## <a name="arguments"></a>Argumente
[@WorkerAgentId =] *WorkerAgentId* Die Worker-Agent-ID für den Scale Out-Worker. Das Argument *WorkerAgentId* ist vom Typ **uniqueidentifier**.

## <a name="example"></a>Beispiel
In diesem Beispiel wird der Scale Out-Worker auf „MachineA“ deaktiviert.

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
 Keine  

## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin** 

## <a name="errors-and-warnings"></a>Fehler und Warnungen
Wenn die Worker-Agent-ID ungültig ist, gibt die gespeicherte Prozedur einen Fehler zurück.
