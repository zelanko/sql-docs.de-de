---
title: MSSQLSERVER_21899 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c8e25f71f23742de35dcc8c9629181dd20af2f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667268"
---
# <a name="mssqlserver21899"></a>MSSQLSERVER_21899
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
**sp_validate_redirected_publisher** fragt die Abonnement-Metadatentabellen von der Verlegerdatenbank beim Remoteserver ab, um seine zugeordneten Abonnenten zu bestimmen. Fehler 21899 wird zurückgegeben, wenn diese Abfrage fehlschlägt. Die Überprüfungsabfrage erfordert Zugriff auf die veröffentlichte Datenbank beim umgeleiteten Verleger. Wenn die Anmeldung, die beim Aufruf von **sp_adddistpublisher** für den ursprünglichen Verleger angegeben wurde, nicht berechtigt ist, beim umgeleiteten Verleger auf die veröffentlichte Datenbank zuzugreifen, wird der Fehler 21899 zurückgegeben.  
  
## <a name="user-action"></a>Benutzeraktion  
Überprüfen Sie die erwähnte Fehlermeldung, um die Fehlerursache zu bestimmen und entsprechende Korrekturmaßnahmen zu ergreifen  
  
