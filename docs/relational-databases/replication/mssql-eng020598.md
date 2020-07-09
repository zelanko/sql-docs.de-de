---
title: MSSQL_ENG020598 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 966d4ed9d77200c85146400aa2c7d8b0b5e462fa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85721684"
---
# <a name="mssql_eng020598"></a>MSSQL_ENG020598
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|20598|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Die Zeile wurde bei der Anwendung des replizierten Befehls auf dem Abonnenten nicht gefunden.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler wird bei der Transaktionsreplikation ausgegeben, wenn der Verteilungs-Agent versucht, eine Zeile auf dem Abonnenten zu aktualisieren, die Zeile jedoch gelöscht bzw. der Primärschlüssel geändert wurde. Standardmäßig sollten Abonnenten von Transaktionsreplikationen schreibgeschützt sein, da Änderungen nicht an den Verleger zurückgegeben werden. Bei der Transaktionsreplikation sollten Benutzeränderungen nur am Abonnenten vorgenommen werden, wenn aktualisierbare Abonnements oder Peer-zu-Peer-Replikationen verwendet werden. Informationen zu diesen Optionen finden Sie unter [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md) und [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 **So lösen Sie dieses Problem**  
  
1.  Wenn die Replikation fortgesetzt werden muss, während Sie den Ursprung des Fehlers ermitteln, geben Sie den Parameter **-SkipErrors 20598** für den Verteilungs-Agent an. Hierdurch kann der Agent Änderungen auslassen, die den Fehler 20598 verursachen, und dennoch zulassen, dass andere Änderungen repliziert werden.  
  
2.  Stellen Sie fest, welche Zeilen auf dem Abonnenten gelöscht wurden bzw. einen anderen Primärschlüssel aufweisen als die Zeilen auf dem Verleger. Verwenden Sie [tablediff Utility](../../tools/tablediff-utility.md) , um zu ermitteln, welche Zeilen sich in den Veröffentlichungs- und Abonnementdatenbanken unterscheiden. Informationen zum Verwenden dieses Hilfsprogramms finden Sie unter [Überprüfen replizierter Tabellen auf Unterschiede &#40;Replikationsprogrammierung&#41;](../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
3.  Verbessern Sie die Zeilen auf dem Abonnenten mithilfe des Hilfsprogramms **tablediff** oder einer anderen Methode.  
  
4.  (Optional) Entfernen Sie den Parameter **-SkipErrors** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
