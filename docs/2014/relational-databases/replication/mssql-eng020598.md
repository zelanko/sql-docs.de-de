---
title: MSSQL_ENG020598 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ae79a5e4eb05b9933289e7e3ee5a0cb6cda7cf89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152530"
---
# <a name="mssqleng020598"></a>MSSQL_ENG020598
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|20598|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Die Zeile wurde bei der Anwendung des replizierten Befehls auf dem Abonnenten nicht gefunden.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler wird bei der Transaktionsreplikation ausgegeben, wenn der Verteilungs-Agent versucht, eine Zeile auf dem Abonnenten zu aktualisieren, die Zeile jedoch gelöscht bzw. der Primärschlüssel geändert wurde. Standardmäßig sollten Abonnenten von Transaktionsreplikationen schreibgeschützt sein, da Änderungen nicht an den Verleger zurückgegeben werden. Bei der Transaktionsreplikation sollten Benutzeränderungen nur am Abonnenten vorgenommen werden, wenn aktualisierbare Abonnements oder Peer-zu-Peer-Replikationen verwendet werden. Informationen zu diesen Optionen finden Sie unter [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) und [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 **So lösen Sie dieses Problem**  
  
1.  Wenn die Replikation fortgesetzt werden muss, während Sie den Ursprung des Fehlers ermitteln, geben Sie den Parameter **-SkipErrors 20598** für den Verteilungs-Agent an. Hierdurch kann der Agent Änderungen auslassen, die den Fehler 20598 verursachen, und dennoch zulassen, dass andere Änderungen repliziert werden.  
  
2.  Stellen Sie fest, welche Zeilen auf dem Abonnenten gelöscht wurden bzw. einen anderen Primärschlüssel aufweisen als die Zeilen auf dem Verleger. Verwenden Sie [tablediff Utility](../../tools/tablediff-utility.md) , um zu ermitteln, welche Zeilen sich in den Veröffentlichungs- und Abonnementdatenbanken unterscheiden. Informationen zum Verwenden dieses Hilfsprogramms finden Sie unter [Überprüfen replizierter Tabellen auf Unterschiede &#40;Replikationsprogrammierung&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
3.  Verbessern Sie die Zeilen auf dem Abonnenten mithilfe des Hilfsprogramms **tablediff** oder einer anderen Methode.  
  
4.  (Optional) Entfernen Sie den Parameter **-SkipErrors** .  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
