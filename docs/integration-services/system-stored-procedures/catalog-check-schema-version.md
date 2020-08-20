---
description: catalog.check_schema_version
title: catalog.check_schema_version | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b8f1d04f2a41c247a3de8a66f5b07ee74f5036b5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456995"
---
# <a name="catalogcheck_schema_version"></a>catalog.check_schema_version 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Bestimmt, ob das SSISDB-Katalogschema und die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Binärdateien (ISServerExec- und SQLCLR-Assembly) kompatibel sind.  
  
 ISServerExec.exc protokolliert eine Fehlermeldung, wenn das Schema und die Binärdateien nicht kompatibel sind.  
  
 Die SSISDB-Schemaversion wird inkrementiert, wenn sich das Schema während der Anwendung von Patches und während der Upgrades ändert. Es wird empfohlen, dass Sie diese gespeicherte Prozedur ausführen, nachdem eine SSISDB-Sicherung wiederhergestellt wurde, um sicherzustellen, dass das Schema und die Binärdateien kompatibel sind.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.check_schema_version [ @use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>Argumente  
 [ @use32bitruntime= ] *use32bitruntime*  
 Wenn der Parameter auf **1** festgelegt wird, wird die 32-Bit-Version von dtexec aufgerufen. *use32bitruntime* ist **int**.  
  
## <a name="result-set"></a>Resultset  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert die folgende Berechtigung:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin** .  
  
  
