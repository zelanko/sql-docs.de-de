---
title: catalog.set_worker_agent_property (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ddd2a534-6925-4d66-90e7-541c14f41de7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ea5a3a5d3d816c8debe1fb51b69a953cf6dd324a
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295240"
---
# <a name="catalogset_worker_agent_property-ssisdb-database"></a>catalog.set_worker_agent_property (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Legt die Eigenschaft eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Scale Out-Workers fest.

## <a name="syntax"></a>Syntax

```sql
catalog.set_worker_agent_property [@WorkerAgentId =] WorkerAgentId, [@PropertyName =] PropertyName, [@PropertyValue =] PropertyValue 
```

## <a name="arguments"></a>Argumente
[@WorkerAgentId =] *WorkerAgentId*  
Die Worker-Agent-ID für den Scale Out-Worker. Das Argument *WorkerAgentId* ist vom Typ **uniqueidentifier**.

[@PropertyName =] *PropertyName*  
Der Name der Eigenschaft. Das Argument *PropertyName* ist vom Typ **nvarchar(256)** .

[@PropertyValue =] *PropertyValue*  
Der Wert der Eigenschaft. Das Argument *PropertyValue* ist vom Typ **nvarchar(max)** .

## <a name="remarks"></a>Remarks
Die gültigen Eigenschaftennamen sind **DisplayName**, **Description**, **Tags**.

## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 None  

## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**

## <a name="errors-and-warnings"></a>Fehler und Warnungen
  In der folgenden Liste werden einige Bedingungen beschrieben, die möglicherweise einen Fehler oder eine Warnung auslösen:  
  
-   Der Benutzer verfügt nicht über die entsprechenden Berechtigungen. 

-   Die Worker-Agent-ID ist ungültig.

-   Der Eigenschaftsname ist ungültig.

-   Der Eigenschaftswert ist ungültig.  
