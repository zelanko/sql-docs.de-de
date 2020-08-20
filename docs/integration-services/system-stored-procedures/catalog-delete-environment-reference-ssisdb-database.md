---
description: catalog.delete_environment_reference (SSISDB-Datenbank)
title: catalog.delete_environment_reference (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 1f68f157-c4e9-412c-92b3-53a2faaba29b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ec190a40b71b874d2b888adff31ad99a41db1f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456922"
---
# <a name="catalogdelete_environment_reference-ssisdb-database"></a>catalog.delete_environment_reference (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht einen Umgebungsverweis aus einem Projekt im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.delete_environment_reference [ @reference_id = ] reference_id  
```  
  
## <a name="arguments"></a>Argumente  
 [ @reference_id = ] *reference_id*  
 Der eindeutige Bezeichner des Umgebungsverweises. Der *reference_id* ist **bigint**.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   MODIFY-Berechtigung für das Projekt  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden einige Bedingungen beschrieben, die möglicherweise einen Fehler oder eine Warnung auslösen:  
  
-   Der Bezeichner des Umgebungsverweises ist nicht gültig.  
  
-   Der Benutzer verfügt nicht über die entsprechenden Berechtigungen.  
  
  
