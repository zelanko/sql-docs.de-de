---
description: catalog.delete_environment (SSISDB-Datenbank)
title: catalog.delete_environment (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: d44b765f-9523-4e6a-bb17-37846d5e5334
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ea6093e6c4f3359d1178879295448531009ff090
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456893"
---
# <a name="catalogdelete_environment-ssisdb-database"></a>catalog.delete_environment (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht eine Umgebung aus einem Ordner im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Katalog.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.delete_environment [ @folder_name = ] folder_name , [ @environment_name = ] environment_name  
```  
  
## <a name="arguments"></a>Argumente  
 [ @folder_name = ] *folder_name*  
 Der Name des Ordners, der die Umgebung enthält. Der *folder_name* ist **nvarchar(128)** .  
  
 [ @environment_name = ] *environment_name*  
 Der Name der Umgebung, die gelöscht werden soll. Der *environment_name* ist **nvarchar(128)** .  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung und MODIFY-Berechtigung für die Umgebung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden einige Bedingungen beschrieben, die möglicherweise einen Fehler oder eine Warnung auslösen:  
  
-   Die angegebene Umgebung ist nicht vorhanden.  
  
-   Der Benutzer verfügt nicht über die entsprechenden Berechtigungen.  
  
  
