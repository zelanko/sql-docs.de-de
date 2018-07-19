---
title: Erstellen und konfigurieren eine PowerPivot-Dienstanwendung in der Zentraladministration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b2e5693e-4af3-453f-83f3-07481ab1ac6a
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 13e41850c466a62c2e4e7ae07821e3ff96692cd2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263706"
---
# <a name="create-and-configure-a-powerpivot-service-application-in-central-administration"></a>Erstellen und Konfigurieren von PowerPivot-Dienstanwendungen in der Zentraladministration
  Eine PowerPivot-Dienstanwendung ist eine freigegebene Dienstinstanz des PowerPivot-Systemdiensts. Jede Dienstanwendung verfügt über eine eigene Anwendungsidentität, Konfigurationseinstellungen, Eigenschaften und einen internen Datenspeicher.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Bestimmen Sie, ob eine neue PowerPivot-Dienstanwendung erstellt.](#determine)  
  
 [Erstellen einer PowerPivot-Dienstanwendung](#CreateApp)  
  
 [Konfigurieren der PowerPivot-Dienstanwendung](#ConfigApp)  
  
 [Zuweisen einer PowerPivot-Dienstanwendung zu einer Webanwendung](#AssignGSA)  
  
 [Bearbeiten von Eigenschaften für Dienstanwendungen](#EditGSA)  
  
##  <a name="determine"></a> Bestimmen Sie, ob eine neue PowerPivot-Dienstanwendung erstellt.  
 Eine PowerPivot für SharePoint-Installation muss mindestens eine PowerPivot-Dienstanwendung in der Farm enthalten. Eine Dienstanwendung wird automatisch erstellt, wenn Sie das PowerPivot-Konfigurationstool zum Konfigurieren des Servers verwendet haben. Andernfalls müssen Sie in der Zentraladministration manuell eine PowerPivot-Dienstanwendung erstellen.  
  
 Beim Erstellen einer Dienstanwendung wird der Dienst verfügbar gemacht und die Datenbank der Dienstanwendung generiert. Abhängig von den beim Erstellen der Dienstanwendung ausgewählten Optionen wird der Standard-Dienstverbindungsgruppe eine PowerPivot-Dienstverbindung hinzugefügt. Alle SharePoint-Webanwendungen, die die Standard-Dienstverbindungsgruppe abonnieren, erhalten automatisch direkten Zugriff auf die PowerPivot-Dienstanwendung.  
  
 Sie können mehrere PowerPivot-Dienstanwendungen erstellen. Obwohl eine Dienstanwendung für die meisten Bereitstellungsszenarien ausreichend ist, kann die Erstellung einer zusätzlichen PowerPivot-Dienstanwendung in Betracht gezogen werden, falls folgende Unternehmensanforderungen bestehen:  
  
-   Verwenden unterschiedlicher Konten für unbeaufsichtigte PowerPivot-Datenaktualisierungen für jede Anwendung.  
  
-   Verwenden unterschiedlicher Timeouts, Verwendungsverläufe und Schwellenwerte für Abfrageantwortberichte.  
  
-   Delegieren der Dienstverwaltung an unterschiedliche Personen. Ein Administrator sieht den Datenaktualisierungsverlauf, die Verwendungsdaten und andere Eigenschaften nur für die Anwendung, die er verwaltet. Es kann erforderlich sein, SharePoint-Webanwendungen zu isolieren, z. B. wenn das Unternehmen ein Hostingdienst ist, der Datenisolation für die SharePoint-Webanwendungen garantieren muss, die unterschiedlichen Kunden gehören. In diesem Fall können Sie durch die Erstellung separater PowerPivot-Dienstanwendungen diese Isolationsanforderungen erfüllen. Stellen Sie dabei sicher, dass jeder Dienstadministrator nur die Konfigurationseinstellungen und die Eigenschaften für die Anwendung sieht, die er verwaltet.  
  
 Die Erstellung zusätzlicher Dienstanwendungen führt zu neuen Anforderungen beim Verwalten von Dienstzuordnungen. Sie müssen dann nämlich benutzerdefinierte Dienstzuordnungslisten für jede zusätzliche erstellte Dienstanwendung erstellen und verwenden.  
  
 Wenn kein bestimmter Grund für eine zusätzliche PowerPivot-Dienstanwendung vorliegt, sollten Sie eine einzige Dienstanwendung für alle Webanwendungen in der Farm verwenden.  
  
##  <a name="CreateApp"></a> Erstellen einer PowerPivot-Dienstanwendung  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie im Menüband **Dienstanwendungen** auf **Neu**.  
  
3.  Wählen Sie **SQL Server PowerPivot-Dienstanwendung**. Wenn dies nicht in der Liste angezeigt wird, wurde PowerPivot für SharePoint nicht installiert oder nicht ordnungsgemäß konfiguriert.  
  
4.  In der **erstellen neue PowerPivot-Dienstanwendung** Seite, geben Sie einen Namen für die Anwendung. Der Standardwert ist PowerPivotServiceApplication\<Anzahl >. Wenn Sie mehrere PowerPivot-Dienstanwendungen erstellen, hilft ein aussagekräftiger Name anderen Administratoren, den Verwendungszweck der Anwendung zu verstehen.  
  
5.  Erstellen Sie in Anwendungspool einen neuen Anwendungspool für die Anwendung (empfohlen). Wählen Sie ein verwaltetes Konto für den Anwendungspool aus, oder erstellen Sie es. Sie müssen ein Domänenbenutzerkonto angeben. Ein Domänenbenutzerkonto ermöglicht die Verwendung der in SharePoint verfügbaren Funktion Verwaltetes Konto, mit der Sie Kennwörter und Kontoinformationen zentral aktualisieren können. Domänenkonten sind auch erforderlich, wenn Sie beabsichtigen, die Bereitstellung auf zusätzlichen Dienstinstanzen, die unter der gleichen Identität ausgeführt werden, zu skalieren.  
  
6.  Der Standardwert unter **Datenbankserver**entspricht der SQL Server-Datenbank-Engine-Instanz, die die Konfigurationsdatenbanken der Farm hostet. Sie können diesen Server verwenden oder einen anderen SQL Server auswählen.  
  
7.  In **Datenbanknamen**, der Standardwert ist PowerPivotServiceApplication1_\<Guid >. Sie müssen eine eindeutige Datenbank für jede PowerPivot-Dienstanwendung erstellen. Der Standardname für die Datenbank entspricht dem Standardnamen der Dienstanwendung. Wenn Sie einen eindeutigen Dienstanwendungsnamen eingegeben haben, verwenden Sie eine ähnliche Benennungskonvention für den Datenbanknamen, damit Sie sie zusammen verwalten können.  
  
8.  Der Standardwert unter **Datenbankauthentifizierung**lautet Windows-Authentifizierung. Wenn Sie **SQL-Authentifizierung**auswählen, finden Sie im SharePoint-Administratorhandbuch bewährte Methoden zur Verwendung dieses Authentifizierungstyps in einer SharePoint-Bereitstellung.  
  
9. Wählen Sie optional das Kontrollkästchen für **Proxy für diese PowerPivot-Dienstanwendung zur Standardproxygruppe der Farm hinzufügen.** . Dadurch wird der Standard-Dienstverbindungsgruppe die Dienstanwendungsverbindung hinzugefügt.  
  
     Sie müssen dieses Kontrollkästchen aktivieren, wenn Sie die erste PowerPivot-Dienstanwendung erstellen. Es muss eine PowerPivot-dienstanwendung in der standardverbindungsgruppe in der Reihenfolge für PowerPivot-Management-Dashboard ordnungsgemäß funktioniert.  
  
     Fügen Sie der Standardverbindungsgruppe die PowerPivot-Dienstanwendung nicht hinzu, wenn bereits eine vorhanden ist. Das Hinzufügen mehrerer Einträge des gleichen Dienstanwendungstyps ist keine unterstützte Konfiguration und könnte Fehler verursachen. Wenn Sie zusätzliche Dienstanwendungen erstellen, nehmen Sie sie nicht in die Standardverbindungsgruppe auf. Fügen Sie sie stattdessen benutzerdefinierten Listen hinzu.  
  
     Weitere Informationen zu dienstzuordnungen finden Sie unter [Verbinden einer PowerPivot-Dienstanwendung zu einer SharePoint-Webanwendung in der Zentraladministration](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).  
  
10. Klicken Sie auf **OK.** Der Dienst wird zusammen mit anderen verwalteten Diensten in der Dienstanwendungsliste der Farm angezeigt.  
  
##  <a name="ConfigApp"></a> Konfigurieren von PowerPivot-Dienstanwendung  
 Eine PowerPivot-Dienstanwendung wird unter Verwendung einer Standardkonfiguration erstellt. Für die meisten Szenarien werden die Standardeinstellungen empfohlen. Sie sollten nur geändert werden, falls Antwortzeiten zu lang sind oder Verbindungen getrennt werden oder wenn Sie unterschiedliche PowerPivot-Dienstkonfigurationen für bestimmte SharePoint-Webanwendungen verwenden.  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
     In der Liste der Dienstanwendungen sollte die gerade erstellte und benannte Dienstanwendung angezeigt werden. Der Standardname ist **PowerPivotServiceApplication1**.  
  
2.  Klicken Sie auf die PowerPivot-Dienstanwendung. Dadurch wird das PowerPivot-Management-Dashboard geöffnet.  
  
3.  Klicken Sie in der Liste **Aktionen** oben rechts im Dashboard auf **Einstellungen für Dienstanwendung konfigurieren**.  
  
4.  In **Datenbanktimeout laden**, erhöhen oder verringern Sie den Wert ändern, wie lange der PowerPivot-Dienst auf eine Antwort aus der SQL Server Analysis Services (PowerPivot)-Instanz wartet, eine Anforderung zum Laden von Daten weitergeleitet. Da die Übertragung sehr großer Datasets einige Zeit dauern kann, müssen Sie genügend Zeit vorsehen, damit die PowerPivot-Dienstinstanz die Excel-Arbeitsmappe abrufen und die PowerPivot-Daten zur Abfrageverarbeitung in eine Analysis Services-Instanz verschieben kann. Da PowerPivot-Daten ungewöhnlich umfangreich sein können, ist der Standardwert 30 Minuten.  
  
5.  Erhöhen oder verringern Sie den Wert unter **Timeout für Verbindungspool**, um die Dauer in Minuten zu ändern, die eine Datenverbindung im Leerlauf geöffnet gehalten wird. Der Standardwert ist 30 Minuten. Während dieses Zeitraums wird der PowerPivot-Dienst über eine Datenverbindung im Leerlauf für schreibgeschützte Anforderungen vom gleichen SharePoint-Benutzer für dieselben PowerPivot-Daten wiederverwenden. Wenn im angegebenen Zeitraum keine weiteren Anforderungen für diese Daten empfangen werden, wird die Verbindung aus dem Pool entfernt. Gültige Werte reichen von 1 bis 3600 Sekunden. Weitere Informationen zu Verbindungspools finden Sie unter [Konfigurationseinstellungsverweis &#40;PowerPivot für SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md).  
  
6.  In **Maximalgröße für den Benutzerverbindungspool**, erhöhen oder verringern Sie den Wert aus, um die maximale Anzahl von Verbindungen im Leerlauf zu ändern, wird der PowerPivot-Dienst in einzelnen Verbindungspools für jeden SharePoint-Benutzer, PowerPivot-Datasets, erstellen, und versionskombinationen.  
  
     Der Standardwert ist 1.000 Verbindungen im Leerlauf. Gültige Werte sind -1 (unbegrenzt), 0 (deaktiviert das Pooling von Benutzerverbindungen) oder 1 bis 10.000.  
  
     Durch diese Verbindungspools kann der Dienst fortlaufende Verbindungen mit den gleichen schreibgeschützten Daten, die vom selben Benutzer hergestellt werden, effizienter unterstützen. Wenn Sie das Verbindungspooling deaktivieren, wird jede Verbindung erneut erstellt.  
  
     Beachten Sie, dass Änderungen am Grenzwert der Verbindungspoolgröße (auch die Festlegung auf 0) nicht dazu führen, dass Verbindungen getrennt werden. Verbindungspools sind vorhanden, um Wartezeiten beim Herstellen einer Datenverbindung zu reduzieren. Der PowerPivot-Dienst wird nie eine Verbindung aufgrund von Verbindungspooleinstellungen ablehnen.  
  
7.  In **maximale Administrative Größe des Serververbindungspools**, erhöhen oder verringern Sie den Wert zum Ändern der Anzahl der geöffneten Verbindungen in einem Verbindungspool, der für eine PowerPivot-dienstverbindung mit Analysis Services erstellt wurde. Jede PowerPivot-Dienstinstanz öffnet eine separate Administratorverbindung zur Analysis Services-Instanz auf demselben Computer. Der PowerPivot-Dienst erstellt einen separaten Pool, damit Administratorverbindungen wiederverwendet werden können, um Verbindungen im Leerlauf zu suchen und den Serverzustand zu überwachen. Der Standardwert ist 200 Verbindungen. Gültige Werte sind -1 (unbegrenzt), 0 (deaktiviert die Verwendung des Verwaltungsverbindungspools) oder 1 bis 10000. Wenn Sie 0 auswählen, wird jede Verbindung neu erstellt.  
  
8.  In **Zuordnungsmethode**, können Sie angeben, das Lastenausgleichsschema, die PowerPivot-Systemdienst verwendet, um eine bestimmte PowerPivot-dienstanwendung, für den Lastenausgleich einer ersten Anforderung auszuwählen. Die Standardeinstellung ist **Zustandsbasiert**, mit der Anforderungen auf Grundlage des Serverzustands zugeordnet werden, wie anhand des verfügbaren Arbeitsspeichers und der Prozessorauslastung ermittelt. Alternativ können Sie **Roundrobin** auswählen, um Anforderungen den Servern in der gleichen wiederholten Reihenfolge zuzuordnen, unabhängig davon, ob ein Server ausgelastet oder im Leerlauf ist.  
  
9. Unter Datenaktualisierung in **Geschäftszeiten**können Sie den Zeitraum angeben, der einen Geschäftstag definiert. Zeitpläne zur Datenaktualisierung können am Ende eines Geschäftstags ausgeführt werden, um die während der regulären Geschäftszeiten generierten Transaktionsdaten zu sammeln.  
  
10. In **unbeaufsichtigte Datenaktualisierungskonto PowerPivot**, Sie können angeben, dass eine vordefinierte Secure Store Service-Zielanwendung, die ein vordefiniertes Konto zum Ausführen von PowerPivot-datenaktualisierungsaufträgen speichert. Stellen Sie sicher, dass Sie den Namen der Zielanwendung und nicht die ID angeben. Die Zielanwendung für die unbeaufsichtigte Datenaktualisierung wird automatisch erstellt, wenn Sie die Option "Neuer Server" im SQL Server-Setup verwendet haben, um PowerPivot für SharePoint zu installieren. Andernfalls müssen Sie die Zielanwendung manuell erstellen. Anweisungen zum Konfigurieren des Kontos, finden Sie unter [konfigurieren Sie die PowerPivot-datenaktualisierungskonto &#40;PowerPivot für SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md).  
  
11. Unter **Benutzer dürfen benutzerdefinierte Windows-Anmeldeinformationen eingeben**können Sie das Kontrollkästchen aktivieren oder deaktivieren, um anzugeben, ob Zeitplanbesitzer beliebige Windows-Anmeldeinformationen für die Ausführung eines Datenaktualisierungszeitplans eingeben können. Wenn Sie dieses Kontrollkästchen aktivieren, erstellt und verwaltet die PowerPivot-Dienstanwendung eine Zielanwendung für jeden Satz gespeicherter Anmeldeinformationen. Weitere Informationen finden Sie unter [konfigurieren gespeicherter Anmeldeinformationen für die PowerPivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
12. Unter **Maximale Verarbeitungsverlaufslänge**können Sie angeben, wie lange ein Verlaufsdatensatz der Datenaktualisierungsverarbeitung beibehalten wird. Diese Informationen werden auf den Seiten für den Datenaktualisierungsverlauf angezeigt, die für jede Arbeitsmappe angelegt werden, die die Datenaktualisierung nutzt. Sie werden auch im PowerPivot-Management-Dashboard angezeigt.  
  
13. Geben Sie unter Sammlung von Verwendungsdaten in **Berichtsintervall für Abfragen**ein Zeitintervall an, in dem Abfragestatistiken gemeldet werden. Abfragestatistiken werden als einzelnes Ereignis gemeldet, um die Kommunikation zwischen den Servern zu minimieren.  
  
14. Geben Sie unter Verwendungsdatenverlauf an, wie lange ein Verlaufsdatensatz der Verwendungsdaten beibehalten wird. Die Verwendungsinformationen werden im PowerPivot-Management-Dashboard angezeigt. Die Berichte sind weniger effektiv, wenn Sie für den Verwendungsdatenverlauf einen zu niedrigen Wert angeben.  
  
15. Geben Sie unter Sammlung von Verwendungsdaten für jeden Abfrageantwort-Schwellenwert eine Obergrenze an, die bestimmt, wo eine Kategorie aufhört und die nächste beginnt. Durch diese Kategorien wird eine Basislinie festgelegt, auf deren Grundlage das Abfrageverhalten gemessen wird. Sie können diese Kategorien verwenden, um Trends in den Abfrageantwortzeiten Ihres Systems zu überwachen. Diese Informationen werden im PowerPivot-Management-Dashboard angezeigt.  
  
16. Klicken Sie auf **OK** , um die Änderungen zu speichern.  
  
     Änderungen am Timeout für Ladevorgänge oder an der Zuordnungsmethode werden nur auf neu eingehende Anforderungen angewendet. Für Anforderungen, die bereits ausgeführt werden, gelten die Werte, die beim Empfang der Anforderung gültig waren.  
  
##  <a name="AssignGSA"></a> Zuweisen einer PowerPivot-Dienstanwendung zu einer Webanwendung  
 Nachdem Sie eine PowerPivot-Dienstanwendung konfiguriert haben, können Sie sie einer Webanwendung zuweisen, indem Sie sie der Liste der Dienstanwendungsverbindungen für die jeweilige Webanwendung hinzufügen. Hierfür gibt es zwei Möglichkeiten:  
  
-   Fügen Sie die Anwendung der **Standardverbindungsgruppe** hinzu. Die *Standardverbindungsgruppe* ist eine Sammlung von Dienstanwendungsverbindungen, die jeder Webanwendung zur Verfügung stehen, die darauf verweist. Sie müssen dieser Liste eine PowerPivot-Dienstanwendung hinzufügen.  
  
-   Erstellen Sie für eine bestimmte Webanwendung eine **benutzerdefinierte** Verbindungsliste. Wenn Sie mehrere PowerPivot-Dienstanwendungen erstellt haben, können Sie die zu verwendende Anwendung aus einer benutzerdefinierten Liste auswählen.  
  
 Die Standardverbindungsgruppe kann mehr als eine Dienstanwendung des gleichen Typs enthalten. Beachten Sie jedoch, dass das Hinzufügen von mehr als einer PowerPivot-Dienstanwendung zu dieser Liste keine unterstützte Konfiguration ist.  
  
1.  Klicken Sie in der Zentraladministration unter **Anwendungsverwaltung**auf **Webanwendungen verwalten**.  
  
2.  Wählen Sie die Anwendung aus, für die Sie eine Verbindung zuweisen möchten (z. B. SharePoint -80).  
  
3.  Klicken Sie auf **Dienstverbindungen**.  
  
4.  Wählen Sie unter **Folgende Zuordnungsgruppe bearbeiten**entweder **default** oder **[custom]** aus.  
  
5.  Aktivieren Sie für **[custom]** das Kontrollkästchen neben jeder Dienstanwendungsverbindung, die Sie verwenden möchten. Wenn Sie mehrere PowerPivot-dienstanwendungen verfügen (angegeben durch den Typ `PowerPivot Service Application Proxy`), achten Sie darauf, nur eine auszuwählen.  
  
6.  Klicken Sie auf **OK**.  
  
##  <a name="EditGSA"></a> Bearbeiten von Eigenschaften für Dienstanwendungen  
 Verwenden Sie die folgenden Anweisungen, um die Eigenschaftenseite erneut zu öffnen, die den Dienstanwendungsnamen, den Anwendungspool sowie die Datenbankeinstellungen und Dienstzuordnungen enthält.  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Wählen Sie die PowerPivot-Dienstanwendung aus, aber klicken Sie nicht darauf. Sie können auf den Typnamen klicken, um die gesamte Zeile auszuwählen.  
  
3.  Klicken Sie im Menüband auf **Eigenschaften** .  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Serververwaltung und -konfiguration in der Zentraladministration](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
