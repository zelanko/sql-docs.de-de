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
ms.openlocfilehash: f2b925540844a45d94fb2ee823a8ac5e9bc7ef2a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095640"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a>Verwenden des Assistenten zum Hinzufügen von Azure-Replikaten (SQL Server)
  Der Assistent zum Hinzufügen von Azure-Replikaten unterstützt Sie dabei, eine neue Windows Azure-VM in einer hybriden IT-Umgebung zu erstellen und als sekundäres Replikat für eine neue oder vorhandene AlwaysOn-Verfügbarkeitsgruppe zu konfigurieren.  
  
-   **Vorbereitungen:**  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
     [Security](#Security)  
  
-   **Fügen Sie ein Replikat hinzu mit:**  [Assistent zum Hinzufügen von Azure-Replikaten (SQL Server Management Studio)](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
 Wenn Sie noch nie zu einer verfügbarkeitsgruppe ein verfügbarkeitsreplikat hinzugefügt haben, finden Sie unter der "Serverinstanzen" und "Verfügbarkeitsgruppen und Replikate" Abschnitte in [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Sie müssen mit der Serverinstanz verbunden sein, auf der das aktuelle primäre Replikat gehostet wird.  
  
-   Sie benötigen eine hybride IT-Umgebung, in der das lokale Subnetz über ein Standort-zu-Standort-VPN mit Windows Azure verbunden ist. Weitere Informationen finden Sie unter [Konfigurieren eines Standort-zu-Standort-VPNs im Verwaltungsportal](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create).  
  
-   Ihre Verfügbarkeitsgruppe muss lokale Verfügbarkeitsreplikate enthalten.  
  
-   Clients des Verfügbarkeitsgruppenlisteners müssen über Internetverbindungen verfügen, falls sie mit dem Listener verbunden bleiben sollen, wenn für die Verfügbarkeitsgruppe ein Failover auf ein Windows Azure-Replikat ausgeführt wird.  
  
-   **Voraussetzungen für die Verwendung der vollständigen anfänglichen Datensynchronisierung** : Sie müssen eine Netzwerkfreigabe angeben, damit der Assistent Sicherungen erstellen und darauf zugreifen kann. Für das primäre Replikat kann das zum Starten von [!INCLUDE[ssDE](../../../includes/ssde-md.md)] verwendete Konto über Lese- und Schreibberechtigungen für das Dateisystem in einer Netzwerkfreigabe verfügen. Bei sekundären Replikaten muss das Konto über eine Leseberechtigung für die Netzwerkfreigabe verfügen.  
  
     Wenn Sie nicht den Assistenten für eine vollständige anfängliche Datensynchronisierung verwenden können, müssen Sie die sekundären Datenbanken manuell vorbereiten. Dies ist vor oder nach dem Ausführen des Assistenten möglich. Weitere Informationen finden Sie unter [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)erstellt und konfiguriert wird.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Siehe [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)  
  
##  <a name="SSMSProcedure"></a> Verwenden des Assistenten zum Hinzufügen von Azure-Replikaten (SQL Server Management Studio)  
 Der Assistent zum Hinzufügen von Azure-Replikaten kann auf der Seite [Replikate angeben](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)gestartet werden. Die Seite kann auf zwei Weisen aufgerufen werden:  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Assistenten zum Hinzufügen von Replikaten zu Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 Nachdem Sie den Assistenten zum Hinzufügen von Azure-Replikaten gestartet haben, führen Sie die folgenden Schritte aus:  
  
1.  Laden Sie zunächst ein Verwaltungszertifikat für Ihr Windows Azure-Abonnement herunter. Klicken Sie auf **Herunterladen** , um die Anmeldeseite zu öffnen.  
  
2.  Melden Sie sich auf der Anmeldeseite beim Windows Azure-Abonnement an. Sobald Sie angemeldet sind, installiert der Assistent ein Verwaltungszertifikat auf dem lokalen Computer. Dieses Verwaltungszertifikat wird automatisch geladen, wenn Sie den Assistenten erneut verwenden. Wenn Sie mehrere Verwaltungszertifikate heruntergeladen haben, können Sie auf die Schaltfläche zum Durchsuchen ( **...** ) klicken, um das gewünschte Zertifikat auszuwählen.  
  
3.  Stellen Sie als Nächstes eine Verbindung mit dem Abonnement her, indem Sie auf **Verbinden**klicken. Sobald die Verbindung hergestellt ist, werden die Dropdownlisten mit den Microsoft Azure-Parametern, wie **Virtuelles Netzwerk** und **Virtuelles Netzwerk – Subnetz**, aufgefüllt.  
  
4.  Geben Sie die Einstellungen für die Windows Azure-VM an, die das neue sekundäre Replikat hostet:  
  
     Bild  
     Der Name des SQL Server-Images, das für die Windows Azure-VM verwendet werden soll.  
  
     VM-Größe  
     Die Größe der Windows Azure-VM.  
  
     VM-Name  
     Der DNS-Name der Windows Azure-VM.  
  
     VM-Benutzername  
     Der Benutzername des Standardadministrators für die Windows Azure-VM.  
  
     VM-Administratorkennwort (und Kennwortbestätigung)  
     Das Kennwort des Standardadministrators für die Windows Azure-VM.  
  
     Virtuelles Netzwerk  
     Das virtuelle Netzwerk, in das die Windows Azure-VM eingefügt werden soll.  
  
     Virtuelles Netzwerk – Subnetz  
     Das Subnetz des virtuellen Netzwerks, in das die Windows Azure-VM eingefügt werden soll.  
  
     Domäne  
     Die Active Directory (AD)-Domäne, mit der die Windows Azure-VM verknüpft werden soll.  
  
     Domänenbenutzername  
     Der AD-Benutzername, über den die Windows Azure-VM mit der Domäne verknüpft wird.  
  
     Kennwort  
     Das Kennwort, über das die Windows Azure-VM mit der Domäne verknüpft wird.  
  
5.  Klicken Sie auf **OK** , um Ihre Einstellungen zu bestätigen und den Assistenten zum Hinzufügen von Azure-Replikaten zu beenden.  
  
6.  Führen Sie die übrigen Konfigurationsschritte auf der Seite [Replikate angeben](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) wie für jedes neue Replikat aus.  
  
     Sobald Sie den Assistenten für neue Verfügbarkeitsgruppen oder den Assistenten zum Hinzufügen von Replikaten zu Verfügbarkeitsgruppen abgeschlossen haben, werden vom Konfigurationsprozess alle notwendigen Vorgänge in Windows Azure ausgeführt, um die neue VM zu erstellen, mit der AD-Domäne zu verknüpfen, dem Windows-Cluster hinzuzufügen, hohe Verfügbarkeit mit AlwaysOn zu aktivieren und das neue Replikat der Verfügbarkeitsgruppe hinzuzufügen.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Hinzufügen eines sekundären Replikats zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Hinzufügen eines sekundären Replikats zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
