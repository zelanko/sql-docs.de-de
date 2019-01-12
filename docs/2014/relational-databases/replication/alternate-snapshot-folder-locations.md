---
title: Alternative Speicherorte für Momentaufnahmeordner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c86e79928bdadb129ed0aa591e4bd035ffe22c1c
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54129000"
---
# <a name="alternate-snapshot-folder-locations"></a>Alternative Speicherorte für Momentaufnahmeordner
  Alternative Momentaufnahmespeicherorte ermöglichen Ihnen das Speichern von Momentaufnahmedateien an einem anderen Speicherort oder zusätzlich zum Standardspeicherort, der sich normalerweise auf dem Verteiler befindet. Alternative Speicherorte können sich auf einem anderen Server, in einem Netzlaufwerk oder auf Wechselmedien befinden, z. B. CD-ROMs oder Wechseldatenträgern.  
  
 Alternative Momentaufnahmespeicherorte werden als Eigenschaft der Veröffentlichung gespeichert. Da der alternative Momentaufnahmespeicherort eine Veröffentlichungseigenschaft ist, sind der Verteilungs-Agent und der Merge-Agent in der Lage, die ordnungsgemäße Momentaufnahme als Teil des Synchronisierungsprozesses zu finden.  
  
 Wenn Sie einen alternativen Speicherort für Momentaufnahmeordner angeben oder Momentaufnahmedateien komprimieren möchten, erstellen Sie die Veröffentlichung, ohne die AnfangsMomentaufnahme sofort zu erstellen, legen Sie die Veröffentlichungseigenschaften für den Momentaufnahmespeicherort fest, und führen Sie dann den Momentaufnahme-Agent für diese Veröffentlichung aus. Wenn Sie den alternativen Speicherort nach der Erstellung der Anfangsmomentaufnahme ändern, wird keiner der für die Veröffentlichung generierten Momentaufnahmen an den alternativen Speicherort verschoben. In diesem Fall ist der Merge-Agent bzw. Verteilungs-Agent möglicherweise nicht in der Lage, die Momentaufnahmedateien an dem neuen alternativen Speicherort ausfindig zu machen.  
  
> [!NOTE]  
>  Geben Sie keinen alternativen Speicherort (mithilfe des Dialogfelds **Veröffentlichungseigenschaften** oder [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)) an, der der gleiche ist wie der Standardspeicherort für Momentaufnahmen.  
  
> [!CAUTION]  
>  Verwenden Sie WebSync und alternative Ordnerspeicherorte für Momentaufnahmen nicht gleichzeitig.  
  
 **So geben Sie alternative Momentaufnahmespeicherorte an**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Angeben eines Speicherortes für den alternativen Momentaufnahmespeicherort](snapshot-options.md#snapshot-folder-locations) 
  
-   Replikationsprogrammierung mit [!INCLUDE[tsql](../../includes/tsql-md.md)]: [Konfigurieren von Momentaufnahmeeigenschaften &#40;Replikationsprogrammierung mit Transact-SQL&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Initialisieren eines Abonnements mit einer Momentaufnahme](initialize-a-subscription-with-a-snapshot.md)   
 [Momentaufnahmeoptionen](snapshot-options.md)  
  
  
