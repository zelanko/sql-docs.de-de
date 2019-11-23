---
title: Verwenden des Assistenten zum Hinzufügen von Azure-Replikaten (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 90418193ac869641a20f8b0f684fc43dd46712f8
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70175993"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a>Verwenden des Assistenten zum Hinzufügen von Azure-Replikaten (SQL Server)
  Mithilfe des Assistenten zum Hinzufügen von Azure-Replikaten können Sie eine neue Azure-VM in Hybrid-IT erstellen und als sekundäres Replikat für eine neue oder vorhandene AlwaysOn-Verfügbarkeits Gruppe konfigurieren.  
  
-   **Vorbereitungen:**  
  
     [Voraussetzungen](#Prerequisites)  
  
     [Sicherheit](#Security)  
  
-   **Fügen Sie ein Replikat hinzu mit:**  [Assistent zum Hinzufügen von Azure-Replikaten (SQL Server Management Studio)](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
 Wenn Sie einer Verfügbarkeits Gruppe noch nie ein Verfügbarkeits Replikat hinzugefügt haben, lesen Sie die Abschnitte "Server Instanzen" und "Verfügbarkeits Gruppen und-Replikate" unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="Prerequisites"></a>Voraussetzungen  
  
-   Sie müssen mit der Serverinstanz verbunden sein, auf der das aktuelle primäre Replikat gehostet wird.  
  
-   Sie benötigen eine hybride IT-Umgebung, in der das lokale Subnetz über ein Site-to-Site-VPN mit Azure verbunden ist. Weitere Informationen finden Sie unter [Konfigurieren eines Standort-zu-Standort-VPNs im Verwaltungsportal](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create).  
  
-   Ihre Verfügbarkeitsgruppe muss lokale Verfügbarkeitsreplikate enthalten.  
  
-   Clients des Verfügbarkeitsgruppenlisteners müssen über Internetverbindungen verfügen, falls sie mit dem Listener verbunden bleiben sollen, wenn für die Verfügbarkeitsgruppe ein Failover auf ein Azure-Replikat ausgeführt wird.  
  
-   **Voraussetzungen für die Verwendung der vollständigen anfänglichen Datensynchronisierung** : Sie müssen eine Netzwerkfreigabe angeben, damit der Assistent Sicherungen erstellen und darauf zugreifen kann. Für das primäre Replikat kann das zum Starten von [!INCLUDE[ssDE](../../../includes/ssde-md.md)] verwendete Konto über Lese- und Schreibberechtigungen für das Dateisystem in einer Netzwerkfreigabe verfügen. Bei sekundären Replikaten muss das Konto über eine Leseberechtigung für die Netzwerkfreigabe verfügen.  
  
     Wenn Sie nicht den Assistenten für eine vollständige anfängliche Datensynchronisierung verwenden können, müssen Sie die sekundären Datenbanken manuell vorbereiten. Dies ist vor oder nach dem Ausführen des Assistenten möglich. Weitere Informationen finden Sie unter [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Berechtigungen  
 Siehe [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)  
  
##  <a name="SSMSProcedure"></a> Verwenden des Assistenten zum Hinzufügen von Azure-Replikaten (SQL Server Management Studio)  
 Der Assistent zum Hinzufügen von Azure-Replikaten kann auf der Seite [Replikate angeben](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)gestartet werden. Die Seite kann auf zwei Weisen aufgerufen werden:  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Assistenten zum Hinzufügen von Replikaten zu Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 Nachdem Sie den Assistenten zum Hinzufügen von Azure-Replikaten gestartet haben, führen Sie die folgenden Schritte aus:  
  
1.  Laden Sie zunächst ein Verwaltungszertifikat für Ihr Azure-Abonnement herunter. Klicken Sie auf **Herunterladen** , um die Anmeldeseite zu öffnen.  
  
2.  Melden Sie sich auf der Anmeldeseite bei Ihrem Azure-Abonnement an. Sobald Sie angemeldet sind, installiert der Assistent ein Verwaltungszertifikat auf dem lokalen Computer. Dieses Verwaltungszertifikat wird automatisch geladen, wenn Sie den Assistenten erneut verwenden. Wenn Sie mehrere Verwaltungszertifikate heruntergeladen haben, können Sie auf die Schaltfläche zum Durchsuchen ( **...** ) klicken, um das gewünschte Zertifikat auszuwählen.  
  
3.  Stellen Sie als Nächstes eine Verbindung mit dem Abonnement her, indem Sie auf **Verbinden**klicken. Sobald die Verbindung hergestellt ist, werden die Dropdownlisten mit den Azure-Parametern, wie **Virtuelles Netzwerk** und **Virtuelles Netzwerk – Subnetz**, aufgefüllt.  
  
4.  Geben Sie die Einstellungen für die Azure-VM an, die das neue sekundäre Replikat hostet:  
  
     Bild  
     Der Name des SQL Server-Images, das für die Azure-VM verwendet werden soll.  
  
     VM-Größe  
     Die Größe der Azure-VM.  
  
     VM-Name  
     Der DNS-Name der Azure-VM.  
  
     VM-Benutzername  
     Der Benutzername des Standardadministrators für die Azure-VM.  
  
     VM-Administratorkennwort (und Kennwortbestätigung)  
     Das Kennwort des Standardadministrators für die Azure-VM.  
  
     Virtuelles Netzwerk  
     Das virtuelle Netzwerk, in das die Azure-VM eingefügt werden soll.  
  
     Virtuelles Netzwerk – Subnetz  
     Das Subnetz des virtuellen Netzwerks, in das die Azure-VM eingefügt werden soll.  
  
     Domäne  
     Die Active Directory (AD)-Domäne, mit der die Azure-VM verknüpft werden soll.  
  
     Domänenbenutzername  
     Der AD-Benutzername, über den die Azure-VM mit der Domäne verknüpft wird.  
  
     Kennwort  
     Das Kennwort, über das die Azure-VM mit der Domäne verknüpft wird.  
  
5.  Klicken Sie auf **OK** , um Ihre Einstellungen zu bestätigen und den Assistenten zum Hinzufügen von Azure-Replikaten zu beenden.  
  
6.  Führen Sie die übrigen Konfigurationsschritte auf der Seite [Replikate angeben](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) wie für jedes neue Replikat aus.  
  
     Wenn Sie den Assistenten für Verfügbarkeits Gruppen oder den Assistenten zum Hinzufügen von Replikaten zu Verfügbarkeits Gruppen abgeschlossen haben, führt der Konfigurationsprozess alle Vorgänge in Azure aus, um den neuen virtuellen Computer zu erstellen, ihn mit der AD-Domäne zu verknüpfen, ihn dem Windows-Cluster hinzuzufügen und AlwaysOn hoch Verfügbarkeit, und fügen Sie das neue Replikat der Verfügbarkeits Gruppe hinzu.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Hinzufügen eines sekundären Replikats zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41; ](overview-of-always-on-availability-groups-sql-server.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41; ](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Hinzufügen eines sekundären Replikats zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
