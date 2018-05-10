---
title: Catalog.add_execution_worker (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 788cae214b3e9cebe8071cf0e0f82e03ac4a528b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>Catalog.add_execution_worker (SSISDB-Datenbank)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Fügt einen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out-Worker einer Instanz der Ausführung in Scale Out hinzu.

## <a name="syntax"></a>Syntax

```sql
catalog.add_execution_worker [@execution_id = ] execution_id, [@workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>Argumente
[ @execution_id = ] *execution_id*  
 Der eindeutige Bezeichner für die Instanz der Ausführung. Der *execution_id* ist **bigint**.  
 
[@workeragent_id = ] *workeragent_id*  
Die Worker-Agent-ID für den Scale Out-Worker. Die *workeragent_id* ist **uniqueIdentifier**.

## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 InclusionThresholdSetting  

## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   READ- und MODIFY-Berechtigungen für die Instanz der Ausführung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
 
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden einige Bedingungen beschrieben, die möglicherweise einen Fehler oder eine Warnung auslösen:  
 
- Der Benutzer verfügt nicht über die entsprechenden Berechtigungen.

- Der Ausführungsbezeichner ist ungültig.

- Die Worker-Agent-ID ist ungültig.

- Die Ausführung erfolgt nicht in horizontaler Hochskalierung.

## <a name="see-also"></a>Weitere Informationen finden Sie unter
[Ausführen von Paketen in horizontaler Hochskalierung](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).

