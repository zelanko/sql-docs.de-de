---
title: catalog.check_schema_version | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 23746065ca7096b0405114344d4f6a752bfedda1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68110460"
---
# <a name="catalogcheckschemaversion"></a>catalog.check_schema_version 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Bestimmt, ob das SSISDB-Katalogschema und die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Binärdateien (ISServerExec- und SQLCLR-Assembly) kompatibel sind.  
  
 ISServerExec.exc protokolliert eine Fehlermeldung, wenn das Schema und die Binärdateien nicht kompatibel sind.  
  
 Die SSISDB-Schemaversion wird inkrementiert, wenn sich das Schema während der Anwendung von Patches und während der Upgrades ändert. Es wird empfohlen, dass Sie diese gespeicherte Prozedur ausführen, nachdem eine SSISDB-Sicherung wiederhergestellt wurde, um sicherzustellen, dass das Schema und die Binärdateien kompatibel sind.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.check_schema_version [@use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>Argumente  
 [ @use32bitruntime= ] *use32bitruntime*  
 Wenn der Parameter auf **1** festgelegt wird, wird die 32-Bit-Version von dtexec aufgerufen. *use32bitruntime* ist **int**.  
  
## <a name="result-set"></a>Resultset  
 None  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert die folgende Berechtigung:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin** .  
  
  
