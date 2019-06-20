---
title: Verwenden Sie das Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen-Assistenten (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], databases
ms.assetid: 81e5e36d-735d-4731-8017-2654673abb88
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0be8ed6cf2a163b3c195cfb5e4e18440549b501c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62815725"
---
# <a name="use-the-add-database-to-availability-group-wizard-sql-server-management-studio"></a>Verwenden des Assistenten zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen (SQL Server Management Studio)
  Verwenden Sie den Assistenten zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen, um einer vorhandenen AlwaysOn-Verfügbarkeitsgruppe eine oder mehrere Datenbank hinzuzufügen.  
  
> [!NOTE]  
>  Informationen zum Hinzufügen einer Datenbank mithilfe von [!INCLUDE[tsql](../../../includes/tsql-md.md)] oder PowerShell finden Sie unter [Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](availability-group-add-a-database.md).  
  
 **In diesem Thema:**  
  
-   **Vorbereitungen:**  
  
     [Voraussetzungen und Einschränkungen](#Prerequisites)  
  
     [Sicherheit](#Security)  
  
-   **Zum Hinzufügen einer Datenbank mit:**  [Fügen Sie Datenbank hinzu, um den Assistenten für Verfügbarkeitsgruppen (SQL Server Management Studio)](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
 Wenn Sie einer verfügbarkeitsgruppe noch nie eine Datenbank hinzugefügt haben, finden Sie im Abschnitt "Verfügbarkeitsdatenbanken" [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="Prerequisites"></a> Voraussetzungen, Einschränkungen und Empfehlungen  
  
-   Sie müssen mit der Serverinstanz verbunden sein, auf der das aktuelle primäre Replikat gehostet wird.  
  
-   Wenn eine Datenbank verschlüsselt ist oder sogar einen Datenbankverschlüsselungs-Schlüssel (DEK) enthält, können Sie die Datenbank nicht mithilfe von [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] oder [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] einer Verfügbarkeitsgruppe hinzufügen. Selbst wenn eine verschlüsselte Datenbank entschlüsselt wurde, enthalten ihre Protokollsicherungen möglicherweise verschlüsselte Daten. In diesem Fall ist es unter Umständen nicht möglich, die anfängliche Datensynchronisierung vollständig auf der Datenbank durchzuführen. Grund hierfür ist die Tatsache, dass für den Wiederherstellungsprotokollvorgang eventuell das Zertifikat erforderlich ist, das von den Datenbank-Verschlüsselungsschlüsseln (DEKs) verwendet wurde, und dieses Zertifikat möglicherweise nicht verfügbar ist.  
  
     **So erstellen Sie eine entschlüsselte Datenbank verfügbar für das zu einer verfügbarkeitsgruppe mithilfe des Assistenten zum Hinzufügen**  
  
    1.  Erstellen Sie eine Protokollsicherung von der primären Datenbank.  
  
    2.  Erstellen Sie eine vollständige Datenbanksicherung der primären Datenbank.  
  
    3.  Stellen Sie die Datenbanksicherung auf der Serverinstanz wieder her, die das sekundäre Replikat hostet.  
  
    4.  Erstellen Sie eine neue Protokollsicherung aus der primären Datenbank.  
  
    5.  Stellen Sie diese Protokollsicherung in der sekundären Datenbank wieder her.  
  
-   **Voraussetzungen für die Verwendung der vollständigen anfänglichen Datensynchronisierung**  
  
    -   Alle Datenbankdateipfade müssen auf allen Serverinstanzen, die ein Replikat für die neue Verfügbarkeitsgruppe hosten, identisch sein.  
  
    -   Primäre Datenbanknamen können nicht auf Serverinstanzen vorhanden sein, die ein sekundäres Replikat hosten. Daher kann noch keine der neuen sekundären Datenbanken vorhanden sein.  
  
    -   Sie müssen eine Netzwerkfreigabe angeben, damit der Assistent Sicherungen erstellen und auf Sicherungen zugreifen kann. Für das primäre Replikat kann das zum Starten von [!INCLUDE[ssDE](../../../includes/ssde-md.md)] verwendete Konto über Lese- und Schreibberechtigungen für das Dateisystem in einer Netzwerkfreigabe verfügen. Bei sekundären Replikaten muss das Konto über eine Leseberechtigung für die Netzwerkfreigabe verfügen.  
  
     Wenn Sie nicht den Assistenten für eine vollständige anfängliche Datensynchronisierung verwenden können, müssen Sie die sekundären Datenbanken manuell vorbereiten. Dies ist vor oder nach dem Ausführen des Assistenten möglich. Weitere Informationen finden Sie unter [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)erstellt und konfiguriert wird.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.  
  
##  <a name="SSMSProcedure"></a> Verwenden des Assistenten zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen(SQL Server Management Studio)  
 **So verwenden Sie den Assistenten zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Serverinstanz her, die das primäre Replikat der Verfügbarkeitsgruppe hostet, und erweitern Sie die Serverstruktur.  
  
2.  Erweitern Sie den Knoten **Hohe Verfügbarkeit (immer aktiviert)** und den Knoten **Verfügbarkeitsgruppen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Verfügbarkeitsgruppe, der Sie eine Datenbank hinzufügen, und wählen Sie den Befehl **Datenbank hinzufügen** aus. Dieser Befehl startet den Assistenten zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen.  
  
4.  Wählen Sie auf der Seite **Datenbanken auswählen** mindestens eine Datenbank aus. Weitere Informationen finden Sie unter [Seite "Datenbanken" wählen &#40;-Assistent – hinzufügen Datenbankassistenten für neue Verfügbarkeitsgruppen&#41;](select-databases-page-new-availability-group-wizard-and-add-database-wizard.md).  
  
5.  Wählen Sie auf der Seite **Anfängliche Datensynchronisierung auswählen** aus, wie die neuen sekundären Datenbanken erstellt und mit der Verfügbarkeitsgruppe verknüpft werden sollen. Wählen Sie eine der folgenden Optionen aus:  
  
    -   **Full**  
  
         Aktivieren Sie diese Option, wenn Ihre Umgebung die Anforderungen zum automatischen Starten der anfänglichen Datensynchronisierung erfüllt. Weitere Informationen finden Sie weiter oben in diesem Thema unter [Voraussetzungen, Einschränkungen und Empfehlungen](#Prerequisites).  
  
         Wenn Sie **Vollständig**auswählen, versucht der Assistent, nach der Erstellung der Verfügbarkeitsgruppe alle primären Datenbanken und ihre Transaktionsprotokolle auf einer Netzwerkfreigabe zu sichern und die Sicherungen auf allen Serverinstanzen wiederherzustellen, die ein sekundäres Replikat hosten. Der Assistent verknüpft anschließend alle sekundären Datenbanken mit der Verfügbarkeitsgruppe.  
  
         Legen Sie im Feld zum **Angeben eines freigegebenen Netzwerkspeicherorts, auf den von allen Replikaten zugegriffen werden kann** , eine Sicherungsfreigabe fest, für die alle Serverinstanzen, die Replikate hosten, Lese-/Schreibzugriff besitzen. Die Protokollsicherungen sind Teil der Protokollsicherungskette. Speichern Sie die Protokollsicherungsdateien ordnungsgemäß.  
  
        > [!IMPORTANT]  
        >  Informationen zu den erforderlichen Dateisystemberechtigungen finden Sie weiter oben in diesem Thema unter [Erforderliche Komponenten](#Prerequisites).  
  
    -   **Nur verknüpfen**  
  
         Wenn Sie sekundäre Datenbanken auf den Serverinstanzen, die die sekundären Replikate hosten, manuell vorbereitet haben, können Sie diese Option aktivieren. Der Assistent verknüpft die vorhandenen sekundären Datenbanken mit der Verfügbarkeitsgruppe.  
  
    -   **Anfängliche Datensynchronisierung überspringen**  
  
         Aktivieren Sie diese Option, wenn Sie eigene Datenbank- und Protokollsicherungen der primären Datenbanken verwenden möchten. Weitere Informationen finden Sie unter [Starten der Datenverschiebung auf einer sekundären AlwaysOn-Datenbank &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
     Weitere Informationen finden Sie unter [anfängliche Datensynchonisierung auswählen &#40;AlwaysOn-Verfügbarkeitsgruppen-Assistenten&#41;](select-initial-data-synchronization-page-always-on-availability-group-wizards.md).  
  
6.  Klicken Sie auf der Seite **Mit vorhandenen sekundären Replikaten verbinden** auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Alle verbinden **, wenn die Instanzen von**, die die Verfügbarkeitsreplikate für diese Verfügbarkeitsgruppe hosten, als ein Dienst unter demselben Benutzerkonto ausgeführt werden. Wenn eine der Serverinstanzen als Dienst unter verschiedenen Konten ausgeführt wird, klicken Sie rechts neben jedem Serverinstanznamen jeweils auf die Schaltfläche **Verbinden** .  
  
     Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit vorhandenen sekundären Replikaten Seite &#40;Assistent zum Hinzufügen von Replikaten und Assistenten zum Hinzufügen von Datenbanken&#41;](connect-to-existing-secondary-replicas-page.md).  
  
7.  Auf der Seite **Überprüfung** wird überprüft, ob die in diesem Assistenten angegebenen Werte die Anforderungen des Assistenten für neue Verfügbarkeitsgruppen erfüllen. Um eine Änderung vorzunehmen, können Sie auf **Zurück** klicken, um zu einer vorherigen Assistentenseite zurückzukehren und Werte zu ändern. Klicken Sie anschließend auf **Weiter** , um auf die Seite **Überprüfung** zurückzukehren, und klicken Sie auf **Überprüfung erneut ausführen**.  
  
     Weitere Informationen finden Sie unter [Seite "Überprüfung" &#40;AlwaysOn-Verfügbarkeitsgruppen-Assistenten&#41;](validation-page-always-on-availability-group-wizards.md).  
  
8.  Überprüfen Sie auf der Seite **Zusammenfassung** die Optionen für die neue Verfügbarkeitsgruppe. Um eine Änderung vorzunehmen, klicken Sie auf **Zurück** , um zu der relevanten Seite zurückzukehren. Nachdem Sie die Änderung vorgenommen haben, klicken Sie auf **Weiter** , um zur Seite **Zusammenfassung** zurückzukehren.  
  
     Weitere Informationen finden Sie unter [Seite "Zusammenfassung" &#40;AlwaysOn-Verfügbarkeitsgruppen-Assistenten&#41;](summary-page-always-on-availability-group-wizards.md).  
  
     Wenn Sie mit der Auswahl zufrieden sind, klicken Sie optional auf "Skript", um ein Skript der Schritte zu erstellen, die der Assistent ausführt. Klicken Sie dann zum Erstellen und Konfigurieren der neuen Verfügbarkeitsgruppe auf **Fertig stellen**.  
  
9. Auf der Seite **Status** wird der Status der Schritte zum Erstellen der Verfügbarkeitsgruppe angezeigt (Konfigurieren von Endpunkten, Erstellen der Verfügbarkeitsgruppe und Hinzufügen des sekundären Replikats zu der Gruppe).  
  
     Weitere Informationen finden Sie unter [Statusseite &#40;AlwaysOn-Verfügbarkeitsgruppen-Assistenten&#41;](progress-page-always-on-availability-group-wizards.md).  
  
10. Wenn diese Schritte abgeschlossen sind, wird auf der Seite **Ergebnisse** das Ergebnis der einzelnen Schritte angezeigt. Wenn all diese Schritte erfolgreich sind, ist die neue Verfügbarkeitsgruppe vollständig konfiguriert. Wenn einer der Schritte zu einem Fehler führt, müssen Sie die Konfiguration möglicherweise manuell abschließen. Klicken Sie in der Spalte **Ergebnis** auf den zugehörigen Fehlerlink, um weitere Informationen zur Ursache eines bestimmten Fehlers zu erhalten.  
  
     Klicken Sie nach Abschluss des Assistenten auf **Schließen** , um den Assistenten zu beenden.  
  
     Weitere Informationen finden Sie unter der [Seite 'Ergebnisse' &#40;AlwaysOn-Verfügbarkeitsgruppen-Assistenten&#41;](results-page-always-on-availability-group-wizards.md).  
  
11. Wenn die anfängliche Datensynchronisierung nicht automatisch auf allen sekundären Datenbanken gestartet wurde, müssen Sie noch nicht verknüpfte Datenbanken konfigurieren. Weitere Informationen finden Sie unter [Starten der Datenverschiebung auf einer sekundären AlwaysOn-Datenbank &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe (SQL Server)](availability-group-add-a-database.md)   
 [Starten der Datenverschiebung auf einer sekundären AlwaysOn-Datenbank &#40;SQLServer&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)   
 [Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
  
