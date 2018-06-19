---
title: catalog.rename_folder (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 336ab467-c32f-4d2e-a79c-174dc6fab75e
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: db70bc495dfbef1a4d1c1e5fffd7bb4631cfcbdf
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35335804"
---
# <a name="catalogrenamefolder-ssisdb-database"></a>catalog.rename_folder (SSISDB-Datenbank)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Benennt einen Ordner im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog um.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.rename_folder [ @old_name = ] old_name , [ @new_name = ] new_name  
```  
  
## <a name="arguments"></a>Argumente  
 [ @old_name = ] *old_name*  
 Der ursprüngliche Name des Ordners. Der *old_name* ist **nvarchar(128)**.  
  
 [ @new_name = ] *new_name*  
 Der neue Name des Ordners. Der *new_name* ist **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 InclusionThresholdSetting  
  
## <a name="result-sets"></a>Resultsets  
 InclusionThresholdSetting  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden einige Bedingungen beschrieben, die möglicherweise einen Fehler oder eine Warnung auslösen:  
  
-   Der ursprüngliche Ordnername ist nicht gültig.  
  
-   Der neue Name wurde bereits für einen vorhandenen Ordner verwendet.  
  
  
