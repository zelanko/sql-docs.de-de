---
title: MSSQLSERVER_21899 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 957cb58c292f895e31ae01d9918af4872a29bd9d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415409"
---
# <a name="mssqlserver21899"></a>MSSQLSERVER_21899
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21899|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21899|  
|Meldungstext|Die Abfrage beim umgeleiteten Verleger '%s' zur Bestimmung, ob sysserver-Einträge für die Abonnenten des ursprünglichen Verlegers '%s' vorliegen, ist mit dem Fehler '%d', Fehlermeldung '%s', fehlgeschlagen.|  
  
## <a name="explanation"></a>Erklärung  
 `sp_validate_redirected_publisher` fragt die Abonnementmetadatentabellen von der Verlegerdatenbank beim Remoteserver ab, um seine zugeordneten Abonnenten zu bestimmen. Fehler 21899 wird zurückgegeben, wenn diese Abfrage fehlschlägt. Die Überprüfungsabfrage erfordert Zugriff auf die veröffentlichte Datenbank beim umgeleiteten Verleger. Wenn die Anmeldung, die beim Aufruf von `sp_adddistpublisher` für den ursprünglichen Verleger angegeben wurde, nicht berechtigt ist, beim umgeleiteten Verleger auf die veröffentlichte Datenbank zuzugreifen, wird Fehler 21899 zurückgegeben.  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie die erwähnte Fehlermeldung, um die Fehlerursache zu bestimmen und entsprechende Korrekturmaßnahmen zu ergreifen  
  
  
