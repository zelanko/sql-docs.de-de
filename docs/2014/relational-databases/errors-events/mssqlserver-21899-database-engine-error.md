---
title: MSSQLSERVER_21899 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 76c7fdccdb05e5cbe99c073c2f3f5613c17c734b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553385"
---
# <a name="mssqlserver_21899"></a>MSSQLSERVER_21899
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21899|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21899|  
|Meldungstext|Die Abfrage beim umgeleiteten Verleger '%s' zur Bestimmung, ob sysserver-Einträge für die Abonnenten des ursprünglichen Verlegers '%s' vorliegen, ist mit dem Fehler '%d', Fehlermeldung '%s', fehlgeschlagen.|  
  
## <a name="explanation"></a>Erklärung  
 `sp_validate_redirected_publisher` fragt die Abonnementmetadatentabellen von der Verlegerdatenbank beim Remoteserver ab, um seine zugeordneten Abonnenten zu bestimmen. Fehler 21899 wird zurückgegeben, wenn diese Abfrage fehlschlägt. Die Überprüfungsabfrage erfordert Zugriff auf die veröffentlichte Datenbank beim umgeleiteten Verleger. Wenn die Anmeldung, die beim Aufruf von `sp_adddistpublisher` für den ursprünglichen Verleger angegeben wurde, nicht berechtigt ist, beim umgeleiteten Verleger auf die veröffentlichte Datenbank zuzugreifen, wird Fehler 21899 zurückgegeben.  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie die erwähnte Fehlermeldung, um die Fehlerursache zu bestimmen und entsprechende Korrekturmaßnahmen zu ergreifen  
  
  
