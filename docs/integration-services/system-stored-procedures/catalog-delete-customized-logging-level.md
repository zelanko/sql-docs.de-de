---
title: catalog.delete_customized_logging_level | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 0aec1e34-f30b-4e5f-bba1-c26665cf2da6
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ebe7fdcfb808f71dd0157647480440595304b33f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="catalogdeletecustomizedlogginglevel"></a>catalog.delete_customized_logging_level
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Löscht einen vorhandenen benutzerdefinierten Protokolliergrad. Weitere Informationen zu benutzerdefinierten Protokolliergraden finden Sie unter [Integration Services &#40;SSIS&#41; Logging (SSIS-Protokollierung [SQL Server Integration Services])](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Syntax  
  
```sql  
delete_customized_logging_level [ @level_name = ] level_name  
  
```  
  
## <a name="arguments"></a>Argumente  
 [ @level_name = ] *level_name*  
 Der Name des vorhandenen zu löschenden benutzerdefinierten Protokolliergrads.  
  
 Das Argument *level_name* ist vom Typ **nvarchar(128)**.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="return-codes"></a>Rückgabecodes  
 0 (Erfolg)  
  
 Wenn die gespeicherte Prozedur fehlschlägt, wird ein Fehler ausgelöst.  
  
## <a name="result-set"></a>Resultset  
 InclusionThresholdSetting  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 Die folgende Liste beschreibt Bedingungen, unter denen die gespeicherte Prozedur fehlschlägt.  
  
-   Der Benutzer verfügt nicht über die erforderlichen Berechtigungen.  
  
  
