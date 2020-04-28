---
title: Topologie konfigurieren (Peer-zu-Peer-Replikation) | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.peers.f1
ms.assetid: 5377c59f-2e25-4852-a306-c87ae3dca9fd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5c41bc845e7b02959f25aa8282452db64f819558
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176570"
---
# <a name="configure-topology-peer-to-peer-replication"></a>Topologie konfigurieren (Peer-zu-Peer-Replikation)
  Auf der Seite **Topologie konfigurieren** können Sie allgemeine Konfigurationsaufgaben ausführen, z. B. neue Knoten hinzufügen, Knoten löschen und neue Verbindungen zwischen vorhandenen Knoten hinzufügen. Auf der Entwurfsoberfläche wird der Knoten angezeigt, den Sie auf der Seite **Veröffentlichung** des Assistenten ausgewählt haben. Zum Angeben von Konfigurationsoptionen klicken Sie mit der rechten Maustaste auf einen Knoten, eine Verbindung oder die Entwurfsoberfläche.

> [!NOTE]
>  Der Assistent zum Konfigurieren der Peer-zu-Peer-Topologie fordert Topologieinformationen an, wenn der Assistent geschlossen wird. Wenn der Assistent geschlossen und erneut geöffnet wird, bevor alle Knoten auf die Anforderung von Informationen reagiert haben, zeigt der Assistent möglicherweise ein Teilnetzwerk an.

## <a name="options"></a>Tastatur
 Die Seite **Topologie konfigurieren** enthält Oberflächenelemente und Optionen, die verfügbar sind, wenn Sie mit der rechten Maustaste auf ein Element klicken. In der folgenden Tabelle werden die einzelnen Oberflächenelemente beschrieben.

|Oberflächenelement|BESCHREIBUNG|
|-----------------------|-----------------|
|Entwurfsoberfläche|Zeigt andere Oberflächenelemente an. Zum Hinzufügen von Elementen klicken Sie mit der rechten Maustaste auf die Entwurfsoberfläche.|
|![Der erste Knoten einer Topologie](media/p2pwizard-firstnode.gif "Der erste Knoten einer Topologie")|Der ursprüngliche Knoten in der Topologie. Neue Knoten werden mit einer Kopie der Veröffentlichungsdatenbank vom ursprünglichen Knoten initialisiert.|
|![Ein Knoten, für den wir vollständige Informationen](media/p2pwizard-complete.gif "Ein Knoten, für den vollständige Informationen vorhanden sind") oder eine höhere Version haben, für die die Replikation über vollständige Informationen verfügt. Zum Angeben von Konfigurationsoptionen klicken Sie mit der rechten Maustaste auf den Knoten.|
|![Ein Knoten, für den unvollständige Informationen vorhanden sind](media/p2pwizard-incomplete.gif "Ein Knoten, für den unvollständige Informationen vorhanden sind")|Ein Knoten, für den unvollständige Informationen für die Replikation vorhanden sind. Zum Angeben von Konfigurationsoptionen klicken Sie mit der rechten Maustaste auf den Knoten. Die Informationen für die Replikation können aus einem der folgenden Gründe unvollständig sein:<br /><br /> Auf dem Knoten wird eine Instanz von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ausgeführt, von der nicht alle für den Assistenten erforderlichen Metadaten gespeichert werden.<br /><br /> Auf dem Knoten wird eine höhere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt, aber die Replikation kann keine Abonnementinformationen von dem Knoten abrufen. So beheben Sie dieses Problem:<br />-Stellen Sie sicher, dass die Datenbank auf dem Knoten online ist und Sie eine Verbindung mit der Datenbank herstellen können, indem Sie dieselben Anmelde Informationen verwenden wie die Verteilungs-Agents, die eine Verbindung mit dem Knoten herstellen.<br />-Stellen Sie sicher, dass die Protokolllese-Agent und alle Verteilungs-Agents, die eine Verbindung mit dem Knoten herstellen, ausgeführt werden.<br />-Stellen Sie sicher, dass das Aktualisierungs Timeout hoch genug festgelegt ist, um alle Topologieinformationen zu erfassen. Klicken Sie zum Festlegen des Timeouts mit der rechten Maustaste auf die Entwurfsoberfläche, und klicken Sie dann auf **Aktualisierungstimeout festlegen**.|
|Graue Linie mit Pfeilen|Die Verbindung zwischen zwei Knoten. Klicken Sie zum Hinzufügen einer Verbindung mit der rechten Maustaste auf einen der Knoten, die Sie verbinden möchten. Zum Entfernen einer Verbindung klicken Sie mit der rechten Maustaste auf diese Verbindung.<br /><br /> Wenn die Linie nur einen Pfeil aufweist, sind für einen der Knoten unvollständige Informationen für die Replikation vorhanden.|

### <a name="options-for-the-design-surface"></a>Optionen für die Entwurfsoberfläche
 **Diagramm neu zeichnen** Zeichnet die Objekte auf der Entwurfsoberfläche neu, ohne die Topologie zu aktualisieren. Durch das Neuzeichnen erhalten Sie möglicherweise eine bessere Ansicht der Topologie.

 **Topologie aktualisieren** Fragt jeden Knoten in der Topologie ab und zeigt aktualisierte Informationen zu jedem Knoten an. Bei zahlreichen Knoten kann dieser Vorgang mehrere Minuten dauern.

 Wenn der Assistent Topologieinformationen anfordert und Sie den Assistenten dann schließen und erneut öffnen, bevor alle Knoten auf die Anforderung reagiert haben, werden auf dieser Seite möglicherweise nicht alle Knoten in der Topologie angezeigt.

 **Neuen Peer Knoten hinzufügen** Fügen Sie der Peer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -zu-Peer-Topologie eine Instanz von hinzu. Wenn Sie eine Instanz als Knoten hinzufügen, wird nach Abschluss des Assistenten auf dieser Instanz eine Veröffentlichung erstellt. Klicken Sie nach dem Hinzufügen des Knotens mit der rechten Maustaste auf diesen Knoten, um eine Verbindung zwischen dem neuen und einem vorhandenen Knoten hinzuzufügen.

 Für die Verwendung in einer Peer-zu-Peer-Topologie muss die Instanz die folgenden Anforderungen erfüllen:

-   Sie muss bereits als Verteiler konfiguriert oder einem Remoteverteiler zugeordnet worden sein.

-   Sie muss eine Kopie der in die Replikation involvierten Datenbank enthalten. Bei dieser Kopie handelt es sich i. d. R. um eine wiederhergestellte Sicherung der ursprünglichen Veröffentlichungsdatenbank.

 **Knoten zum Anzeigen auswählen** Wählen Sie die Knoten aus, die auf der Entwurfs Oberfläche angezeigt werden sollen. Diese Option ist nützlich, wenn die Topologie eine große Anzahl von Knoten enthält. Beachten Sie, dass Sie Verbindungen nur zwischen Knoten hinzufügen können, die auf der Entwurfsoberfläche sichtbar sind.

 **Aktualisierungstimeout festlegen** Geben Sie an, wie lange der Aktualisierungsvorgang ausgeführt werden kann, bevor ein Timeout eintritt.

### <a name="options-for-each-node"></a>Optionen für einzelne Knoten
 **Neue Peerverbindung hinzufügen** Fügen Sie eine Verbindung zwischen zwei Knoten hinzu. Wenn Sie z. B. eine Verbindung zwischen Knoten A und Knoten B hinzufügen, werden bei der Replikation zwei Abonnements hinzugefügt. Durch das erste Abonnement wird Knoten A in die Lage versetzt, Änderungen der Veröffentlichung auf Knoten B zu empfangen, während durch das zweite Abonnement Knoten B in die Lage versetzt wird, Änderungen der Veröffentlichung auf Knoten A zu empfangen.

 **Peerknoten löschen** Entfernt einen Knoten aus der Topologie. Wenn Sie z. B. Knoten C entfernen, wird die Veröffentlichung auf diesem Knoten entfernt. Abonnements zwischen Knoten A und Knoten C sowie zwischen Knoten B und Knoten C werden ebenfalls entfernt. Die Datenbank auf Knoten C wird nicht gelöscht, und Veröffentlichung und Verteilung werden nicht deaktiviert.

> [!NOTE]
>  Wenn Sie Peer-zu-Peer-Replikation konfigurieren, geben Sie eine ID für jeden Knoten an. Diese ID muss für alle Knoten in der Topologie eindeutig sein und wird in der Spalte originator_id der Systemtabelle [MSpeer_originatorid_history](/sql/relational-databases/system-tables/mspeer-originatorid-history-transact-sql) gespeichert. Wenn ein Knoten aus der Topologie entfernt wird, wird die ID weiterhin in der Verlaufstabelle beibehalten. Die ID wird beibehalten, um FALSE-Konflikte zu vermeiden, wenn Änderungen am entfernten Knoten weiterhin topologieübergreifend repliziert werden. Wenn Sie die ID für einen neuen Knoten wiederverwenden möchten, müssen Sie die ID endgültig aus der Tabelle MSpeer_originatorid_history für alle Knoten löschen. Bevor Sie eine ID für einen Knoten löschen, führen Sie [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) aus, um zu überprüfen, ob alle Änderungen, die vom Knoten stammen, repliziert wurden.

 **Mit ALLEN angezeigten Knoten verbinden** Fügt Verbindungen zwischen dem ausgewählten Knoten und allen anderen Knoten hinzu. Wenn Sie z. B. diese Option für Knoten C in einer drei Knoten umfassenden Topologie auswählen, werden bei der Replikation vier Abonnements hinzugefügt, und zwar zwei, mit denen Knoten A und Knoten B in die Lage versetzt werden, Änderungen der Veröffentlichung auf Knoten C zu empfangen, und zwei, mit denen Knoten C in die Lage versetzt wird, Änderungen der Veröffentlichungen auf Knoten A und Knoten B zu empfangen.

 **Knoten zum Anzeigen auswählen** Wählen Sie die Knoten aus, die auf der Entwurfs Oberfläche angezeigt werden sollen. Diese Option ist nützlich, wenn die Topologie eine große Anzahl von Knoten enthält. Beachten Sie, dass Sie Verbindungen nur zwischen Knoten hinzufügen können, die auf der Entwurfsoberfläche sichtbar sind.

### <a name="options-for-the-connection-arrows"></a>Optionen für die Verbindungspfeile
 **Peerverbindung entfernen** Entfernt eine Verbindung zwischen zwei Knoten. Wenn Sie z. B. eine Verbindung zwischen Knoten A und Knoten B entfernen, werden bei der Replikation zwei Abonnements gelöscht, und zwar das Abonnement, das Knoten A in die Lage versetzt, Änderungen der Veröffentlichung auf Knoten B zu empfangen, und das Abonnement, das Knoten B in die Lage versetzt, Änderungen der Veröffentlichung auf Knoten A zu empfangen.

## <a name="see-also"></a>Weitere Informationen
 [Konfigurieren der Veröffentlichung und der Verteilung](configure-publishing-and-distribution.md) [Verwalten einer Peer-zu-Peer-Topologie &#40;Replikations Programmierung mit Transact-SQL&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) [Peer-zu-Peer-Transaktions Replikation](transactional/peer-to-peer-transactional-replication.md)


