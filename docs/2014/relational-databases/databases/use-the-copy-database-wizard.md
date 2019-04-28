---
title: Verwenden des Assistenten zum Kopieren von Datenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.cdw.transfermethod.f1
- sql12.swb.cdw.welcome.f1
- sql12.swb.cdw.packageconfiguration.f1
- sql12.swb.cdw.schedule.f1
- sql12.swb.cdw.destination.f1
- sql12.swb.cdw.complete.f1
- sql12.swb.cdw.destinationconfiguration.f1
- sql12.swb.cdw.selectdatabaseobjects.f1
- sql12.swb.cdw.databases.f1
- sql12.swb.cdw.source.f1
- sql12.swb.cdw.locationofsourcedbfiles.f1
helpviewer_keywords:
- Copy Database Wizard
- starting Copy Database Wizard
ms.assetid: 7a999fc7-0a26-4a0d-9eeb-db6fc794f3cb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e72b960db0fd5b733119cafeca98f124eaa15f38
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871137"
---
# <a name="use-the-copy-database-wizard"></a>Verwenden des Assistenten zum Kopieren von Datenbanken
  Mit dem Assistenten zum Kopieren von Datenbanken können Sie Datenbanken und zugehörige Objekte von einem Server auf einen anderen ohne Serverausfallzeiten verschieben oder kopieren. Sie können auch Datenbanken von einer früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version zu [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]aktualisieren. Mit diesem Assistenten können Sie folgende Aktionen ausführen:  
  
-   Einen Quell- und Zielserver auswählen.  
  
-   Wählen Sie Datenbanken aus, die verschoben, kopiert oder aktualisiert werden sollen.  
  
-   Den Dateispeicherort für die Datenbanken angeben.  
  
-   Anmeldungen auf dem Zielserver erstellen.  
  
-   Zusätzliche unterstützende Objekte, Aufträge, benutzerdefinierte gespeicherte Prozeduren und Fehlermeldungen kopieren.  
  
-   Planen, wann die Datenbanken verschoben oder kopiert werden.  
  
 Zusätzlich zum Kopieren von Datenbanken können Sie zugehörige Metadaten, wie Anmeldedaten und Objekte, aus der **Masterdatenbank** kopieren, die von einer kopierten Datenbank angefordert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **Verwenden des Assistenten zum Kopieren einer Datenbank an:**  
  
     [Kopieren, verschieben oder Aktualisieren von Datenbanken](#Copy_Move)  
  
-   **Nachverfolgung, nach dem Upgrade:**  
  
     [Nach dem Aktualisieren einer SQL Server-Datenbank](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Der Assistent zum Kopieren von Datenbanken ist nicht in der Express Edition verfügbar.  
  
-   Der Assistent zum Kopieren von Datenbanken kann nicht zum Kopieren oder Verschieben der folgenden Datenbanken verwendet werden.  
  
    -   Systemdatenbanken  
  
    -   Zur Replikation markierte Datenbanken.  
  
    -   Datenbanken mit der Kennzeichnung Kein Zugriff, Lädt, Offline, Wird wiederhergestellt, Fehlerverdächtig oder Notfallmodus.  
  
-   Nach dem Aktualisieren einer Datenbank kann es nicht zu einer früheren Version herabgestuft werden.  
  
-   Wenn Sie die Option **Verschieben** auswählen, wird die Quelldatenbank nach dem Verschieben der Datenbank automatisch vom Assistenten gelöscht. Wenn Sie die Option **Kopieren** auswählen, wird die Quelldatenbank vom Assistenten zum Kopieren von Datenbanken nicht gelöscht.  
  
-   Wenn Sie den Volltextkatalog mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object-Methode verschieben, müssen Sie den Index nach dem Verschieben wieder auffüllen.  
  
-   Die Methode zum Trennen und Anfügen trennt die Datenbank, verschiebt oder kopiert die MDF-, NDF- und LDF-Dateien der Datenbank und fügt die Datenbank am neuen Zielort wieder an. Bei der Methode zum Trennen und Anfügen können zur Vermeidung von Datenverlust und Inkonsistenzen keine aktiven Sitzungen an die verschobene oder kopierte Datenbank angefügt werden. Wenn aktive Sitzungen vorhanden sind, wird der Verschiebe- bzw. Kopiervorgang vom Assistenten zum Kopieren von Datenbanken nicht ausgeführt. Bei der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object-Methode werden aktive Sitzungen zugelassen, da die Datenbank nie offline gesetzt wird.  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
 Stellen Sie sicher, dass SQL Server-Agent auf dem Zielserver gestartet wird.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Um die optimale Leistung einer aktualisierten Datenbank sicherzustellen, führen Sie sp_updatestats (Statistikupdate) für die aktualisierte Datenbank aus.  
  
-   Wenn Sie eine Datenbank auf eine andere Serverinstanz kopieren, müssen Sie möglicherweise einen Teil oder auch alle Metadaten für die Datenbank, wie Anmeldenamen und Aufträge, auf der anderen Serverinstanz erneut erstellen, um Benutzern und Anwendungen ein konsistentes Verhalten zu bieten. Weitere Informationen finden Sie unter [Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einer anderen Serverinstanz &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Sie müssen auf dem Quell- und Zielserver ein Mitglied der festen Serverrolle **sysadmin** sein.  
  
##  <a name="Copy_Move"></a> Kopieren, verschieben oder Aktualisieren von Datenbanken  
  
1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Objekt-Explorer **Datenbanken**, klicken Sie mit der rechten Maustaste auf eine Datenbank, zeigen Sie auf **Tasks**, und klicken Sie dann auf **Datenbank kopieren**.  
  
2.  Geben Sie auf der Seite **Quellserver auswählen** den Server an, auf dem sich die zu verschiebende oder zu kopierende Datenbank befindet, und geben Sie die Anmeldeinformationen ein. Nach der Auswahl der Authentifizierungsmethode und der Eingabe der Anmeldeinformationen, klicken Sie auf **Weiter** , um die Verbindung zum Quellserver herzustellen. Diese Verbindung bleibt während der ganzen Sitzung bestehen.  
  
     **Quellserver**  
     Wählen Sie den Namen des Servers bzw. der Serverinstanz aus, auf dem bzw. der sich die zu verschiebenden oder zu kopierenden Datenbanken befinden. Sie können auch auf die Schaltfläche zum Durchsuchen klicken (**...**), um nach dem gewünschten Server zu suchen. Der Server muss mindestens [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]sein.  
  
     **Windows-Authentifizierung verwenden**  
     Ermöglicht den Benutzern eine Verbindung über ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Benutzerkonto.  
  
     **SQL Server-Authentifizierung verwenden**  
     Ermöglicht den Benutzern, mithilfe eines Benutzernamens und eines Kennworts für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung aufzubauen.  
  
     **Benutzername**  
     Geben Sie den Benutzernamen für die Verbindung ein. Diese Option ist nur verfügbar, wenn Sie zum Verbinden die Authentifizierung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgewählt haben.  
  
     **Kennwort**  
     Geben Sie das Kennwort für die Anmeldung ein. Diese Option ist nur verfügbar, wenn Sie zum Verbinden die Authentifizierung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgewählt haben.  
  
     **Weiter**  
     Stellen Sie eine Verbindung zum Server her, und überprüfen Sie den Benutzer. Mit diesem Vorgang wird überprüft, ob der Benutzer ein Mitglied der festen **sysadmin** -Serverrolle auf dem ausgewählten Computer ist.  
  
3.  Geben Sie auf der Seite **Zielserver auswählen** den Server an, auf den die Datenbank verschoben oder kopiert werden soll. Wenn Quell- und Zielserver auf derselben Serverinstanz eingerichtet sind, wird eine Kopie der Datenbank erstellt. In diesem Fall müssen Sie die Datenbank zu einem späteren Zeitpunkt im Assistenten umbenennen. Der Name der Quelldatenbank kann nur für die kopierte oder verschobene Datenbank verwendet werden, wenn keine Namenskonflikte auf dem Zielserver bestehen. Wenn Namenskonflikte bestehen, müssen Sie diese manuell auf dem Zielserver lösen, bevor Sie den Namen der Quelldatenbank verwenden können.  
  
     **Zielserver**  
     Wählen Sie den Namen des Servers aus, auf den die Datenbank(en) kopiert oder verschoben wird/werden. Sie können auch auf die Schaltfläche zum Durchsuchen (**...**) klicken, um einen Zielserver zu suchen.  
  
    > [!NOTE]  
    >  Sie können einen gruppierten Server als Ziel verwenden. Mit dem Assistenten zum Kopieren von Datenbanken wird sichergestellt, dass Sie nur freigegebene Laufwerke auf einem gruppierten Zielserver auswählen.  
  
     **Windows-Authentifizierung verwenden**  
     Ermöglicht den Benutzern eine Verbindung über ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Benutzerkonto.  
  
     **SQL Server-Authentifizierung verwenden**  
     Ermöglicht den Benutzern, mithilfe eines Benutzernamens und eines Kennworts für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung aufzubauen.  
  
     **Benutzername**  
     Geben Sie den Benutzernamen für die Verbindung ein. Diese Option ist nur verfügbar, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung ausgewählt haben.  
  
     **Kennwort**  
     Geben Sie das Kennwort für die Anmeldung ein. Diese Option ist nur verfügbar, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung ausgewählt haben.  
  
     **Weiter**  
     Stellen Sie eine Verbindung zum Server her, und überprüfen Sie den Benutzer. Mit diesem Prozess wird überprüft, ob der Benutzer über die oben aufgeführten Berechtigungen für den ausgewählten Computern verfügt.  
  
4.  Wählen Sie auf der Seite **Übertragungsmethode auswählen** die Übertragungsmethode aus.  
  
     **Methode zum Trennen und Anfügen verwenden**  
     Trennt die Datenbank vom Quellserver, kopiert die Datenbankdateien (MDF, NDF und LDF) auf den Zielserver und fügt die Datenbank dem Zielserver hinzu. Diese Methode ist normalerweise die schnellere, weil die Hauptarbeit im Lesen des Quelldatenträgers und im Schreiben auf den Zieldatenträger besteht. Es ist keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Logik zum Erstellen von Objekten innerhalb der Datenbank oder zum Erstellen von Datenspeicherstrukturen erforderlich. Diese Methode kann zeitaufwändiger sein, wenn die Datenbank große zugeordnete, aber nicht verwendete Speicherbereiche enthält. Bei einer neuen und fast leeren Datenbank, die mit zugeordnetem Speicher von 100 MB erstellt wurde, werden beispielsweise die gesamten 100 MB kopiert, auch wenn nur 5 MB belegt sind.  
  
    > [!NOTE]  
    >  Bei dieser Methode ist die Datenbank während der Übertragung für die Benutzer nicht verfügbar.  
  
     **Bei Auftreten eines Fehlers Quelldatenbank erneut anfügen**  
     Wenn eine Datenbank kopiert wird, werden die ursprünglichen Datenbankdateien immer erneut an den Quellserver angefügt. Verwenden Sie dieses Feld, um ursprüngliche Dateien erneut an die Quelldatenbank anzufügen, wenn eine Datenbankverschiebung nicht beendet werden kann.  
  
     **SMO-Methode (SQL Management Object) verwenden**  
     Diese Methode liest die Definition jedes Datenbankobjekts in der Quelldatenbank und erstellt alle Objekte in der Zieldatenbank. Dann werden die Daten aus den Quelltabellen in die Zieltabellen übertragen, wobei Indizes und Metadaten neu erstellt werden.  
  
    > [!NOTE]  
    >  Datenbankbenutzer können während der Übertragung weiter auf die Datenbank zugreifen.  
  
5.  Wählen Sie auf der Seite **Datenbank auswählen** die Datenbank oder Datenbanken aus, die vom Quellserver auf den Zielserver kopiert oder verschoben werden soll(en). Weitere Informationen finden Sie unter [Einschränkungen](#Restrictions) im Abschnitt "Vorbereitungen" dieses Themas.  
  
     **Verschieben**  
     Verschiebt die Datenbank auf den Zielserver.  
  
     **Kopieren**  
     Kopiert die Datenbank auf den Zielserver.  
  
     **Quelle**  
     Zeigt die auf dem Quellserver vorhandenen Datenbanken an.  
  
     **Status**  
     Zeigt **OK** an, wenn die Datenbank verschoben werden kann. Andernfalls wird der Grund angezeigt, warum ein Verschieben der Datenbank nicht möglich ist.  
  
     **Aktualisieren**  
     Aktualisiert die Liste der Datenbanken.  
  
     **Weiter**  
     Startet den Überprüfungsvorgang und setzt den Vorgang dann im nächsten Bildschirm fort.  
  
6.  Auf der Seite **Zieldatenbank konfigurieren** ändern Sie bei Bedarf den Datenbanknamen und geben den Speicherort und die Namen der Datenbankdateien an. Diese Seite wird einmal für jede Datenbank angezeigt, die verschoben oder kopiert wird.  
  
7.  Auf der Seite **Datenbankobjekte auswählen** wählen Sie die Objekte aus, die ein Verschiebe- oder Kopiervorgang enthalten sollte. Diese Seite ist nur verfügbar, wenn Quelle und Ziel verschiedene Server sind. Wenn Sie ein Objekt einfügen möchten, klicken Sie im Feld **Verfügbare verbundene Objekte** auf den Objektnamen und dann auf die Schaltfläche **>>** , um das Objekt in das Feld **Ausgewählte verbundene Objekte** zu verschieben. Wenn Sie ein Objekt ausschließen möchten, klicken Sie im Feld **Ausgewählte verbundene Objekte** auf den Objektnamen und dann auf die Schaltfläche **<\<** , um das Objekt in das Feld **Verfügbare verbundene Objekte** zu verschieben. Standardmäßig werden alle Objekte aller ausgewählten Typen übertragen. Wenn Sie einzelne Objekte beliebiger Typen auswählen möchten, klicken Sie auf die Schaltfläche mit den drei Punkten (...) neben dem entsprechenden Objekttyp im Feld **Ausgewählte verbundene Objekte** . Dadurch wird ein Dialogfeld geöffnet, in dem Sie einzelne Objekte auswählen können.  
  
     **Anmeldungen (alle Anmeldungen zur Laufzeit)**  
     Schließt Anmeldungen in den Verschiebe- oder Kopiervorgang ein. Standardmäßig ausgewählt.  
  
     **Gespeicherte Prozeduren aus der master-Datenbank**  
     Schließt gespeicherte Prozeduren aus der **master** -Datenbank in den Verschiebungs- bzw. Kopiervorgang mit ein.  
  
    > [!NOTE]  
    >  Erweiterte gespeicherte Prozeduren und deren zugeordnete DLLs sind vom automatischen Kopieren ausgenommen.  
  
     **Aufträge des SQL Server-Agents**  
     Schließt Aufträge aus der **msdb** -Datenbank in den Verschiebungs- bzw. Kopiervorgang mit ein.  
  
     **Benutzerdefinierte Fehlermeldungen**  
     Schließt benutzerdefinierte Fehlermeldungen in den Verschiebungs- bzw. Kopiervorgang mit ein.  
  
     **Endpunkte**  
     Schließt in der Quelldatenbank definierte Endpunkte ein.  
  
     **Volltextkatalog**  
     Schließt Volltextkataloge aus der Quelldatenbank ein.  
  
     **SSIS-Paket**  
     Schließt in der Quelldatenbank definierte [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Pakete ein.  
  
     **Beschreibung**  
     Eine Beschreibung des -Objekts.  
  
8.  Geben Sie auf der Seite **Speicherort der Quelldatenbankdateien** eine Dateisystemfreigabe an, die die Datenbankdateien auf dem Quellserver enthält. Dies ist erforderlich, wenn sich die Quell- und Zielserverinstanzen auf anderen Computern befinden.  
  
     **Datenbank**  
     Zeigt die Namen der Datenbanken an, die verschoben werden.  
  
     **Speicherort des Ordners**  
     Geben Sie den Speicherort der Quelldatenbankdateien im Dateisystem an.  
  
     Zum Beispiel: C:\Program Files\Microsoft SQL Server\MSSQL110. MSSQLSERVER\MSSQL\DATA  
  
     **Dateifreigabe auf dem Quellserver**  
     Geben Sie den Speicherort der Quelldatenbankdateien als Pfad einer Dateifreigabe an.  
  
     Zum Beispiel: "\\\\*Server_name*\c$\Programme\Microsoft SQL Server\MSSQL110. MSSQLSERVER\MSSQL\Data  
  
9. Der Assistent zum Kopieren von Datenbanken erstellt ein [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paket, um die Datenbank von der Seite **Paket konfigurieren** zu übertragen. Sie können das Paket bei Bedarf anpassen.  
  
     **Paketspeicherort**  
     Zeigt an, wo das [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paket geschrieben wird.  
  
     **Paketname**  
     Geben Sie einen Namen für das [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paket ein.  
  
     **Protokollierungsoptionen**  
     Wählen Sie aus, ob die Protokollierungsinformationen im Windows-Ereignisprotokoll oder in einer Textdatei gespeichert werden sollen.  
  
     **Fehlerprotokollpfad**  
     Stellen Sie einen Pfad für den Speicherort der Protokolldatei bereit. Diese Option ist nur bei ausgewählter Option zum Protokollieren der Textdatei verfügbar.  
  
10. Geben Sie auf der Seite **Zeitplan für Paket** an, wann der Verschiebe- oder Kopiervorgang beginnen soll. Wenn Sie kein Systemadministrator sind, müssen Sie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Proxykonto angeben, das Zugriff auf das Subsystem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS)-Paketausführung hat.  
  
     **Run immediately**  
     Starten Sie den Verschiebe- bzw. Kopiervorgang, nachdem Sie auf **Weiter**geklickt haben.  
  
     **Zeitplan**  
     Startet den Verschiebe- bzw. Kopiervorgang später. Die aktuellen Einstellungen des Zeitplans werden im Feld Beschreibung angezeigt. Klicken Sie auf **Ändern**, um den Zeitplan zu ändern.  
  
     **Änderung**  
     Öffnet das Dialogfeld **Neuer Auftragszeitplan** .  
  
     **Integration Services-Proxykonto**  
     Wählen Sie ein verfügbares Proxykonto aus. Wenn Sie die Übertragung planen möchten, muss für den Benutzer mindestens ein Proxykonto verfügbar sein, das mit der Berechtigung für das Subsystem **SQL Server Integration Services-Paketausführung** konfiguriert ist.  
  
     Wenn Sie ein Proxykonto für die [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketausführung erstellen möchten, erweitern Sie im **Objekt-Explorer**den **SQL Server-Agent**, erweitern Sie **Proxys**, klicken Sie mit der rechten Maustaste auf **SSIS-Paketausführung**, und klicken Sie dann auf Neuer Proxy.  
  
     Mitglieder der festen Serverrolle **sysadmin** können das **SQL Server-Agent-Dienstkonto**auswählen, das über die erforderlichen Berechtigungen verfügt.  
  
11. Überprüfen Sie auf der Seite **Assistenten abschließen** die Zusammenfassung der aktivierten Optionen. Klicken Sie auf **Zurück** , um eine Option zu ändern. Klicken Sie auf **Fertig stellen** , um die Datenbank zu erstellen. Während der Übertragung werden die Statusinformationen zum Ausführen des **Assistenten zum Kopieren von Datenbanken** auf der Seite **Vorgang wird ausgeführt**überwacht.  
  
     **Aktion**  
     Listet jede Aktion auf, die ausgeführt wird.  
  
     **Status**  
     Gibt an, ob die Aktion insgesamt erfolgreich war oder fehlgeschlagen ist.  
  
     **MessageBox**  
     Stellt alle von jedem Schritt zurückgegebenen Meldungen bereit.  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Aktualisieren einer SQL Server-Datenbank  
 Nachdem Sie mithilfe des Assistenten zum Kopieren von Datenbanken eine Datenbank von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]aktualisiert haben, ist die Datenbank sofort verfügbar und wird automatisch aktualisiert. Wenn die Datenbank Volltextindizes aufweist, werden diese beim Upgrade entweder importiert, zurückgesetzt oder neu erstellt, je nach der Einstellung der Servereigenschaft **Volltextupgrade-Option** . Wenn die Upgradeoption auf **Importieren** oder **Neu erstellen**festgelegt ist, sind die Volltextindizes während des Upgrades nicht verfügbar. Je nach Menge der indizierten Daten kann der Importvorgang mehrere Stunden dauern; die Neuerstellung sogar bis zu zehnmal länger. Wenn die Upgradeoption auf **Importieren**festgelegt und kein Volltextkatalog verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt. Informationen zum Anzeigen oder Ändern der Einstellung der Eigenschaft **Volltextupgrade-Option** finden Sie unter [Verwalten und Überwachen der Volltextsuche auf einer Serverinstanz](../search/manage-and-monitor-full-text-search-for-a-server-instance.md).  
  
 War der Kompatibilitätsgrad einer Benutzerdatenbank vor dem Upgrade 100 oder höher, wird er nach dem Upgrade beibehalten. War der Kompatibilitätsgrad der aktualisierten Datenbank auf 90 festgelegt, wird er auf 100 erhöht, was dem niedrigsten unterstützten Kompatibilitätsgrad in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] entspricht. Weitere Informationen finden Sie unter [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren einer Datenbank durch Trennen und Anfügen &#40;Transact-SQL&#41;](upgrade-a-database-using-detach-and-attach-transact-sql.md)   
 [Erstellen eines Proxys für den SQL Server-Agent](../../ssms/agent/create-a-sql-server-agent-proxy.md)  
  
  
