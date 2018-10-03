---
title: catalog.delete_project (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: f3431445-8dd2-443b-813e-b99db893977e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2b6235eadbbc2dea71ca809be42c3f81934c4495
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628348"
---
# <a name="catalogdeleteproject-ssisdb-database"></a>catalog.delete_project (SSISDB-Datenbank)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Löscht ein vorhandenes Projekt aus einem Ordner im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.delete_project [ @folder_name = ] folder_name , [ @project_name = ] project_name  
```  
  
## <a name="arguments"></a>Argumente  
 [ @folder_name = ] *folder_name*  
 Der Name des Ordners, der das Projekt enthält. *folder_name* ist **nvarchar(128)**  
  
 [ @project_name = ] *project_name*  
 Der Name des Projekts, das gelöscht werden soll. *project_name* ist **nvarchar(128)**  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung und MODIFY-Berechtigung für das Projekt  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden Bedingungen beschrieben, die möglicherweise bewirken, dass die gespeicherte Prozedur „delete_project“ einen Fehler auslöst:  
  
-   Das Projekt ist nicht vorhanden.  
  
-   Der Ordner ist nicht vorhanden.  
  
-   Der Benutzer verfügt nicht über die entsprechenden Berechtigungen.  
  
## <a name="remarks"></a>Remarks  
 Alle Objekte und Umgebungsverweise des entsprechenden Projekts werden zusammen mit dem Projekt gelöscht. Die Versionen des Projekts und die relevanten Vorgangsdatensätze werden jedoch bis zur nächsten Ausführung des Vorgangscleanupauftrags beibehalten.  
  
  
