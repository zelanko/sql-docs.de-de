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
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: e3cc04877f54df9c1865633d2ac7ec4430cbbe00
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795898"
---
# <a name="catalogupdatemasteraddress-ssisdb-database"></a>catalog.update_master_address (SSISDB-Datenbank)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Aktualisieren Sie den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Scale Out-Master-Endpunkt.

## <a name="syntax"></a>Syntax

```sql
catalog.update_master_address [@MasterAddress = ] masterAddress
```

## <a name="arguments"></a>Argumente
[ @MasterAddress = ] *masterAddress*  
Der Scale Out-Master-Endpunkt. Die *masterAddress* ist **nvarchar**.  

 ## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 None  

## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
   
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
 
