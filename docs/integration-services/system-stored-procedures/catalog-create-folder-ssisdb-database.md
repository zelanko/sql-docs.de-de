---
title: catalog.create_folder (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 06fb3549-e970-4ca2-a61f-59affb9c6dcc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 27fcf2f52a91464643ddac7e16b64df5ff34f692
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58274445"
---
# <a name="catalogcreatefolder-ssisdb-database"></a>catalog.create_folder (SSISDB-Datenbank)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Ordner im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Katalog.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.create_folder [@folder_name =] folder_name, [@folder_id =] folder_id OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
 [@folder_name =] *folder_name*  
 Der Name des neuen Ordners. Der *folder_name* ist **nvarchar(128)**.  
  
 [@folder_name =] *folder_id*  
 Der eindeutige Bezeichner (ID) des Ordners. Der *folder_id* ist **bigint**.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 Der Ordnerbezeichner wird zurückgegeben.  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
Wenn bereits ein Ordner mit demselben Namen vorhanden ist, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
  
