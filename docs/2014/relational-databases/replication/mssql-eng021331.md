---
title: MSSQL_ENG021331 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021331 error
ms.assetid: 9acd75d9-fda1-44cd-ba17-20295ad53ea0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 94d898e666c0182a9e323000d78e5a06bce3d1ae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175440"
---
# <a name="mssqleng021331"></a>MSSQL_ENG021331
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21331|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Fehler beim Kopieren der Benutzerskriptdatei auf den Verteiler. (%1!s!)|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler kann auftreten, wenn ein Abonnement manuell initialisiert wird und die Skripts, die durch die Replikation generiert oder in einem Replikationsbefehl angegeben werden, nicht in das angegebene Verzeichnis kopiert werden können. Ursache für den Fehler kann ein Problem mit den Berechtigungen sein: Wenn ein Abonnement ohne Verwendung einer Momentaufnahme initialisiert wird, muss das Konto, über dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst auf dem Verleger ausgeführt wird, Schreibberechtigungen für den Momentaufnahmeordner auf dem Verleger besitzen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie sicher, dass der richtige Pfad für den Momentaufnahmeordner angegeben wird und dass das Konto, über das der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst auf dem Verleger ausgeführt wird, über ausreichende Berechtigungen verfügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Specify the Default Snapshot Location &#40;SQL Server Management Studio&#41; (Angeben des standardmäßigen Momentaufnahmespeicherorts &#40;SQL Server Management Studio&#41;)](specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)   
 [Initialisieren eines Transaktionsabonnements ohne Momentaufnahme](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
