---
title: Erstellen und Konfigurieren einer Power Pivot-Dienst Anwendung in der zentral Administration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b2e5693e-4af3-453f-83f3-07481ab1ac6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 64997cb3db784ea78a72a7c812c8f88034c2358d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66071575"
---
# <a name="create-and-configure-a-powerpivot-service-application-in-central-administration"></a>Erstellen und Konfigurieren von PowerPivot-Dienstanwendungen in der Zentraladministration
  Eine PowerPivot-Dienstanwendung ist eine freigegebene Dienstinstanz des PowerPivot-Systemdiensts. Jede Dienstanwendung verfügt über eine eigene Anwendungsidentität, Konfigurationseinstellungen, Eigenschaften und einen internen Datenspeicher.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Bestimmen, ob eine neue PowerPivot-Dienstanwendung erstellt werden muss](#determine)  
  
 [Erstellen einer Power Pivot-Dienst Anwendung](#CreateApp)  
  
 [Konfigurieren der PowerPivot-Dienstanwendung](#ConfigApp)  
  
 [Zuweisen einer Power Pivot-Dienst Anwendung zu einer Webanwendung](#AssignGSA)  
  
 [Bearbeiten von Eigenschaften der Dienst Anwendung](#EditGSA)  
  
##  <a name="determine-whether-to-create-a-new-powerpivot-service-application"></a><a name="determine"></a>Bestimmen, ob eine neue Power Pivot-Dienst Anwendung erstellt werden soll  
 Eine PowerPivot für SharePoint-Installation muss mindestens eine PowerPivot-Dienstanwendung in der Farm enthalten. Eine Dienstanwendung wird automatisch erstellt, wenn Sie das PowerPivot-Konfigurationstool zum Konfigurieren des Servers verwendet haben. Andernfalls müssen Sie in der Zentraladministration manuell eine PowerPivot-Dienstanwendung erstellen.  
  
 Beim Erstellen einer Dienstanwendung wird der Dienst verfügbar gemacht und die Datenbank der Dienstanwendung generiert. Abhängig von den beim Erstellen der Dienstanwendung ausgewählten Optionen wird der Standard-Dienstverbindungsgruppe eine PowerPivot-Dienstverbindung hinzugefügt. Alle SharePoint-Webanwendungen, die die Standard-Dienstverbindungsgruppe abonnieren, erhalten automatisch direkten Zugriff auf die PowerPivot-Dienstanwendung.  
  
 Sie können mehrere PowerPivot-Dienstanwendungen erstellen. Obwohl eine Dienstanwendung für die meisten Bereitstellungsszenarien ausreichend ist, kann die Erstellung einer zusätzlichen PowerPivot-Dienstanwendung in Betracht gezogen werden, falls folgende Unternehmensanforderungen bestehen:  
  
-   Verwenden unterschiedlicher Konten für unbeaufsichtigte PowerPivot-Datenaktualisierungen für jede Anwendung.  
  
-   Verwenden unterschiedlicher Timeouts, Verwendungsverläufe und Schwellenwerte für Abfrageantwortberichte.  
  
-   Delegieren der Dienstverwaltung an unterschiedliche Personen. Ein Administrator sieht den Datenaktualisierungsverlauf, die Verwendungsdaten und andere Eigenschaften nur für die Anwendung, die er verwaltet. Es kann erforderlich sein, SharePoint-Webanwendungen zu isolieren, z. B. wenn das Unternehmen ein Hostingdienst ist, der Datenisolation für die SharePoint-Webanwendungen garantieren muss, die unterschiedlichen Kunden gehören. In diesem Fall können Sie durch die Erstellung separater PowerPivot-Dienstanwendungen diese Isolationsanforderungen erfüllen. Stellen Sie dabei sicher, dass jeder Dienstadministrator nur die Konfigurationseinstellungen und die Eigenschaften für die Anwendung sieht, die er verwaltet.  
  
 Die Erstellung zusätzlicher Dienstanwendungen führt zu neuen Anforderungen beim Verwalten von Dienstzuordnungen. Sie müssen dann nämlich benutzerdefinierte Dienstzuordnungslisten für jede zusätzliche erstellte Dienstanwendung erstellen und verwenden.  
  
 Wenn kein bestimmter Grund für eine zusätzliche PowerPivot-Dienstanwendung vorliegt, sollten Sie eine einzige Dienstanwendung für alle Webanwendungen in der Farm verwenden.  
  
##  <a name="create-a-powerpivot-service-application"></a><a name="CreateApp"></a>Erstellen einer Power Pivot-Dienst Anwendung  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie im Menüband **Dienstanwendungen** auf **Neu**.  
  
3.  Wählen Sie **SQL Server Power Pivot-Dienst Anwendung**aus. Wenn dies nicht in der Liste angezeigt wird, wurde PowerPivot für SharePoint nicht installiert oder nicht ordnungsgemäß konfiguriert.  
  
4.  Geben Sie auf der Seite **neue Power Pivot-Dienst Anwendung erstellen** einen Namen für die Anwendung ein. Der Standardwert ist PowerPivotServiceApplication\<Number>. Wenn Sie mehrere PowerPivot-Dienstanwendungen erstellen, hilft ein aussagekräftiger Name anderen Administratoren, den Verwendungszweck der Anwendung zu verstehen.  
  
5.  Erstellen Sie in Anwendungspool einen neuen Anwendungspool für die Anwendung (empfohlen). Wählen Sie ein verwaltetes Konto für den Anwendungspool aus, oder erstellen Sie es. Sie müssen ein Domänenbenutzerkonto angeben. Ein Domänenbenutzerkonto ermöglicht die Verwendung der in SharePoint verfügbaren Funktion Verwaltetes Konto, mit der Sie Kennwörter und Kontoinformationen zentral aktualisieren können. Domänenkonten sind auch erforderlich, wenn Sie beabsichtigen, die Bereitstellung auf zusätzlichen Dienstinstanzen, die unter der gleichen Identität ausgeführt werden, zu skalieren.  
  
6.  Der Standardwert unter **Datenbankserver**entspricht der SQL Server-Datenbank-Engine-Instanz, die die Konfigurationsdatenbanken der Farm hostet. Sie können diesen Server verwenden oder einen anderen SQL Server auswählen.  
  
7.  Der Standardwert unter **Datenbankname**ist PowerPivotServiceApplication1_\<GUID>. Sie müssen eine eindeutige Datenbank für jede PowerPivot-Dienstanwendung erstellen. Der Standardname für die Datenbank entspricht dem Standardnamen der Dienstanwendung. Wenn Sie einen eindeutigen Dienstanwendungsnamen eingegeben haben, verwenden Sie eine ähnliche Benennungskonvention für den Datenbanknamen, damit Sie sie zusammen verwalten können.  
  
8.  Der Standardwert unter **Datenbankauthentifizierung**lautet Windows-Authentifizierung. Wenn Sie **SQL-Authentifizierung**auswählen, finden Sie im SharePoint-Administratorhandbuch bewährte Methoden zur Verwendung dieses Authentifizierungstyps in einer SharePoint-Bereitstellung.  
  
9. Aktivieren Sie optional das Kontrollkästchen zum **Hinzufügen des Proxys für diese Power Pivot-Dienst Anwendung zur Standard Proxy Gruppe der Farm.** . Dadurch wird der Standard-Dienstverbindungsgruppe die Dienstanwendungsverbindung hinzugefügt.  
  
     Sie müssen dieses Kontrollkästchen aktivieren, wenn Sie die erste PowerPivot-Dienstanwendung erstellen. Es muss eine Power Pivot-Dienst Anwendung in der Standard Verbindungsgruppe vorhanden sein, damit das Power Pivot-Management-Dashboard ordnungsgemäß funktioniert.  
  
     Fügen Sie der Standardverbindungsgruppe die PowerPivot-Dienstanwendung nicht hinzu, wenn bereits eine vorhanden ist. Das Hinzufügen mehrerer Einträge des gleichen Dienstanwendungstyps ist keine unterstützte Konfiguration und könnte Fehler verursachen. Wenn Sie zusätzliche Dienstanwendungen erstellen, nehmen Sie sie nicht in die Standardverbindungsgruppe auf. Fügen Sie sie stattdessen benutzerdefinierten Listen hinzu.  
  
     Weitere Informationen zu Dienst Zuordnungen finden [Sie unter Verbinden einer Power Pivot-Dienst Anwendung mit einer SharePoint-Webanwendung in der zentral Administration](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).  
  
10. Klicken Sie auf **OK**. Der Dienst wird zusammen mit anderen verwalteten Diensten in der Dienstanwendungsliste der Farm angezeigt.  
  
##  <a name="configure-powerpivot-service-application"></a><a name="ConfigApp"></a>Power Pivot-Dienst Anwendung konfigurieren  
 Eine PowerPivot-Dienstanwendung wird unter Verwendung einer Standardkonfiguration erstellt. Für die meisten Szenarien werden die Standardeinstellungen empfohlen. Sie sollten nur geändert werden, falls Antwortzeiten zu lang sind oder Verbindungen getrennt werden oder wenn Sie unterschiedliche PowerPivot-Dienstkonfigurationen für bestimmte SharePoint-Webanwendungen verwenden.  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
     In der Liste der Dienstanwendungen sollte die gerade erstellte und benannte Dienstanwendung angezeigt werden. Der Standardname ist **PowerPivotServiceApplication1**.  
  
2.  Klicken Sie auf die PowerPivot-Dienstanwendung. Dadurch wird das PowerPivot-Management-Dashboard geöffnet.  
  
3.  Klicken Sie in der Liste **Aktionen** oben rechts im Dashboard auf **Einstellungen für Dienstanwendung konfigurieren**.  
  
4.  Erhöhen oder verringern Sie den Wert unter **Timeout für Daten Bank Auslastung**, um zu ändern, wie lange der Power Pivot-Dienst auf eine Antwort von der SQL Server Analysis Services (Power Pivot)-Instanz wartet, an die eine Anforderung zum Laden von Daten weitergeleitet wurde. Da die Übertragung sehr großer Datasets einige Zeit dauern kann, müssen Sie genügend Zeit vorsehen, damit die PowerPivot-Dienstinstanz die Excel-Arbeitsmappe abrufen und die PowerPivot-Daten zur Abfrageverarbeitung in eine Analysis Services-Instanz verschieben kann. Da PowerPivot-Daten ungewöhnlich umfangreich sein können, ist der Standardwert 30 Minuten.  
  
5.  Erhöhen oder verringern Sie den Wert unter **Timeout für Verbindungspool**, um die Dauer in Minuten zu ändern, die eine Datenverbindung im Leerlauf geöffnet gehalten wird. Der Standardwert ist 30 Minuten. Während dieses Zeitraums wird eine Datenverbindung im Leerlauf für schreibgeschützte Anforderungen desselben SharePoint-Benutzers für dieselben Power Pivot-Daten vom Power Pivot-Dienst wieder verwendet. Wenn im angegebenen Zeitraum keine weiteren Anforderungen für diese Daten empfangen werden, wird die Verbindung aus dem Pool entfernt. Gültige Werte reichen von 1 bis 3600 Sekunden. Weitere Informationen zu Verbindungspools finden Sie unter [Referenz zur Konfigurationseinstellung &#40;PowerPivot für SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md).  
  
6.  Erhöhen oder verringern Sie den Wert unter **Maximale Größe für den Benutzer Verbindungs Pool**, um die maximale Anzahl von Verbindungen im Leerlauf zu ändern, die der Power Pivot-Dienst in einzelnen Verbindungspools für die einzelnen SharePoint-Benutzer, Power Pivot-Datasets und Versions Kombinationen erstellt.  
  
     Der Standardwert ist 1.000 Verbindungen im Leerlauf. Gültige Werte sind -1 (unbegrenzt), 0 (deaktiviert das Pooling von Benutzerverbindungen) oder 1 bis 10.000.  
  
     Durch diese Verbindungspools kann der Dienst fortlaufende Verbindungen mit den gleichen schreibgeschützten Daten, die vom selben Benutzer hergestellt werden, effizienter unterstützen. Wenn Sie das Verbindungspooling deaktivieren, wird jede Verbindung erneut erstellt.  
  
     Beachten Sie, dass Änderungen am Grenzwert der Verbindungspoolgröße (auch die Festlegung auf 0) nicht dazu führen, dass Verbindungen getrennt werden. Verbindungspools sind vorhanden, um Wartezeiten beim Herstellen einer Datenverbindung zu reduzieren. Der PowerPivot-Dienst wird nie eine Verbindung aufgrund von Verbindungspooleinstellungen ablehnen.  
  
7.  Erhöhen oder verringern Sie den Wert unter **Maximale Größe für den administrativen Verbindungspool**, um die Anzahl der geöffneten Verbindungen in einem Verbindungspool zu ändern, der für eine Power Pivot-Dienst Verbindung Analysis Services erstellt wurde. Jede PowerPivot-Dienstinstanz öffnet eine separate Administratorverbindung zur Analysis Services-Instanz auf demselben Computer. Der PowerPivot-Dienst erstellt einen separaten Pool, damit Administratorverbindungen wiederverwendet werden können, um Verbindungen im Leerlauf zu suchen und den Serverzustand zu überwachen. Der Standardwert ist 200 Verbindungen. Gültige Werte sind -1 (unbegrenzt), 0 (deaktiviert die Verwendung des Verwaltungsverbindungspools) oder 1 bis 10000. Wenn Sie 0 auswählen, wird jede Verbindung neu erstellt.  
  
8.  In der **Zuordnungs Methode**können Sie das Lasten Ausgleichs Schema angeben, das der PowerPivot-Systemdienst verwendet, um eine bestimmte Power Pivot-Dienst Anwendung für den Lastenausgleich einer ersten Anforderung auszuwählen. Die Standardeinstellung ist **Zustandsbasiert**, mit der Anforderungen auf Grundlage des Serverzustands zugeordnet werden, wie anhand des verfügbaren Arbeitsspeichers und der Prozessorauslastung ermittelt. Alternativ können Sie **Roundrobin** auswählen, um Anforderungen den Servern in der gleichen wiederholten Reihenfolge zuzuordnen, unabhängig davon, ob ein Server ausgelastet oder im Leerlauf ist.  
  
9. Unter Datenaktualisierung in **Geschäftszeiten**können Sie den Zeitraum angeben, der einen Geschäftstag definiert. Zeitpläne zur Datenaktualisierung können am Ende eines Geschäftstags ausgeführt werden, um die während der regulären Geschäftszeiten generierten Transaktionsdaten zu sammeln.  
  
10. Im **unbeaufsichtigten Daten Aktualisierungs Konto für Power Pivot**können Sie eine vordefinierte einmaliges Anmelden Zielanwendung angeben, die ein vordefiniertes Konto zum Ausführen von Power Pivot-Daten Aktualisierungs Aufträgen speichert. Stellen Sie sicher, dass Sie den Namen der Zielanwendung und nicht die ID angeben. Die Zielanwendung für die unbeaufsichtigte Datenaktualisierung wird automatisch erstellt, wenn Sie die Option "Neuer Server" im SQL Server-Setup verwendet haben, um PowerPivot für SharePoint zu installieren. Andernfalls müssen Sie die Zielanwendung manuell erstellen. Anweisungen zum Konfigurieren des Kontos finden Sie unter [Konfigurieren des Power Pivot-Kontos für die unbeaufsichtigte Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md).  
  
11. Unter **Benutzer dürfen benutzerdefinierte Windows-Anmeldeinformationen eingeben**können Sie das Kontrollkästchen aktivieren oder deaktivieren, um anzugeben, ob Zeitplanbesitzer beliebige Windows-Anmeldeinformationen für die Ausführung eines Datenaktualisierungszeitplans eingeben können. Wenn Sie dieses Kontrollkästchen aktivieren, erstellt und verwaltet die PowerPivot-Dienstanwendung eine Zielanwendung für jeden Satz gespeicherter Anmeldeinformationen. Weitere Informationen finden Sie unter [Konfigurieren gespeicherter Anmelde Informationen für die Power Pivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
12. Unter **Maximale Verarbeitungsverlaufslänge**können Sie angeben, wie lange ein Verlaufsdatensatz der Datenaktualisierungsverarbeitung beibehalten wird. Diese Informationen werden auf den Seiten für den Datenaktualisierungsverlauf angezeigt, die für jede Arbeitsmappe angelegt werden, die die Datenaktualisierung nutzt. Sie werden auch im PowerPivot-Management-Dashboard angezeigt.  
  
13. Geben Sie unter Sammlung von Verwendungsdaten in **Berichtsintervall für Abfragen**ein Zeitintervall an, in dem Abfragestatistiken gemeldet werden. Abfragestatistiken werden als einzelnes Ereignis gemeldet, um die Kommunikation zwischen den Servern zu minimieren.  
  
14. Geben Sie unter Verwendungsdatenverlauf an, wie lange ein Verlaufsdatensatz der Verwendungsdaten beibehalten wird. Die Verwendungsinformationen werden im PowerPivot-Management-Dashboard angezeigt. Die Berichte sind weniger effektiv, wenn Sie für den Verwendungsdatenverlauf einen zu niedrigen Wert angeben.  
  
15. Geben Sie unter Sammlung von Verwendungsdaten für jeden Abfrageantwort-Schwellenwert eine Obergrenze an, die bestimmt, wo eine Kategorie aufhört und die nächste beginnt. Durch diese Kategorien wird eine Basislinie festgelegt, auf deren Grundlage das Abfrageverhalten gemessen wird. Sie können diese Kategorien verwenden, um Trends in den Abfrageantwortzeiten Ihres Systems zu überwachen. Diese Informationen werden im PowerPivot-Management-Dashboard angezeigt.  
  
16. Klicken Sie auf **OK** , um die Änderungen zu speichern.  
  
     Änderungen am Timeout für Ladevorgänge oder an der Zuordnungsmethode werden nur auf neu eingehende Anforderungen angewendet. Für Anforderungen, die bereits ausgeführt werden, gelten die Werte, die beim Empfang der Anforderung gültig waren.  
  
##  <a name="assign-a-powerpivot-service-application-to-a-web-application"></a><a name="AssignGSA"></a>Zuweisen einer Power Pivot-Dienst Anwendung zu einer Webanwendung  
 Nachdem Sie eine PowerPivot-Dienstanwendung konfiguriert haben, können Sie sie einer Webanwendung zuweisen, indem Sie sie der Liste der Dienstanwendungsverbindungen für die jeweilige Webanwendung hinzufügen. Hierfür gibt es zwei Möglichkeiten:  
  
-   Fügen Sie die Anwendung der Standardverbindungsgruppe **** hinzu. Die *Standardverbindungsgruppe* ist eine Sammlung von Dienstanwendungsverbindungen, die jeder Webanwendung zur Verfügung stehen, die darauf verweist. Sie müssen dieser Liste eine PowerPivot-Dienstanwendung hinzufügen.  
  
-   Erstellen Sie für eine bestimmte Webanwendung eine **benutzerdefinierte** Verbindungsliste. Wenn Sie mehrere PowerPivot-Dienstanwendungen erstellt haben, können Sie die zu verwendende Anwendung aus einer benutzerdefinierten Liste auswählen.  
  
 Die Standardverbindungsgruppe kann mehr als eine Dienstanwendung des gleichen Typs enthalten. Beachten Sie jedoch, dass das Hinzufügen von mehr als einer PowerPivot-Dienstanwendung zu dieser Liste keine unterstützte Konfiguration ist.  
  
1.  Klicken Sie in der Zentraladministration unter **Anwendungsverwaltung**auf **Webanwendungen verwalten**.  
  
2.  Wählen Sie die Anwendung aus, für die Sie eine Verbindung zuweisen möchten (z. B. SharePoint -80).  
  
3.  Klicken Sie auf **Dienstverbindungen**.  
  
4.  Wählen Sie unter folgende Zuordnungs **Gruppe bearbeiten die**Option **Standard** oder **[Benutzer definiert]** aus.  
  
5.  Aktivieren Sie für **[Custom]** das Kontrollkästchen neben jeder Dienst Anwendungs Verbindung, die Sie verwenden möchten. Wenn Sie über mehrere Power Pivot-Dienst Anwendungen verfügen (angezeigt durch den `PowerPivot Service Application Proxy`Typ auf festgelegt), achten Sie darauf, nur eine zu wählen.  
  
6.  Klicken Sie auf **OK**.  
  
##  <a name="edit-service-application-properties"></a><a name="EditGSA"></a>Bearbeiten von Eigenschaften der Dienst Anwendung  
 Verwenden Sie die folgenden Anweisungen, um die Eigenschaftenseite erneut zu öffnen, die den Dienstanwendungsnamen, den Anwendungspool sowie die Datenbankeinstellungen und Dienstzuordnungen enthält.  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Wählen Sie die PowerPivot-Dienstanwendung aus, aber klicken Sie nicht darauf. Sie können auf den Typnamen klicken, um die gesamte Zeile auszuwählen.  
  
3.  Klicken Sie im Menüband auf **Eigenschaften** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [PowerPivot-Serververwaltung und -konfiguration in der Zentraladministration](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
