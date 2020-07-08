---
title: catalog.update_master_address (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
author: haoqian
ms.author: haoqian
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: afcd5083c5b0132d2594c45690b10f2a69371e70
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85673984"
---
# <a name="catalogupdate_master_address-ssisdb-database"></a>catalog.update_master_address (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/applies-to-version/sqlserver2017.md)]

Aktualisieren Sie den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out-Master-Endpunkt.

## <a name="syntax"></a>Syntax

```sql
catalog.update_master_address [ @MasterAddress = ] masterAddress
```

## <a name="arguments"></a>Argumente
[ @MasterAddress = ] *masterAddress*  
Der Scale Out-Master-Endpunkt. Die *masterAddress* ist **nvarchar**.  

 ## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  

## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
   
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
 
