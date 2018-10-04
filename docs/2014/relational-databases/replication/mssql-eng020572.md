---
title: MSSQL_ENG020572 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020572 error
ms.assetid: 636566db-ffcf-4109-8c11-15b8c7cb9cd9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f296fab429acc1b5fa9887a88553895a46bc93d8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218252"
---
# <a name="mssqleng020572"></a>MSSQL_ENG020572
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|20572|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Das Abonnement des Abonnenten '%s' für den '%s'-Artikel in der '%s'-Veröffentlichung wurde nach einem Datenüberprüfungsfehler neu initialisiert.|  
  
## <a name="explanation"></a>Erklärung  
 Die Daten des Abonnenten wurden gegen die Daten des Verlegers abgeglichen, und es wurde keine Übereinstimmung der Daten festgestellt. Daher konnte die Überprüfung nicht erfolgreich abgeschlossen werden. Bei der Angabe zur Ausführung einer Überprüfung haben Sie die Option aktiviert, dass im Falle eines Fehlers bei der Überprüfung eine erneute Initialisierung des Abonnements erfolgen soll. Für eine erneute Initialisierung des Abonnements muss eine neue Momentaufnahme auf dem Abonnenten angewendet werden. Weitere Informationen zur Überprüfung finden Sie unter [Validate Replicated Data](validate-replicated-data.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 Die Daten auf dem Verleger und auf dem Abonnenten stimmen überein, nachdem die neue Momentaufnahme auf dem Abonnenten angewendet wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
