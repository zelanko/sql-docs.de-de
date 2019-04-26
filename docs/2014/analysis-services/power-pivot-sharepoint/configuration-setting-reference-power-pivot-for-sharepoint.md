---
title: Konfigurationseinstellungsverweis (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 3b57dd3f-7820-4ba8-b233-01dc68908273
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a3ee6babe5048398f62cd335e0a121f32f4734ff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743366"
---
# <a name="configuration-setting-reference-powerpivot-for-sharepoint"></a>Konfigurationseinstellungsverweis (PowerPivot für SharePoint)
  Dieses Thema enthält Referenzdokumentation zu den von PowerPivot-Dienstanwendungen in einer SharePoint-Farm verwendeten Konfigurationseinstellungen. Wenn Sie einen Server mithilfe von PowerShell-Skripts konfigurieren oder Informationen zu einer bestimmten Einstellung suchen möchten, finden Sie in den Informationen in diesem Thema ausführliche Beschreibungen.  
  
 Konfigurationseinstellungen werden für jede PowerPivot-Dienstanwendung festgelegt. Innerhalb einer Farm können Sie mehrere Serveranwendungen erstellen, um so unabhängige logische Instanzen der gleichen physischen Dienstinstanz zu konfigurieren. Konfigurationseinstellungen werden in der PowerPivot-Anwendungsdatenbank gespeichert, die für jede von Ihnen konfigurierte Dienstanwendung erstellt wird.  
  
 Wenn Sie Konfigurationseinstellungen ändern, werden die Änderungen sofort abgerufen und für nachfolgende Anforderungen und Verbindungen verwendet. Laufende Vorgänge unterliegen den Einstellungen, die zu Beginn des Vorgangs wirksam waren.  
  
 Klicken Sie auf die folgenden Links, um Informationen zu bestimmten Konfigurationsbereichen zu erhalten:  
  
 [Data Load Timeout](#LoadingData)  
  
 [Verbindungspools](#ConnectionPool)  
  
 [Lastenausgleich](#AllocationScheme)  
  
 [Datenaktualisierung](#DataRefresh)  
  
 [Sammlung von Verwendungsdaten](#UsageData)  
  
 Anweisungen dazu, wie Sie eine PowerPivot-dienstanwendung zu erstellen, finden Sie unter [erstellen und konfigurieren Sie eine PowerPivot-Dienstanwendung in der Zentraladministration](create-and-configure-power-pivot-service-application-in-ca.md).  
  
##  <a name="LoadingData"></a> Data Load Timeout  
 PowerPivot-Daten werden durch Analysis Services-Serverinstanzen in die Farm abgerufen und geladen. Je nachdem, wie und wann zuletzt auf die Daten zugegriffen wurde, werden sie entweder aus einer Inhaltsbibliothek oder aus einem lokalen Dateicache geladen. Daten werden immer dann in den Arbeitsspeicher geladen, wenn eine Abfrage- oder Verarbeitungsanforderung empfangen wird. Um die Gesamtverfügbarkeit des Servers zu maximieren, können Sie einen Timeoutwert festlegen, der den Server anweist, eine Anforderung zum Laden von Daten zu beenden, wenn sie nicht innerhalb der vorgesehenen Zeit abgeschlossen werden kann.  
  
|Name|Standard|Gültige Werte|Description|  
|----------|-------------|------------------|-----------------|  
|Data Load Timeout|1800 (in Sekunden)|1 bis 3600|Gibt an, wie lange eine PowerPivot-Dienstanwendung auf eine Antwort von einer bestimmten Analysis Services-Serverinstanz wartet.<br /><br /> Standardmäßig wartet die Dienstanwendung 30 Minuten auf eine Datennutzlast von der Engine-Dienstinstanz, an die sie eine bestimmte Anforderung weitergeleitet hat.<br /><br /> Wenn die PowerPivot-Datenquelle nicht innerhalb dieses Zeitraums geladen werden kann, wird der Thread beendet und ein neuer gestartet.|  
  
##  <a name="ConnectionPool"></a> Verbindungspools  
 Die PowerPivot-Dienstanwendung erstellt und verwaltet Verbindungspools, damit Verbindungen wiederverwendet werden können. Es gibt zwei Typen von Verbindungspools: ein Typ für Datenverbindungen mit schreibgeschützten Daten und ein weiterer für Serververbindungen.  
  
 Datenverbindungspools enthalten zwischengespeicherte Verbindungen für PowerPivot-Datenquellen. Jeder Verbindungspool basiert auf dem Kontext, der beim Laden der Datenbank festgelegt wurde. Dieser Kontext enthält die Identität der physischen Dienstinstanz, die Datenbank-ID sowie die Identität des SharePoint-Benutzers, der Daten anfordert. Für jede Kombination wird ein separater Verbindungspool erstellt. Beispielsweise werden für Anforderungen unterschiedlicher Benutzer, die dieselbe, auf dem gleichen Server ausgeführte Datenbank verwenden, Verbindungen aus unterschiedlichen Pools genutzt.  
  
 Der Zweck eines Verbindungspools besteht darin, dass für schreibgeschützte Anforderungen desselben SharePoint-Benutzers, die an die gleiche Analysis Services-Datenbank gerichtet sind, zwischengespeicherte Verbindungen verwendet werden können. Die PowerPivot-Dienstinstanz entspricht dem Server, in dessen Arbeitsspeicher die Daten geladen wurden. Die Datenbank-ID ist ein interner Bezeichner für die im Arbeitsspeicher enthaltenen Datenstrukturen des Datenmodells (ein Modell wird als [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Cubedatenbank instanziiert). Versionsinformationen werden implizit in den Bezeichner integriert.  
  
 Serververbindungspools enthalten zwischengespeicherte Verbindungen zwischen einer PowerPivot-Dienstanwendungsinstanz und einer Analysis Services-Serverinstanz. Dabei stellt die Dienstanwendung die Verbindung mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Sysadmin-Berechtigungen auf dem Analysis Services-Server her. Diese Verbindungen werden verwendet, um eine Anforderung zum Laden der Datenbank auszugeben und die Systemintegrität zu überwachen.  
  
 Jeder Typ von Verbindungspool verfügt über Obergrenzen, die Sie für die Verbindungsverwaltung festlegen können, um sicherzustellen, dass der Systemspeicher optimal genutzt wird.  
  
|Name|Standard|Gültige Werte|Description|  
|----------|-------------|------------------|-----------------|  
|Verbindungspool-Timeout|1800 (in Sekunden)|1 bis 3600.|Diese Einstellung gilt für Datenverbindungspools.<br /><br /> Sie gibt an, wie lange eine Verbindung im Leerlauf im Verbindungspool verbleiben kann, bevor sie entfernt wird.<br /><br /> Die Dienstanwendung entfernt eine Verbindung standardmäßig, wenn sie länger als fünf Minuten inaktiv ist.|  
|Maximale Größe für den Benutzerverbindungspool|1000|-1, 0 oder 1 bis 10000.<br /><br /> -1 gibt eine unbegrenzte Anzahl von Verbindungen im Leerlauf an.<br /><br /> 0 bedeutet, dass keine Verbindungen im Leerlauf beibehalten werden. Es muss jedes Mal eine neue Verbindung mit einer PowerPivot-Datenquelle erstellt werden.|Diese Einstellung gilt für die Anzahl von Verbindungen im Leerlauf in allen für eine bestimmte PowerPivot-Dienstanwendungsinstanz erstellten Datenverbindungspools.<br /><br /> Für eindeutige Kombinationen aus SharePoint-Benutzer, PowerPivot-Daten und Dienstinstanz werden individuelle Verbindungspools erstellt. Wenn zahlreiche Benutzer auf unterschiedliche PowerPivot-Datenquellen zugreifen, könnte die Serverleistung durch einen größeren Verbindungspool verbessert werden.<br /><br /> Wenn sich mehr als 100 Verbindungen mit einer PowerPivot-Dienstinstanz im Leerlauf befinden, werden neue im Leerlauf befindliche Verbindungen getrennt und nicht an den Pool zurückgegeben.|  
|Maximale Größe für den Verwaltungsverbindungspool|200|-1, 0 oder 1 bis 10000.<br /><br /> -1 gibt eine unbegrenzte Anzahl von Verbindungen im Leerlauf an.|Die maximale Anzahl von Serververbindungen im Leerlauf in allen Verwaltungsverbindungspools, die für PowerPivot-Dienstanwendungsverbindungen mit einer Analysis Services-Serverinstanz erstellt wurden. Für Anforderungen zum Laden von Datenbanken und Zurückspeichern von Änderungen in der SharePoint-Datenbank werden Serververbindungen verwendet.|  
  
##  <a name="AllocationScheme"></a> Lastenausgleich  
 Zu den Funktionen des PowerPivot-Diensts gehört die Bestimmung der verfügbaren PowerPivot-Dienstinstanz, in der Analysis Services-Daten geladen werden. Die `AllocationMethod`-Einstellung gibt die Kriterien an, nach denen eine Dienstinstanz ausgewählt wird.  
  
|Name|Standard|Gültige Werte|Description|  
|----------|-------------|------------------|-----------------|  
|Zuordnungsmethode|RoundRobin|Roundrobin<br /><br /> Zustandsbasiert|Ein Schema zum Zuordnen von Ladeanforderungen unter mindestens zwei Analysis Services-Serverinstanzen.<br /><br /> Standardmäßig verteilt der PowerPivot-Dienst die Anforderungen auf Grundlage des Serverzustands. Bei Zustandsbasiert werden Anforderungen dem Server zugeordnet, dem unter Berücksichtigung des verfügbaren Arbeitsspeichers und der CPU-Auslastung die meisten Systemressourcen zur Verfügung stehen.<br /><br /> Bei Roundrobin werden die Anforderungen in sequenzieller Reihenfolge auf die verfügbaren Servern verteilt, unabhängig von der aktuellen Serverauslastung oder vom Serverzustand.|  
  
##  <a name="DataRefresh"></a> Datenaktualisierung  
 Geben Sie den Zeitraum an, der einem normalen bzw. typischen Geschäftstag in Ihrer Organisation entspricht. Diese Konfigurationseinstellungen bestimmen den Zeitpunkt, zu dem Datenaktualisierungsvorgänge nach den Geschäftsstunden verarbeitet werden. Die Verarbeitung nach den Geschäftsstunden kann am Ende des Geschäftstags initiiert werden. Die Verarbeitung nach den Geschäftsstunden ist eine Zeitplanoption für Dokumentbesitzer, die eine PowerPivot-Datenquelle mit Transaktionsdaten aktualisieren möchten, die während normaler Geschäftszeiten generiert wurden.  
  
|Name|Standard|Gültige Werte|Description|  
|----------|-------------|------------------|-----------------|  
|Startzeit|04:00 Uhr|1 bis 12 Stunden, wobei der Wert einer gültigen ganzen Zahl innerhalb dieses Bereichs entspricht.<br /><br /> Der Typ lautet Zeit.|Legt die Untergrenze eines Geschäftstags fest.|  
|Beendigungszeit|20:00 Uhr|1 bis 12 Stunden, wobei der Wert einer gültigen ganzen Zahl innerhalb dieses Bereichs entspricht.<br /><br /> Der Typ lautet Zeit.|Legt die Obergrenze eines Geschäftstags fest.|  
|Konto der unbeaufsichtigten PowerPivot-Datenaktualisierung|None|Eine Zielanwendungs-ID|Dieses Konto wird verwendet, um Datenaktualisierungsaufträge für einen Zeitplanbesitzer auszuführen.<br /><br /> Das unbeaufsichtigte Datenaktualisierungskonto muss im Voraus definiert werden, bevor auf der Dienstanwendungskonfigurationsseite darauf verwiesen werden kann. Weitere Informationen finden Sie unter [konfigurieren Sie die PowerPivot-datenaktualisierungskonto &#40;PowerPivot für SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md).|  
|Ermöglichen Sie Benutzern, benutzerdefinierte Windows-Anmeldeinformationen einzugeben|Aktiviert|Boolean|Legt fest, ob die Seite für die Konfiguration geplanter Datenaktualisierungen eine Option anzeigt, die einem Zeitplanbesitzer ermöglicht, Windows-Benutzerkonto und Kennwort anzugeben, um einen Datenaktualisierungsauftrag auszuführen.<br /><br /> Secure Store Service muss aktiviert werden, damit diese Option funktioniert. Weitere Informationen finden Sie unter [konfigurieren gespeicherter Anmeldeinformationen für die PowerPivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).|  
|Maximale Verarbeitungsverlaufslänge|365|1 bis 5000 Tage|Bestimmt, wie lange der Datenaktualisierungsverlauf in der PowerPivot-Dienstanwendungsdatenbank beibehalten wird. Weitere Informationen finden Sie unter [PowerPivot Usage Data Collection](power-pivot-usage-data-collection.md).|  
  
##  <a name="UsageData"></a> Sammlung von Verwendungsdaten  
 Verwendungsberichte, die im PowerPivot-Management-Dashboard angezeigt werden, können wichtige Informationen darüber enthalten, wie PowerPivot-aktivierte Arbeitsmappen verwendet werden. Die folgenden Konfigurationseinstellungen steuern Aspekte bei der Sammlung von Verwendungsdaten für PowerPivot-Serverereignisse, die anschließend in Verwendungs- oder Aktivitätsberichten präsentiert werden.  
  
|Name|Standard|Gültige Werte|Description|  
|----------|-------------|------------------|-----------------|  
|Abfrage eines Berichtsintervalls|300 (in Sekunden)|1 bis n Sekunden, wobei n eine beliebige gültige ganze Zahl darstellt.|Um sicherzustellen dass die Datenübertragungskapazität der Farm bei der Sammlung von Verwendungsdaten nicht zu stark beansprucht wird, wird für jede Verbindung eine Abfragestatistik erstellt und als einzelnes Ereignis gemeldet. Das Abfrageberichtsintervall bestimmt, wie oft ein Ereignis gemeldet wird. Standardmäßig wird eine Abfragestatistik alle 5 Minuten ausgegeben.<br /><br /> Da Verbindungen sofort nach dem Senden einer Anforderung geschlossen werden, generiert das System selbst dann eine sehr große Anzahl von Verbindungen, wenn nur ein Benutzer auf eine einzelne PowerPivot-Datenquelle zugreift. Aus diesem Grund werden für jede Kombination aus Benutzer und PowerPivot-Datenquelle Verbindungspools erstellt, damit eine einmal erstellte Verbindung vom gleichen Benutzer für dieselben Daten wiederverwendet werden kann. Die PowerPivot-Dienstanwendung generiert in regelmäßigen, durch diese Konfigurationseinstellung angegeben Abständen einen Verwendungsdatenbericht für jede Verbindung im Verbindungspool.<br /><br /> Wenn Sie das Intervall für die Berichterstellung vergrößern, werden weniger Ereignisse protokolliert. Falls Sie den Wert jedoch zu hoch ansetzen, riskieren Sie den Verlust von Ereignisdaten, wenn der Server neu gestartet oder eine Verbindung geschlossen wird.<br /><br /> Wenn Sie den Wert herabsetzen, werden mehr Ereignisse in kürzeren Abständen protokolliert und dem Datensammlungssystem in der SharePoint-Verwendungsdatenbank zusätzliche PowerPivot-Verwendungsdaten zugeführt.<br /><br /> Im Allgemeinen sollten Sie diese Konfigurationseinstellung nicht ändern, sofern nicht ein bestimmtes Problem behoben werden muss (beispielsweise, wenn die Verwendungsdatenbank aufgrund von PowerPivot-Verwendungsdaten zu schnell anwächst).|  
|Verwendungsdatenverlauf|365 (in Tagen)|0 oder 1 bis n Tage, wobei n eine beliebige gültige ganze Zahl darstellt.<br /><br /> 0 bedeutet, dass der Verlauf immer beibehalten und nie gelöscht wird.|Verwendungsdaten werden standardmäßig ein Jahr in der Datenbank der PowerPivot-Dienstanwendung beibehalten. Datensätze von über einem Jahr werden aus der Datenbank gelöscht.<br /><br /> Eine Überprüfung der abgelaufenen Verlaufdaten findet täglich statt, wenn der Microsoft Share Point Foundation Usage Data Processing-Auftrag läuft. Der Zeitgeberauftrag liest diese Einstellung und löst in der Datenbank der PowerPivot-Dienstanwendung einen Befehl zum Löschen abgelaufener Vergangenheitsdaten aus.|  
|Obergrenze für triviale Antworten|500 (in Millisekunden)|1 bis n Millisekunden, wobei n eine beliebige gültige ganze Zahl darstellt.|Standardmäßig beträgt der Schwellenwert für triviale Anforderungen eine halbe Sekunde.<br /><br /> Zu trivialen Anforderungen gehören Ping-Signale an den Server, Metadatenanforderungen und das Starten von Sitzungen.|  
|Obergrenze für schnelle Antworten|1000 (in Millisekunden)|1 bis n Millisekunden, wobei n eine beliebige gültige ganze Zahl darstellt.|Der Schwellenwert für schnelle Anforderungen beträgt standardmäßig eine Sekunde.<br /><br /> Schnelle Anforderungen verfügen typischerweise über ein äußerst kleines Dataset oder über Anforderungen von Metadaten, die große Elementgruppen umfassen.|  
|Obergrenze für erwartete Antwortdauer|3000 (in Millisekunden)|1 bis n Millisekunden, wobei n eine beliebige gültige ganze Zahl darstellt.|Der Schwellenwert für erwartete Anforderungen beträgt standardmäßig drei Sekunden.<br /><br /> Dieser Schwellenwert legt die Obergrenze einer erwarteten Abfragezeit fest.|  
|Obergrenze für lange Antwort|10000 (in Millisekunden)|1 bis n Millisekunden, wobei n eine beliebige gültige ganze Zahl darstellt.|Der Schwellenwert für lange Anforderungen beträgt standardmäßig zehn Sekunden.<br /><br /> Die Ausführung dieser Anforderungen dauert länger als erwartet, liegt aber immer noch innerhalb eines akzeptablen Bereichs.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Konfigurieren einer PowerPivot-Dienstanwendung in der Zentraladministration](create-and-configure-power-pivot-service-application-in-ca.md)   
 [PowerPivot-Datenaktualisierung mit SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)   
 [Konfigurieren der Sammlung von Verwendungsdaten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)   
 [Konfigurieren von PowerPivot-Dienstkonten](configure-power-pivot-service-accounts.md)   
 [PowerPivot-Management-Dashboard und -Verwendungsdaten](power-pivot-management-dashboard-and-usage-data.md)  
  
  
