---
title: Ausführen von Skripts vor und nach dem Anwenden einer Momentaufnahme (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], scripts
- scripts [SQL Server replication], snapshots
- snapshot replication [SQL Server], scripts
ms.assetid: b7bb1e4c-5b48-4bb1-9dc8-47c911f2cc82
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b5fdb23fc81a4025ded4bf02a56df06014d4ca3d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155950"
---
# <a name="execute-scripts-before-and-after-a-snapshot-is-applied-sql-server-management-studio"></a>Ausführen von Skripts vor und nach dem Anwenden einer Momentaufnahme (SQL Server Management Studio)
  Geben Sie auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** ein optionales Skript an, das vor oder nach dem Anwenden der Momentaufnahme ausgeführt wird. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
> [!NOTE]  
>  Diese Optionen sind nicht verfügbar, wenn für **Momentaufnahmeformat** die Option **Zeichen**festgelegt ist.  
  
### <a name="to-execute-a-script-before-or-after-a-snapshot-is-applied"></a>So führen Sie ein Skript vor und nach dem Anwenden einer Momentaufnahme aus  
  
1.  Gehen Sie auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** wie folgt vor:  
  
    -   Wenn Sie ein Skript angeben möchten, das vor dem Anwenden der Momentaufnahme ausgeführt werden soll, klicken Sie auf **Durchsuchen** , um zum entsprechenden Skript zu navigieren, oder geben Sie im Textfeld **Dieses Skript vor Anwenden der Momentaufnahme ausführen** den Pfad zum gewünschten Skript ein.  
  
        > [!NOTE]  
        >  Der Verteilungs-Agent bzw. Merge-Agent muss für das von Ihnen angegebene Verzeichnis Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\computername\scripts\myscript.sql.  
  
    -   Wenn Sie ein Skript angeben möchten, das nach dem Anwenden der Momentaufnahme ausgeführt werden soll, klicken Sie auf **Durchsuchen** , um zum entsprechenden Skript zu navigieren, oder geben Sie im Textfeld **Dieses Skript nach Anwenden der Momentaufnahme ausführen** den UNC-Pfad zum gewünschten Skript ein.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Momentaufnahmeeigenschaften &#40;Replikationsprogrammierung mit Transact-SQL&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](publish/change-publication-and-article-properties.md)   
 [Ausführen von Skripts vor und nach dem Anwenden der Momentaufnahme](execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](initialize-a-subscription-with-a-snapshot.md)  
  
  
