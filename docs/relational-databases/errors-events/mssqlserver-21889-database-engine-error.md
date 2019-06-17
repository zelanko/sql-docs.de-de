---
title: MSSQLSERVER_21889 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 635205cbc92121034cd8c949382c4910c794b55e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045827"
---
# <a name="mssqlserver21889"></a>MSSQLSERVER_21889
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21889|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21889|  
|Meldungstext|Die SQL Server-Instanz „%s“ ist kein Replikationsverleger. Führen Sie **sp_adddistributor** auf der SQL Server-Instanz „%s“ mit dem Verteiler „%s“ aus, um die Instanz als Host der Veröffentlichungsdatenbank „%s“ zu aktivieren. Stellen Sie sicher, dass Sie die gleiche Anmeldung und das gleiche Kennwort angeben, die für den ursprünglichen Verleger verwendet worden sind.|  
  
## <a name="explanation"></a>Erklärung  
Um die Verlegerdatenbank hosten zu können, muss die Instanz von SQL Server ein Replikationsverleger sein. **sp_validate_redirected_publisher** ruft **sp_helpdistributor** auf dem Remoteserver auf, um zu bestimmen, ob es sich beim Server um einen Replikationsverleger handelt. Dieser Fehler weist darauf hin, dass die Zielinstanz von SQL Server kein Replikationsverleger ist.  
  
## <a name="user-action"></a>Benutzeraktion  
Führen Sie **sp_adddistributor** bei der Instanz von SQL Server aus, die als Host der Verlegerdatenbank fungiert. Wenn Sie **sp_adddistributor** ausführen, geben Sie den richtigen Verteiler an. Verwenden Sie den Wert für den *@password* -Parameter, der verwendet wurde, als **sp_adddistributor** zum ersten Mal beim Verteiler ausgeführt wurde.  
  
