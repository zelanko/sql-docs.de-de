---
title: catalog.set_folder_description (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 802416f6-5177-4db5-bca5-976dec5faf53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3330e1972afe3d5cac62af27d122f72f387d0106
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85674816"
---
# <a name="catalogset_folder_description-ssisdb-database"></a>catalog.set_folder_description (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Legt die Beschreibung eines Ordners im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Katalog fest.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.set_folder_description [ @folder_name = ] folder_name  
    , [ @folder_description = ] folder_description  
```  
  
## <a name="arguments"></a>Argumente  
 [ @folder_name = ] *folder_name*  
 Der Name des Ordners. Der *folder_name* ist **nvarchar(128)** .  
  
 [ @folder_description = ] *folder_description*  
 Die Beschreibung des Ordners. Der *folder_description* ist **nvarchar(MAX)** .  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 Die gespeicherte Prozedur gibt eine Meldung zurück, um das Festlegen der neuen Ordnerbeschreibung zu bestätigen.  
  
  
