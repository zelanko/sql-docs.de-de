---
title: Gespeicherte Stagingprozedur (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 6e66748610d648ec8e427315d2a317d26e699d06
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52758812"
---
# <a name="staging-stored-procedure-master-data-services"></a>Gespeicherte Stagingprozedur (Master Data Services)
  Wenn Sie den Stagingprozess von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]initiieren, verwenden Sie eine von drei gespeicherten Prozeduren.  
  
-   stg.udp_name_Leaf  
  
-   stg.udp_name_Consolidated  
  
-   stg.udp_name_Relationship  
  
 "name" steht für den Namen der Stagingtabelle, die beim Erstellen der Entität angegeben wurde.  
  
## <a name="staging-process-stored-procedure-parameters"></a>Parameter der gespeicherten Prozeduren für den Stagingprozess  
 In der folgenden Tabelle sind die Parameter dieser gespeicherten Prozeduren aufgeführt.  
  
|Parameter|Description|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Erforderlich|Der Name der Version. Dabei wird ggf. abhängig von der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Sortiereinstellung die Groß-/Kleinschreibung beachtet.|  
|**LogFlag**<br /><br /> Erforderlich|Bestimmt, ob Transaktionen während des Stagingprozesses protokolliert werden. Dabei sind folgende Werte möglich:<br /><br /> **0**: Protokollieren Sie Transaktionen nicht.<br />**1**: Protokollieren von Transaktionen.<br /><br /> <br /><br /> Weitere Informationen über Transaktionen finden Sie unter [Transaktionen &#40;Master Data Services&#41;](transactions-master-data-services.md).|  
|**BatchTag**<br /><br /> Erforderlich, außer vom Webdienst|Der **BatchTag** -Wert wie in der Stagingtabelle angegeben.|  
|**Batch_ID**<br /><br /> Wird nur vom Webdienst benötigt|Der Wert der **Batch_ID** wie in der Stagingtabelle angegeben.|  
  
### <a name="staging-process-stored-procedure-example"></a>Beispiel einer gespeicherten Prozedur für den Stagingprozess  
 Im folgenden Beispiel wird gezeigt, wie der Stagingprozess mit der entsprechenden gespeicherten Prozedur gestartet wird.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
  
GO  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Überprüfungsprozedur &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)   
 [Laden oder Aktualisieren von Elementen in Master Data Services mithilfe des Stagingprozesses](/sql/2014/master-data-services/add-update-and-delete-data-master-data-services)   
 [Anzeigen von Fehlern, die während des Stagingprozesses auftreten &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)  
  
  
