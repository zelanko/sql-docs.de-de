---
description: catalog.rename_folder (SSISDB-Datenbank)
title: catalog.rename_folder (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 336ab467-c32f-4d2e-a79c-174dc6fab75e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 65b913576b68e5c84037eac57205b23b81d53f95
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96129763"
---
# <a name="catalogrename_folder-ssisdb-database"></a>catalog.rename_folder (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
 Keine  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden einige Bedingungen beschrieben, die möglicherweise einen Fehler oder eine Warnung auslösen:  
  
-   Der ursprüngliche Ordnername ist nicht gültig.  
  
-   Der neue Name wurde bereits für einen vorhandenen Ordner verwendet.  
  
  
