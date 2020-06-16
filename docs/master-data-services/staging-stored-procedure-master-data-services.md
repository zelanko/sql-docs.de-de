---
title: Gespeicherte Stagingprozedur
description: Verwenden Sie eine von drei gespeicherten Prozeduren, um den Stagingprozess von SQL Server Management Studio in Master Data Services zu initiieren.
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 82b068612f0699cdba3788e4931fb6bdfe8c7e69
ms.sourcegitcommit: 7d6eb09588ff3477cf39a8fd507d537a603bc60d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2020
ms.locfileid: "84796501"
---
# <a name="staging-stored-procedure-master-data-services"></a>Gespeicherte Stagingprozedur (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Wenn Sie den Stagingprozess von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]initiieren, verwenden Sie eine von drei gespeicherten Prozeduren.  
  
-   STG. udp_ \<name> _Leaf  
  
-   STG. udp_ \<name> _Consolidated  
  
-   STG. udp_ \<name> _Relationship  
  
 "name" steht für den Namen der Stagingtabelle, die beim Erstellen der Entität angegeben wurde.  
  
## <a name="staging-process-stored-procedure-parameters"></a>Parameter der gespeicherten Prozeduren für den Stagingprozess  
 In der folgenden Tabelle sind die Parameter dieser gespeicherten Prozeduren aufgeführt.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Erforderlich|Der Name der Version. Dabei wird ggf. abhängig von der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Sortiereinstellung die Groß-/Kleinschreibung beachtet.|  
|**LogFlag**<br /><br /> Erforderlich|Bestimmt, ob Transaktionen während des Stagingprozesses protokolliert werden. Mögliche Werte:<br /><br /> **0**: Transaktionen nicht protokollieren.<br /><br /> **1**: Transaktionen protokollieren.<br /><br /> <br /><br /> Weitere Informationen über Transaktionen finden Sie unter [Transaktionen &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md).|  
|**BatchTag**<br /><br /> Erforderlich, außer vom Webdienst|Der **BatchTag** -Wert wie in der Stagingtabelle angegeben.|  
|**Batch_ID**<br /><br /> Wird nur vom Webdienst benötigt|Der Wert der **Batch_ID** wie in der Stagingtabelle angegeben.|  
|**Benutzername**|Optionaler Parameter:|  
|**Benutzer-ID**|Optionaler Parameter:|  
  
### <a name="staging-process-stored-procedure-example"></a>Beispiel einer gespeicherten Prozedur für den Stagingprozess  
 Im folgenden Beispiel wird gezeigt, wie der Stagingprozess mit der entsprechenden gespeicherten Prozedur gestartet wird.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
      @UserName=N'domain\user'  
  
GO  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Die gespeicherte Überprüfungs Prozedur &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Anzeigen von Fehlern, die während des Stagings auftreten &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)  
  
  
