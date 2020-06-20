---
title: MSSQL_ENG021331 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021331 error
ms.assetid: 9acd75d9-fda1-44cd-ba17-20295ad53ea0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b595cf760fb0a01e2f9aeebf788355aa328de873
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065810"
---
# <a name="mssql_eng021331"></a>MSSQL_ENG021331
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21331|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Fehler beim Kopieren der Benutzerskriptdatei auf den Verteiler. (%1!s!)|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler kann auftreten, wenn ein Abonnement manuell initialisiert wird und die Skripts, die durch die Replikation generiert oder in einem Replikationsbefehl angegeben werden, nicht in das angegebene Verzeichnis kopiert werden können. Ursache für den Fehler kann ein Problem mit den Berechtigungen sein: Wenn ein Abonnement ohne Verwendung einer Momentaufnahme initialisiert wird, muss das Konto, über dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst auf dem Verleger ausgeführt wird, Schreibberechtigungen für den Momentaufnahmeordner auf dem Verleger besitzen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie sicher, dass der richtige Pfad für den Momentaufnahmeordner angegeben wird und dass das Konto, über das der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst auf dem Verleger ausgeführt wird, über ausreichende Berechtigungen verfügt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben des standardmäßigen Momentaufnahme Speicher Orts](snapshot-options.md#snapshot-folder-locations)   
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)   
 [Initialisieren eines Transaktionsabonnements ohne Momentaufnahme](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
