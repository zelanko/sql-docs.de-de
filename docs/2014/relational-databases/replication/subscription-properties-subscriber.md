---
title: Eigenschaften des SQL Server-Replikation-Abonnements-Abonnent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subproperties.subscriber.f1
- sql12.rep.newsubwizard.subproperties.publisher.f1
helpviewer_keywords:
- Subscription Properties dialog box
ms.assetid: bef66929-3234-4a45-8ec4-3b271519d07a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: af9cb7612837021b156fb8f467899f0e23ef1555
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250268"
---
# <a name="sql-server-replication-subscription-properties"></a>Eigenschaften des SQL Server-Replikation Abonnements 
Dieser Abschnitt enthält Informationen zum Dialogfeld **Abonnement Eigenschaften** . 

## <a name="publisher-properties"></a>Verlegereigenschaften 
  Im Dialogfeld **Abonnementeigenschaften** des Verlegers können Sie die Eigenschaften von Pushabonnements anzeigen und festlegen. Sie können auch bestimmte Eigenschaften von Pullabonnements anzeigen. Die übrigen Eigenschaften sind jedoch nur über das Dialogfeld **Abonnementeigenschaften** des Abonnenten verfügbar und können auch nur dort geändert werden.  
  
 Zu jeder im Dialogfeld **Abonnementeigenschaften** verfügbaren Eigenschaft wird auch eine Beschreibung angezeigt. Klicken Sie auf eine Eigenschaft, um die dazugehörige Beschreibung am unteren Rand des Dialogfelds anzuzeigen. In diesem Thema werden zusätzliche Informationen zu einer Reihe von Eigenschaften bereitgestellt. Die meisten dieser Eigenschaften sind auf dem Verleger nur für Pushabonnements verfügbar. Die Eigenschaften sind in folgenden Kategorien angeordnet:  
  
-   Eigenschaften, die für alle Abonnements gelten.    
-   Eigenschaften, die für Transaktionsabonnements gelten.    
-   Eigenschaften, die für Mergeabonnements gelten.  
  
 Schreibgeschützte Optionen können nur beim Erstellen des Abonnements festgelegt werden. Wenn Sie Optionen festlegen möchten, die nicht im Assistenten für neue Abonnements verfügbar sind, müssen Sie das Abonnement mithilfe von gespeicherten Prozeduren erstellen. Weitere Informationen finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md) und [Create a Push Subscription](create-a-push-subscription.md).  

  
### <a name="options-for-all-subscriptions"></a>Optionen für alle Abonnements  
 **Sicherheit**  
 Klicken Sie in der Zeile **Agentprozesskonto** auf die **Schaltfläche mit den drei Punkten**, um das Konto zu ändern, unter dem Verteilungs-Agent oder Merge-Agent auf dem Verteiler ausgeführt werden. Wenn Sie das Konto ändern möchten, unter dem Verteilungs-Agent oder Merge-Agent eine Verbindung mit dem Abonnenten herstellen, klicken Sie auf **Abonnentenverbindung**, und klicken Sie dann auf die **Schaltfläche mit den drei Punkten**.  
  
 Weitere Informationen zu den für die einzelnen Agents erforderlichen Berechtigungen finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
### <a name="publisher-options-for-transactional-subscriptions"></a>Verlegeroptionen für Transaktionsabonnements  
 **Transaktions Schleifen verhindern**  
 Legt fest, ob der Verteilungs-Agent Transaktionen des Abonnenten zurück an den Abonnenten sendet. Diese Option wird bei der bidirektionalen Transaktionsreplikation verwendet. Weitere Informationen finden Sie unter [bidirektionale Transaktions Replikation](transactional/bidirectional-transactional-replication.md).  
  
 **Aktualisier bares Abonnement**  
 Legt fest, ob die am Abonnenten vorgenommenen Änderungen zurück auf den Verleger repliziert werden. Änderungen können entweder mit einem sofortigen Update oder mit einem verzögerten Update über eine Warteschlange repliziert werden. Mit der Option **Updatemethode für Abonnent** wird die zu verwendende Methode festgelegt. Weitere Informationen finden Sie unter [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md).  
  
### <a name="options-for-merge-subscriptions"></a>Optionen für Mergeabonnements  
 **Partitions Definition (HOST_NAME)**  
 Wenn Sie eine Mergereplikation für eine Veröffentlichung mit parametrisierten Filtern ausführen, wird bei der Synchronisierung eine der beiden Systemfunktionen, **SUSER_SNAME()** oder **HOST_NAME()**(oder beide, sofern die Filter auf beide Funktionen verweisen) ausgewertet, um festzulegen, welche Daten der Abonnent empfangen soll. 
  **HOST_NAME()** gibt standardmäßig den Namen des Computers zurück, auf dem der Merge-Agent ausgeführt wird. Sie können diesen Wert jedoch im Assistenten für neue Abonnements überschreiben. Weitere Informationen zu parametrisierten Filtern und zum Überschreiben von **HOST_NAME()** finden Sie unter [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
 **Abonnementtyp** und **Priorität**  
 Zeigt an, ob es sich bei dem Abonnement um ein Client- oder Serverabonnement handelt (kann nach Erstellen des Abonnements nicht mehr geändert werden). Bei Serverabonnements können Daten erneut für andere Abonnenten veröffentlicht und eine Priorität für die Konfliktlösung festgelegt werden.  
  
 Wenn Sie im Assistenten für neue Abonnements als Abonnementtyp Server ausgewählt haben, wird dem Abonnenten eine Priorität für die Konfliktlösung zugewiesen.  
  
 **Konflikte interaktiv lösen**  
 Legt fest, ob die bei der Synchronisierung auftretenden Konflikte mit der Benutzeroberfläche des interaktiven Konfliktlösers gelöst werden sollen. Dafür ist für **Synchronisierungsverwaltung von Windows verwenden** der Wert **Aktivieren**erforderlich. Weitere Informationen finden Sie unter [Interactive Conflict Resolution](merge/advanced-merge-replication-conflict-interactive-resolution.md).  


## <a name="subscriber-properties"></a>Abonnenteneigenschaften
  Im Dialogfeld **Abonnement Eigenschaften** des Abonnenten können Sie die Eigenschaften für Pullabonnements anzeigen und festlegen.  
  
 Zu jeder im Dialogfeld **Abonnementeigenschaften** verfügbaren Eigenschaft wird auch eine Beschreibung angezeigt. Klicken Sie auf eine Eigenschaft, um die dazugehörige Beschreibung am unteren Rand des Dialogfelds anzuzeigen. Dieses Thema enthält zusätzliche Informationen zu verschiedenen Eigenschaften. Die Eigenschaften sind in folgenden Kategorien angeordnet:  
  
-   Eigenschaften, die für alle Abonnements gelten.    
-   Eigenschaften, die für Transaktionsabonnements gelten.   
-   Eigenschaften, die für Mergeabonnements gelten.  
  
 Schreibgeschützte Optionen können nur beim Erstellen des Abonnements festgelegt werden. Wenn Sie Optionen festlegen möchten, die nicht im Assistenten für neue Abonnements verfügbar sind, müssen Sie das Abonnement mithilfe von gespeicherten Prozeduren erstellen. Weitere Informationen finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md) und [Create a Push Subscription](create-a-push-subscription.md).  
  
> [!NOTE]  
>  Wenn für das Abonnement bislang noch kein Auftrag für den Verteilungs-Agent oder den Merge-Agent erstellt wurde, werden viele Abonnementeigenschaften nicht angezeigt. Um einen Agentauftrag für ein Pullabonnement zu erstellen, führen Sie [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) (für ein Abonnement einer Momentaufnahme- oder Transaktionsveröffentlichung) oder [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql) aus (für ein Abonnement einer Mergeveröffentlichung).  
  
### <a name="options-for-all-subscriptions"></a>Optionen für alle Abonnements  
 **Veröffentlichte Daten aus einer Momentaufnahme initialisieren**  
 Bestimmt, ob Abonnements mit einer Momentaufnahme (Standard) oder mithilfe einer anderen Methode initialisiert werden. Weitere Informationen zum Initialisieren von Abonnements finden Sie unter [Initialisieren eines Abonnements](initialize-a-subscription.md).  
  
 **Momentaufnahme Speicherort**  
 Bestimmt den Speicherort, von dem aus während der Initialisierung oder der erneuten Initialisierung auf Momentaufnahmedateien zugegriffen wird. Für den Speicherort sind folgende Werte möglich:  
  
-   **Standard Speicherort**: der Standard Speicherort, der beim Konfigurieren eines Verteilers definiert wird. Weitere Informationen finden Sie [unter Angeben des standardmäßigen Momentaufnahme Speicher Orts](snapshot-options.md#snapshot-folder-locations).    
-   **Alternativer Ordner**: ein alternativer Speicherort, der im Dialogfeld **Veröffentlichungs Eigenschaften** angegeben werden kann. Weitere Informationen finden Sie unter [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md).    
-   **Ordner für dynamische Momentaufnahme**: ein Momentaufnahme Speicherort für Mergeveröffentlichungen, die parametrisierte Zeilen Filter verwenden. Weitere Informationen finden Sie unter [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).  
-   **FTP-Ordner**: ein Ordner, auf den ein Dateiübertragungsprotokoll (FTP)-Server zugreifen kann. Weitere Informationen finden Sie unter [Übertragen von Momentaufnahmen über FTP](transfer-snapshots-through-ftp.md).  
  
 **Momentaufnahmeordner**  
 Wenn Sie für die Option **Momentaufnahmespeicherort** einen anderen Wert als **Standardspeicherort** auswählen, müssen Sie einen Pfad zum Momentaufnahmeordner angeben.  
  
 **Verwenden der Synchronisierungs Verwaltung von Windows**  
 Bestimmt, ob dieses Abonnement mithilfe von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Synchronization Manager synchronisiert werden kann.  
  
 **Sicherheit**  
 Klicken Sie auf die Zeile **Agentprozesskonto**, und klicken Sie dann auf die Schaltfläche mit den **drei Punkten**, um das Konto zu ändern, unter dem der Verteilungs-Agent oder der Merge-Assistent auf dem Abonnenten ausgeführt werden. Die Sicherheitsoptionen für Verbindungen sind vom Typ des Abonnements abhängig:  
  
-   Für Abonnements einer Transaktionsveröffentlichung: Sie können das Konto, unter dem der Verteilungs-Agent Verbindungen mit dem Verteiler erstellt, ändern, indem Sie auf **Verteilerverbindung**und anschließend auf die Schaltfläche mit den **drei Punkten**klicken.    
-   Für Abonnements mit sofortigem Update von Transaktionsveröffentlichungen: zusätzlich zur oben beschriebenen Verteilerverbindung können Sie die Methode ändern, mit der Änderungen vom Abonnenten zum Verleger übermittelt werden: klicken Sie auf **Verlegerverbindung**und anschließend auf die **Schaltfläche mit den drei Punkten**.  
-   Für Abonnements von Mergeveröffentlichungen, klicken Sie auf **Verlegerverbindung**und anschließend auf die Schaltfläche mit den **drei Punkten**.  
  
 Weitere Informationen zu den für die einzelnen Agents erforderlichen Berechtigungen finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
### <a name="options-for-transactional-subscriptions"></a>Optionen für Transaktionsabonnements  
 **Aktualisier bares Abonnement**  
 Legt fest, ob die am Abonnenten vorgenommenen Änderungen zurück auf den Verleger repliziert werden. Änderungen können entweder mit einem sofortigen Update oder mit einem verzögerten Update über eine Warteschlange repliziert werden. Mit der Option **Updatemethode für Abonnent** wird die zu verwendende Methode festgelegt. Weitere Informationen finden Sie unter [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md).  
  
### <a name="options-for-merge-subscriptions"></a>Optionen für Mergeabonnements  
 **Partitions Definition (HOST_NAME)**  
 Wenn Sie eine Mergereplikation für eine Veröffentlichung mit parametrisierten Filtern ausführen, wird bei der Synchronisierung eine der beiden Systemfunktionen, **SUSER_SNAME()** oder **HOST_NAME()**(oder beide, sofern die Filter auf beide Funktionen verweisen) ausgewertet, um festzulegen, welche Daten der Abonnent empfangen soll. 
  **HOST_NAME()** gibt standardmäßig den Namen des Computers zurück, auf dem der Merge-Agent ausgeführt wird. Sie können diesen Wert jedoch im Assistenten für neue Abonnements überschreiben. Weitere Informationen zu parametrisierten Filtern und zum Überschreiben von **HOST_NAME()** finden Sie unter [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
 **Abonnementtyp** und **Priorität**  
 Zeigt an, ob es sich bei dem Abonnement um ein Client- oder Serverabonnement handelt (kann nach Erstellen des Abonnements nicht mehr geändert werden). Bei Serverabonnements können Daten erneut für andere Abonnenten veröffentlicht und eine Priorität für die Konfliktlösung festgelegt werden.  
  
 Wenn Sie im Assistenten für neue Abonnements als Abonnementtyp Server ausgewählt haben, wird dem Abonnenten eine Priorität für die Konfliktlösung zugewiesen.  
  
 **Konflikte interaktiv lösen**  
 Legt fest, ob die bei der Synchronisierung auftretenden Konflikte mit der Benutzeroberfläche des interaktiven Konfliktlösers gelöst werden sollen. Dafür ist für **Synchronisierungsverwaltung von Windows verwenden** der Wert **Aktivieren**erforderlich. Weitere Informationen finden Sie unter [Interactive Conflict Resolution](merge/advanced-merge-replication-conflict-interactive-resolution.md).  
  
 **Websynchronisierung**  
 **Websynchronisierung verwenden** bestimmt, ob eine Verbindung [!INCLUDE[msCoName](../../includes/msconame-md.md)] mit einem Internetinformationsdienste (IIS)-Server hergestellt werden soll, um das Abonnement zu synchronisieren. Diese Option ist nur verfügbar, wenn die Veröffentlichung für die Websynchronisierung aktiviert ist. Weitere Informationen finden Sie unter [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).  
  
 Wenn Sie für **Websynchronisierung verwenden** den Wert **True**auswählen:  
  
-   Geben Sie die vollständige Adresse des IIS-Servers in **Webserveradresse**ein.   
-   Klicken Sie auf die Zeile **Webserververbindung** , und klicken Sie anschließend auf die Schaltfläche mit den **drei Punkten**, um das Konto festzulegen oder zu ändern, unter dem der Abonnent eine Verbindung mit dem IIS-Server herstellt.   
-   Falls erforderlich, ändern Sie **Webservertimeout** . Ein Timeout bezeichnet die Dauer in Sekunden, bevor eine Websynchronisierungsanforderung ungültig wird.  
  
 Weitere Informationen zur Konfiguration finden Sie unter [Configure Web Synchronization](configure-web-synchronization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eigenschaften von Pullabonnements anzeigen und ändern](view-and-modify-pull-subscription-properties.md)   
 [Anzeigen und Ändern der Eigenschaften von Pushabonnements](view-and-modify-push-subscription-properties.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
