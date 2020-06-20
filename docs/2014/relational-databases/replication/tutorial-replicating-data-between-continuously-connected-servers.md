---
title: 'Tutorial: Replizieren von Daten zwischen Servern mit kontinuierlicher Verbindung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c63e48d4c5f5bfad6fe50155cd7fd7a088c2178
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047615"
---
# <a name="tutorial-replicating-data-between-continuously-connected-servers"></a>Lernprogramm: Replizieren von Daten zwischen Servern mit kontinuierlicher Verbindung
  Die Replikation stellt eine bewährte Lösung für das Problem des Verschiebens von Daten zwischen Servern mit kontinuierlicher Verbindung dar. Mithilfe von Replikations-Assistenten können Sie eine Replikationstopologie auf einfache Weise konfigurieren und verwalten. In diesem Lernprogramm wird die Konfiguration einer Replikationstopologie für Server mit kontinuierlicher Verbindung erläutert.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm erfahren Sie, wie Sie Daten aus einer Datenbank mithilfe der Transaktionsreplikation in einer anderen Datenbank veröffentlichen. In der ersten Lektion wird die Verwendung von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zum Erstellen einer Veröffentlichung erläutert. In den darauf folgenden Lektionen wird erläutert, wie Sie ein Abonnement erstellen und überprüfen und wie Sie die Latenzzeit messen.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Dieses Lernprogramm ist für Benutzer vorgesehen, die mit grundlegenden Datenbankvorgängen vertraut sind, aber nur über begrenzte Kenntnisse in Bezug auf die Replikation verfügen. Für dieses Lernprogramm ist es erforderlich, dass Sie das vorherige Lernprogramm ( [Vorbereiten des Servers für die Replikation](tutorial-preparing-the-server-for-replication.md)) abgeschlossen haben.  
  
 Auf Ihrem System müssen für die Verwendung dieses Lernprogramms folgende Komponenten installiert sein:  
  
-   Auf dem Verlegerserver (Quelle):  
  
    -   Eine beliebige Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit Ausnahme von Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) und [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Diese Editionen können nicht als Verleger für Replikationen verwendet werden.  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] -Beispieldatenbank Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert.  
  
-   Abonnentenserver (Ziel):  
  
    -   Eine beliebige Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit Ausnahme von [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] kann nicht als Abonnent einer Transaktionsreplikation fungieren.  
  
    > [!NOTE]  
    >  Die Replikation wird in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] nicht standardmäßig installiert.  
  
> [!NOTE]  
>  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] müssen Sie eine Verbindung mit dem Verleger und dem Abonnenten herstellen, indem Sie einen Anmelde Namen verwenden, der Mitglied der festen Server Rolle **sysadmin** ist.  
  
 **Geschätzte Zeit bis zum Abschluss dieses Tutorials: 30 Minuten.**  
  
## <a name="lessons-in-this-tutorial"></a>Lektionen in diesem Lernprogramm  
  
-   [Lektion 1: Veröffentlichen von Daten mithilfe der Transaktionsreplikation](lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [Lektion 2: Erstellen eines Abonnements für die Transaktionsveröffentlichung](lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [Lektion 3: Überprüfen des Abonnements und Messen der Latenzzeit](lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
 [Lernprogramm starten](transactional/transactional-replication.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte für die Replikationsprogrammierung](concepts/replication-programming-concepts.md)  
  
  
