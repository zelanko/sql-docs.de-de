---
description: catalog.create_folder (SSISDB-Datenbank)
title: catalog.create_folder (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 06fb3549-e970-4ca2-a61f-59affb9c6dcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9c0c28c81f607f5ab7ddc71d84ae52ea848d9334
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456954"
---
# <a name="catalogcreate_folder-ssisdb-database"></a>catalog.create_folder (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Erstellt einen Ordner im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Katalog.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.create_folder [ @folder_name = ] folder_name, [ @folder_id = ] folder_id OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
 [@folder_name =] *folder_name*  
 Der Name des neuen Ordners. Der *folder_name* ist **nvarchar(128)** .  
  
 [@folder_name =] *folder_id*  
 Der eindeutige Bezeichner (ID) des Ordners. Der *folder_id* ist **bigint**.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 Der Ordnerbezeichner wird zurückgegeben.  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
Wenn bereits ein Ordner mit demselben Namen vorhanden ist, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
  
