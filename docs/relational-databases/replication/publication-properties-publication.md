---
title: Dialogfeld „Veröffentlichungseigenschaften“ für die SQL Server-Replikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.agentsecurity.f1
- sql13.rep.newpubwizard.pubproperties.agentsecurity.f1
- sql13.rep.newpubwizard.pubproperties.filterrows.f1
- sql13.rep.newpubwizard.pubproperties.internetsynchronization.f1
- sql13.rep.newpubwizard.pubproperties.general.f1
- sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1
- sql13.rep.newpubwizard.pubproperties.snapshotformat.f1
helpviewer_keywords:
- Publication Properties dialog box
ms.assetid: 66e845e9-1308-4288-9110-ad2f22f1fc58
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: da86b20dba26536626010d14c1f81a1bbd852156
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65620369"
---
# <a name="sql-server-replication-publication-properties--dialog-box"></a>Dialogfeld „Veröffentlichungseigenschaften“ für die SQL Server-Replikation
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Auf dieser Seite werden die Seiten im Dialogfeld „Veröffentlichungseigenschaften“ beschrieben. 

## <a name="general"></a>Allgemein
 Auf der Seite **Allgemein** des Dialogfelds **Veröffentlichungseigenschaften** sind grundlegende Informationen wie Name, Beschreibung und Abonnementablaufrichtlinie der Veröffentlichung enthalten  
  
### <a name="options"></a>enthalten  
 **Name**  
 Der Name der Veröffentlichung (schreibgeschützt).  
  
 **Datenbank**  
 Der Name der Veröffentlichungsdatenbank (schreibgeschützt).  
  
 **Beschreibung**  
 Die Beschreibung der Veröffentlichung.  
  
 **Typ**  
 Der Typ der Veröffentlichung (schreibgeschützt).  
  
 **Abonnementablauf**  
 Wählen Sie eine der Ablaufoptionen für das Abonnement aus: **Subscriptions never expire** (Abonnements laufen nie ab) oder **Subscriptions expire** (Abonnements laufen ab) mit einem festen Zeitraum (**Intervall**).  
  
 Bei Momentaufnahme- und Transaktionsveröffentlichungen empfiehlt [!INCLUDE[msCoName](../../includes/msconame-md.md)] , die Standardeinstellung **Abonnements laufen nie ab**zu übernehmen.  
  
 Bei Mergereplikationen empfiehlt [!INCLUDE[msCoName](../../includes/msconame-md.md)] , die Standardeinstellung **Abonnements laufen ab** zu übernehmen und einen möglichst niedrigen Wert für **Intervall**festzulegen. Je länger der Ablaufzeitraum des Abonnements ist, desto mehr Metadaten werden auch gespeichert, was sich nachteilig auf die Leistung auswirken kann. Wägen Sie die Notwendigkeit, die Verbindung mit Abonnenten zu trennen oder diese über einen längeren Zeitraum nicht zu synchronisieren, gegen die Leistungsprobleme ab, die das Speichern und Verarbeiten großer Datenmengen nach sich ziehen kann.  
  
 Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Kompatibilitätsgrad**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher; nur für Mergeveröffentlichungen. Wählen Sie die niedrigste [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version aus, die für Abonnenten, die mit dieser Veröffentlichung synchronisiert werden, erforderlich ist. Für die Bestimmung des Kompatibilitätsgrades gibt es eine Reihe von Regeln.  

## <a name="filter-rows"></a>Zeilen filtern
  Mithilfe der Seite **Filterzeilen** des Dialogfelds **Veröffentlichungseigenschaften** können Sie Elemente hinzufügen, bearbeiten oder löschen:  
  
-   Statische Zeilenfilter auf Tabellenartikel in Momentaufnahme-, Transaktions- und Mergeveröffentlichungen anwenden   
-   Parametrisierte Zeilenfilter auf Tabellenartikel in Mergeveröffentlichungen anwenden    
-   Joinfilter verwenden, um Filter für Mergetabellenartikel auf verwandte Tabellenartikel zu erweitern Weitere Informationen zu Filteroptionen finden Sie unter [Filtern von veröffentlichten Daten](../../relational-databases/replication/publish/filter-published-data.md).  
  
> [!NOTE]  
>  Für das Hinzufügen, Bearbeiten oder Löschen eines Filters ist für die Veröffentlichung eine neue Momentaufnahme erforderlich. Darüber hinaus müssen alle Abonnements erneut initialisiert werden.  
  
Wenn Sie die optimale Leistung Ihrer Anwendung sicherstellen und den am Remotestandort benötigten Speicherplatz verringern möchten, oder wenn Sie die Verfügbarkeit bestimmter Daten für bestimmte Abonnenten beschränken möchten, sollten Sie nur die erforderlichen Daten veröffentlichen. Die Veröffentlichung kann sowohl ungefilterte als auch gefilterte Tabellen einschließen. Beispielsweise könnten Sie die vollständige (ungefilterte) Tabelle der Firmenprodukte einschließen und Zeilenfilter verwenden, um eine gefilterte Tabelle der Kunden aus einer bestimmten Region anzugeben. Das Filtern von veröffentlichten Daten bietet folgende Möglichkeiten:  
  
-   Minimieren der über das Netzwerk gesendeten Datenmenge.    
-   Reduzieren des erforderlichen Speicherplatzes beim Abonnenten.    
-   Anpassen von Veröffentlichungen und Anwendungen an die individuellen Anforderungen des Abonnenten.    
-   Vermeiden oder Reduzieren von Konflikten beim Aktualisieren von Daten durch Abonnenten, da unterschiedliche Datenpartitionen an verschiedene Abonnenten gesendet werden können (es ist nicht möglich, dass mehrere Abonnenten dieselben Datenwerte aktualisieren).    
-   Vermeiden der Übertragung vertraulicher Daten. Mithilfe von Zeilenfiltern und Spaltenfiltern kann der Datenzugriff für Abonnenten eingeschränkt werden. Im Fall von Mergereplikationen gelten besondere Sicherheitsüberlegungen, wenn Sie einen parametrisierten Filter verwenden, der HOST_NAME() einschließt. Weitere Informationen finden Sie im Abschnitt über das Filtern mit HOST_NAME() unter [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
### <a name="options"></a>enthalten  
 **Gefilterte Tabellen**  
 Dieser Bereich wird mit Filtern aufgefüllt, während Sie den Tabellenartikeln in der Veröffentlichung Filter hinzufügen. Tabellen mit Zeilenfiltern werden im Bereich als Knoten der obersten Ebene angezeigt. Für Mergeveröffentlichungen werden Tabellen, auf die das Filtern durch einen Joinfilter erweitert wurde, als untergeordnete Knoten angezeigt.  
  
 **Hinzufügen**  
 Klicken Sie auf **Hinzufügen** , um ein Dialogfeld aufzurufen, mit dem Sie Tabellenartikel filtern können. Wenn Sie für eine Momentaufnahme- oder Transaktionsveröffentlichung auf **Hinzufügen** klicken, wird sofort ein Dialogfeld geöffnet. Wenn Sie für eine Mergeveröffentlichung auf **Hinzufügen** klicken, werden drei Auswahlmöglichkeiten angezeigt: **Filter hinzufügen**, **Add Join to Extend the Selected Filter** (Join zum Erweitern des ausgewählten Filters hinzufügen) und **Filter automatisch generieren**.  
  
-   Wählen Sie **Filter hinzufügen** aus, um das Dialogfeld **Filter hinzufügen** aufzurufen. Mithilfe dieses Dialogfelds können Sie Zeilenfilter auf einen Tabellenartikel anwenden. Im Dialogfeld **Filter hinzufügen** können Sie beispielsweise angeben, dass eine Tabelle mit Kundendaten nur Daten von französischen Kunden enthalten soll, wenn eine Replikation an Abonnenten erfolgt.  
  
-   Wählen Sie **Join hinzufügen, um den ausgewählten Filter zu erweitern** , um das Dialogfeld **Join hinzufügen** aufzurufen. Mithilfe des Dialogfelds **Join hinzufügen** können Sie einen Zeilenfilter so erweitern, dass Daten in Tabellen gefiltert werden, die mit der den Zeilenfilter enthaltenden Tabelle verbunden sind. Wenn beispielsweise eine Kundentabelle so gefiltert wird, dass sie nur Daten zu französischen Kunden enthält und eine verbundene Tabelle für Kundenbestellungen vorhanden ist, können Sie einen Join dieser beiden Tabellen definieren, damit die Bestelltabelle nur Bestellungen von französischen Kunden enthält.  
  
    > [!NOTE]  
    >  Diese Option ist nur verfügbar, wenn Sie im Filterbereich zunächst die Basistabelle des Joins ausgewählt haben.  
  
-   Wählen Sie **Filter automatisch generieren** aus, um das Dialogfeld **Filter generieren** aufzurufen. Mithilfe dieses Dialogfelds können Sie einen Zeilenfilter für eine Tabelle in einer Mergeveröffentlichung definieren, durch die die Replikation automatisch auf andere Tabellen erweitert wird, die durch Fremdschlüsselbeziehungen verbunden sind. Eine Veröffentlichung könnte beispielsweise drei Tabellen enthalten: eine Kundentabelle, eine Bestelltabelle (mit einem Fremdschlüssel zur Kundentabelle) und eine Tabelle mit den Bestellungsdetails (mit einem Fremdschlüssel zur Bestelltabelle). Wenn Sie einen Zeilenfilter für die Kundentabelle definieren, wird die Replikation auf die anderen Tabellen erweitert.  
  
    > [!NOTE]  
    >  Werden Filter durch die Replikation automatisch generiert, werden für die Veröffentlichung vorhandene Filter gelöscht. Wenn Sie sowohl automatisch generierte wie auch manuell angegebene Filter einschließen möchten, müssen Sie zunächst Filter generieren. Sie können für jede Veröffentlichung nur einen Satz automatisch generierter Filter angeben.  
  
 **Bearbeiten**  
 Wählen Sie im Filterbereich einen Zeilenfilter oder einen Joinfilter aus, und klicken Sie auf **Bearbeiten** , um das Dialogfeld **Filter bearbeiten** oder **Join bearbeiten** aufzurufen.  
  
 **Löschen**  
 Wählen Sie im Filterbereich einen Zeilenfilter oder einen Joinfilter aus, und klicken Sie auf **Löschen** , um den Filter zu löschen.  
  
 **Tabelle suchen**  
 Nur Mergeveröffentlichungen. Klicken Sie auf **Tabelle suchen** , um eine Tabelle in einer komplexen Filterstruktur zu suchen. In einer Datenbank mit komplexen Beziehungen kann eine Tabelle mit mehreren Tabellen verknüpft sein. Deshalb kann sie in der Filterstruktur mehrmals angezeigt werden.  
  
 Die eigentliche Tabelle wird in der Struktur nur einmal angezeigt. An den übrigen Stellen wird die Tabelle durch eine Verknüpfung dargestellt. Bei einer Verknüpfung mit einer Tabelle handelt es sich nur um einen Verweis auf die Tabelle. Es werden keine untergeordneten Knoten der Tabelle angezeigt. Ein Verknüpfungsknoten ist mit einem Verknüpfungspfeil markiert. Wenn Sie den Knoten erweitern, wird der Text **Klicken Sie auf „Tabelle suchen“, um die Tabelle für \<Tabellenname> anzuzeigen** angezeigt.  
  
 Wählen Sie im Bereich einen Verknüpfungsknoten aus, und klicken Sie auf **Tabelle suchen** . Der Bereich wird erweitert, und die Tabelle wird hervorgehoben. Wenn Sie auf **Tabelle suchen** klicken, ohne dass ein Verknüpfungsknoten ausgewählt wurde, wird ein Dialogfeld **Tabelle suchen** aufgerufen.  
  
 **Filter**  
 Enthält die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Definition für die im Filterbereich ausgewählten Filter.  

## <a name="publication-access-list"></a>Veröffentlichungszugriffsliste
  Auf der Seite **Veröffentlichungszugriffsliste** im Dialogfeld **Veröffentlichungseigenschaften** können Sie Anmeldungen, Konten und Gruppen zur Veröffentlichungszugriffsliste (PAL) hinzufügen und aus ihr entfernen. Die PAL ist der primäre Mechanismus für die Sicherung der Verleger. Wenn Sie eine Veröffentlichung erstellen, wird von der Replikation eine PAL für diese Veröffentlichung erstellt. Die PAL, deren Funktionen denen einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Zugriffskontrollliste ähneln, enthält eine Liste von Anmeldungen, Konten und Gruppen, denen die Berechtigung zum Zugriff auf die Veröffentlichung erteilt wurde.  
  
 Wenn ein Abonnent eine Verbindung mit dem Verleger oder Verteiler herstellt und den Zugriff auf eine Veröffentlichung anfordert, wird die Anmeldung des Abonnenten mit den Authentifizierungsinformationen in der PAL verglichen. Dadurch wird zusätzliche Sicherheit für den Verleger erreicht, da die Anmeldung bei Verleger und Verteiler vor einer Verwendung durch ein Clienttool geschützt ist, das direkt beim Verleger Änderungen ausführen könnte. Weitere Informationen finden Sie unter [Sichern des Verlegers](../../relational-databases/replication/security/secure-the-publisher.md).  
  
### <a name="options"></a>enthalten  
 **Hinzufügen**  
 Fügen Sie der Liste einen neuen Eintrag hinzu. Nur Benutzer-, Konto- und Gruppennamen, die bereits sowohl auf dem Verleger als auch dem Verteiler definiert sind, können hinzugefügt werden. Sie sind auf beiden Servern definiert, wenn Domänenkonten verwendet werden oder lokale Konten auf beiden Servern erstellt wurden.  
  
 **Entfernen**  
 Entfernen Sie den ausgewählten Eintrag aus der Liste.  
  
 **Alle entfernen**  
 Entfernen Sie alle Einträge aus der Liste.  

## <a name="ftp-snapshot-and-internet"></a>FTP-Momentaufnahme und Internet

-   Legen Sie Eigenschaften für die Übermittlung der Momentaufnahme mittels FTP (File Transfer Protocol) fest. Weitere Informationen finden Sie unter [Übermitteln einer Momentaufnahme über FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md). Sie müssen einen FTP-Server einrichten, um FTP für die Momentaufnahmeübermittlung verwenden zu können. Weitere Informationen finden Sie in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Dokumentation.  
  
    > [!NOTE]  
    >  Bei jeder Änderung an den FTP-Einstellungen muss eine neue Momentaufnahme erstellt werden.  
  
-   Festlegen von Eigenschaften zur Websynchronisierung für Mergereplikationen unter [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen. Dies ermöglicht die Synchronisierung von Abonnements über HTTPS (Secure Hypertext Transfer Protocol). Für die Verwendung der Websynchronisierung müssen Sie einen [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS-Server (Internetinformationsdienste) konfigurieren. Weitere Informationen finden Sie unter [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
### <a name="options"></a>enthalten  
 **Auf Momentaufnahmedateien über FTP zugreifen**  
 Wählen Sie die Option **Abonnenten das Herunterladen von Momentaufnahmedateien über FTP (File Transfer Protocol) ermöglichen**aus, und geben Sie Werte für **FTP-Servername**, **Portnummer**, **Pfad des FTP-Stammordners**, **Anmeldename**und **Kennwort**an, damit Momentaufnahmen von den Abonnenten über FTP übermittelt werden können.  
  
 Mithilfe dieser Option können Abonnenten selbst entscheiden, ob sie Momentaufnahmedateien über FTP abrufen möchten. Wenn diese Option ausgewählt ist, kann der Abonnent im Assistenten für neue Abonnements Momentaufnahmedateien standardmäßig über FTP abrufen. Sie können diese Einstellung im Dialogfeld **Abonnementeigenschaften** ändern. Wenn Sie Abonnenten die Möglichkeit einräumen, über FTP auf die Momentaufnahmedateien zuzugreifen, geben Sie auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften** den FTP-Ordner als Speicherort für Momentaufnahmedateien an. Diese Einstellung hat zur Folge, dass der Momentaufnahme-Agent die Dateien im FTP-Ordner automatisch aktualisiert, sobald eine neuer Momentaufnahme generiert wird. Wenn als Speicherort nicht der FTP-Ordner festgelegt ist, müssen Sie die Dateien beim Generieren neuer Momentaufnahmen manuell aktualisieren. Weitere Informationen finden Sie unter [Übermitteln einer Momentaufnahme über FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
 **Websynchronisierung**  
 Nur für Mergereplikationen zulässig. Wählen Sie die Option **Abonnenten das Synchronisieren durch Herstellen einer Verbindung mit einem Webserver ermöglichen**aus, und geben Sie eine Webserveradresse an, damit Mergeabonnenten die Websynchronisierung verwenden können. Der Webserver muss Secure Sockets Layer (SSL) verwenden, und die Webadresse muss wie `https://server.domain.com/synchronize` vollqualifiziert sein. Weitere Informationen finden Sie unter [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  


## <a name="agent-security"></a>Agent-Sicherheit
  Mithilfe der Seite **Agentsicherheit** des Dialogfelds **Veröffentlichungseigenschaften** können Sie auf die Eigenschaften für die Konten zugreifen, unter denen die folgenden Agents ausgeführt werden und Verbindungen mit Computern in einer Replikationstopologie herstellen:  
  
-   Der Momentaufnahme-Agent für alle Veröffentlichungen.  
  
-   Der Protokolllese-Agent für alle Transaktionsveröffentlichungen. Es gibt einen Protokolllese-Agent für jede Datenbank, die zur Transaktionsreplikation veröffentlicht wird. Das Ändern der Einstellungen des Protokolllese-Agents betrifft alle Transaktionsveröffentlichungen in einer Datenbank.  
  
-   Der Warteschlangenlese-Agent für Transaktionsveröffentlichungen, die Abonnements mit verzögertem Update über eine Warteschlange gestatten. Es gibt einen Warteschlangenlese-Agent für jede Verteilungsdatenbank. Das Ändern der Einstellungen für den Warteschlangenlese-Agent betrifft alle Transaktionsveröffentlichungen mit Abonnements mit verzögertem Update über eine Warteschlange, die dieselbe Verteilungsdatenbank verwenden. Weitere Informationen zu den Sicherheitseinstellungen des Warteschlangenlese-Agents finden Sie unter [Anzeigen und Ändern von Replikationssicherheitseinstellungen](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Weitere Informationen zu den für die einzelnen Agents erforderlichen Sicherheitseinstellungen und Berechtigungen finden Sie unter [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
### <a name="options"></a>enthalten  
 **Sicherheitseinstellungen** oder **Agent erstellen**  
 Klicken Sie, nachdem ein Agentauftrag erstellt wurde, auf **Sicherheitseinstellungen** , um auf ein Dialogfeld zuzugreifen, das Ihnen das Ändern der Sicherheitseinstellungen für einen Agent ermöglicht. Wenn kein Agentauftrag erstellt wurde, klicken Sie zum Erstellen eines Agentauftrags auf **Agent erstellen** , und geben Sie die Sicherheitseinstellungen an.  

## <a name="data-partitions"></a>Datenpartitionen
Datenpartitionen  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]  
  Mithilfe der Seite **Datenpartitionen** des Dialogfelds **Veröffentlichungseigenschaften** können Sie Datenpartitionen für Mergeveröffentlichungen mit parametrisierter Filterung definieren. Nach dem Definieren von Partitionen können Sie Momentaufnahmen für diese Partitionen generieren und verschiedenen Abonnenten auf der Grundlage ihrer Verbindungseigenschaften (Anmelde- und Computername) verschiedene Anfangsdatasets zur Verfügung stellen. Sie können es Abonnenten auch ermöglichen, die Übermittlung und das Generieren von Momentaufnahmen anzufordern, wenn für ihre Partition zum Zeitpunkt der ersten Synchronisierung keine Momentaufnahme verfügbar ist. Weitere Informationen finden Sie unter [Erstellen einer Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
### <a name="options"></a>enthalten  
 **Hinzufügen**  
 Klicken Sie auf **Hinzufügen** , um eine Partition zu definieren. Geben Sie im Dialogfeld **Datenpartition hinzufügen** Werte für **HOST_NAME()** und/oder **SUSER_SNAME()** an, und definieren Sie einen Zeitplan zum Aktualisieren von Momentaufnahmen.  
  
 **Bearbeiten**  
 Wählen Sie im Raster eine vorhandene Partition aus, und klicken Sie auf **Bearbeiten** , um die Partition zu bearbeiten.  
  
 **Löschen**  
 Wählen Sie im Raster eine vorhandene Partition aus, und klicken Sie auf **Löschen** , um die Partition zu löschen.  
  
 **Die ausgewählten Momentaufnahmen jetzt generieren**  
 Wählen Sie im Raster eine oder mehrere Partitionen aus, und klicken Sie auf **Die ausgewählten Momentaufnahmen jetzt generieren** , um Momentaufnahmen für diese Partitionen zu generieren.  
  
 **Cleanup der vorhandenen Momentaufnahmen durchführen**  
 Wählen Sie im Raster eine oder mehrere Partitionen aus, und klicken Sie auf **Cleanup der vorhandenen Momentaufnahmen durchführen** , um einen Cleanup der Momentaufnahmen für diese Partitionen durchzuführen.  
  
 **Bei Bedarf automatisch eine Partition definieren und eine Momentaufnahme generieren, wenn ein neuer Abonnent zu synchronisieren versucht**  
 Wählen Sie diese Option aus, wenn Sie es Abonnenten ermöglichen möchten, das Generieren und die Anwendung von Momentaufnahmen anzufordern. Abonnenten benötigen diese Option möglicherweise, wenn zum Zeitpunkt der ersten Synchronisierung keine Momentaufnahme für ihre Partition verfügbar ist.  

## <a name="snapshot"></a>Momentaufnahme
Momentaufnahme  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]  
  Mithilfe der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften** können Sie das Momentaufnahmeformat, den Speicherort des Momentaufnahmeordners und Skripts, die vor und nach der Anwendung der Momentaufnahme ausgeführt werden, festlegen. Der Momentaufnahmeordner muss als Freigabe definiert sein und über ausreichend Berechtigungen verfügen, sodass Agents Dateien im Ordner lesen und schreiben können. Weitere Informationen zum angemessenen Sichern des Ordners finden Sie unter [Sichern des Momentaufnahmeordners](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
> [!NOTE]  
>  Änderungen erfordern eine neue Momentaufnahme für die Veröffentlichung. Weitere Informationen finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
### <a name="options"></a>enthalten  
 **Momentaufnahmeformat**  
 Wählen Sie für das Momentaufnahmeformat den einheitlichen Modus oder den Zeichenmodus aus.  
  
-   Wählen Sie **Systemeigenes Format von SQL Server - alle Abonnenten müssen Server mit SQL Server sein** aus, wenn alle Abonnenten andere Instanzen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind als [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Das systemeigene Momentaufnahmeformat bietet die beste Leistung.    
-   Wählen Sie **Zeichen - erforderlich, wenn auf einem Verleger oder Abonnenten SQL Server nicht ausgeführt wird** aus, wenn Abonnenten [!INCLUDE[ssEW](../../includes/ssew-md.md)] ausführen oder es sich um Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnenten handelt.    
 **Speicherort der Momentaufnahmedateien**  
 Wählen Sie den Speicherort zum Speichern der Momentaufnahmedateien aus. Die Dateien können am Standardspeicherort gespeichert werden; Sie können jedoch auch an einem alternativen Speicherort statt dem oder zusätzlich zum Standardspeicherort gespeichert werden. An einem alternativen Speicherort gespeicherte Dateien können komprimiert werden.  
  
-   Wählen Sie **Dateien im Standardordner speichern** aus, um für den Verleger den Standard-Momentaufnahmeordner zu verwenden. Der Speicherort des Momentaufnahmeordners ist in diesem Dialogfeld schreibgeschützt, da er für den Verleger nur im Dialogfeld **Verteilereigenschaften** geändert werden kann. Weitere Informationen finden Sie unter [Modify snapshot properties (Ändern von Momentaufnahmeeigenschaften)](../../relational-databases/replication/snapshot-options.md).    
-   Wählen Sie **Dateien im folgenden Ordner speichern** aus, um anstelle des Standardspeicherorts oder zusätzlich dazu einen alternativen Speicherort anzugeben. Geben Sie in das Textfeld einen Pfad ein, oder klicken Sie auf **Durchsuchen** , und navigieren Sie zu einem Speicherort. Wählen Sie **Momentaufnahmedateien in diesem Ordner komprimieren** aus, um die Dateien am alternativen Momentaufnahmespeicherort zu komprimieren. Der alternative Speicherort kann sich auf einem anderen Server, auf einem Netzlaufwerk oder auf Wechselmedien befinden, z. B. auf CD-ROM oder auf einem Wechseldatenträger. Weitere Informationen finden Sie unter [Modify snapshot properties (Ändern von Momentaufnahmeeigenschaften)](../../relational-databases/replication/snapshot-options.md).  
  
 **Weitere Skripts ausführen**  
 Geben Sie Skripts an, die vor oder nach dem Anwenden der Momentaufnahme auf dem Abonnenten ausgeführt werden. Skripts können nicht angegeben werden, wenn für **Momentaufnahmeformat** die Option **Zeichen**festgelegt wurde.  
  
 Skripts sind optional. Sie stellen jedoch eine benutzerfreundliche Möglichkeit dar, Befehle auszuführen und administrative Änderungen auf Abonnenten anzuwenden. Weitere Informationen zum Ausführen von Skripts finden Sie unter [Ausführen von Skripts vor und nach dem Anwenden der Momentaufnahme](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).  
  
-   Geben Sie in das Textfeld **Dieses Skript vor Anwenden der Momentaufnahme ausführen** einen Pfad ein, oder klicken Sie auf **Durchsuchen** , um einen Speicherort für das Skript anzugeben.    
-   Geben Sie in das Textfeld **Dieses Skript nach Anwenden der Momntaufnahme ausführen** einen Pfad ein, oder klicken Sie auf **Durchsuchen** , um einen Speicherort für das Skript anzugeben. 
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   

  
  
