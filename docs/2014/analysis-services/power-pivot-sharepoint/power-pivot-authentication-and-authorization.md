---
title: PowerPivot-Authentifizierung und-Autorisierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 48230cc0-4037-4f99-8360-dadf4bc169bd
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cea8b8e9d6f883d6933ed72591da20de73d55326
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210220"
---
# <a name="powerpivot-authentication-and-authorization"></a>PowerPivot-Authentifizierung und -Autorisierung
  Eine PowerPivot für SharePoint-Bereitstellung, die innerhalb einer SharePoint 2010-Farm ausgeführt wird, verwendet das von den SharePoint-Servern bereitgestellte Authentifizierungssubsystem und Autorisierungsmodell. Die SharePoint-Sicherheitsinfrastruktur erstreckt sich auch auf PowerPivot-Inhalte und -Vorgänge, da sämtliche PowerPivot-bezogenen Inhalte in SharePoint-Inhaltsdatenbanken gespeichert und alle PowerPivot-bezogenen Vorgänge von freigegebenen PowerPivot-Diensten in der Farm ausgeführt werden. Benutzer, die eine Arbeitsmappe mit PowerPivot-Daten anfordern, werden mit einer SharePoint-Benutzeridentität authentifiziert, die auf deren Windows-Benutzeridentität basiert. Anzeigeberechtigungen für die Arbeitsmappe bestimmen, ob die Anforderung gewährt oder verweigert wird.  
  
 Da die Integration mit Excel Services für Self-Service-Datenanalysen erforderlich ist, sollten Ihnen zum Sichern eines PowerPivot-Servers auch die Sicherheitsfunktionen von Excel Services vertraut sein. Wenn ein Benutzer eine PivotTable abfragt, die über eine Datenverbindung zu PowerPivot-Daten verfügt, leiten die Excel Services eine Datenverbindungsanforderung zum Laden der Daten an einen PowerPivot-Server in der Farm weiter. Aufgrund der Interaktion zwischen den Servern sollten Sie wissen, wie Sie Sicherheitseinstellungen für beide Server konfigurieren.  
  
 Klicken Sie auf die folgenden Links, um bestimmte Abschnitte in diesem Thema zu lesen:  
  
 [Windows-Authentifizierung, die unter Verwendung der Anmeldungsanforderung im klassischen Modus](power-pivot-authentication-and-authorization.md#bkmk_auth)  
  
 [PowerPivot-Vorgänge, die eine Benutzerautorisierung erfordern](#UserConnections)  
  
 [SharePoint-Berechtigungen für PowerPivot-Datenzugriff](#Permissions)  
  
 [Excel Services – sicherheitsüberlegungen für PowerPivot-Arbeitsmappen](#excel)  
  
##  <a name="bkmk_auth"></a> Windows-Authentifizierung unter Verwendung der Anmeldungsanforderung im klassischen Modus  
 PowerPivot für SharePoint unterstützt eine eingeschränkte Anzahl der Authentifizierungsoptionen, die in SharePoint verfügbar sind. Von den verfügbaren Authentifizierungsoptionen wird nur die Windows-Authentifizierung für eine PowerPivot für SharePoint-Bereitstellung unterstützt. Außerdem muss die Webanwendung, über die die Anmeldung erfolgt, für den klassischen Modus konfiguriert sein.  
  
 Die Windows-Authentifizierung ist erforderlich, weil die Analysis Services-Daten-Engine in einer PowerPivot für SharePoint-Bereitstellung nur die Windows-Authentifizierung unterstützt. Excel Services stellt über den MSOLAP OLE DB-Anbieter Verbindungen mit Analysis Services her. Dabei wird die Identität eines Windows-Benutzers verwendet, der über NTLM oder das Kerberos-Protokoll authentifiziert wurde.  
  
 Durch die zweite Anforderung, dass für die Webanwendung die Authentifizierung im klassischen Modus verwendet werden soll, wird sichergestellt, dass der PowerPivot-Webdienst funktioniert. Der Webdienst ist eine Komponente, die auf einem Web-Front-End ausgeführt wird und die HTTP-Umleitung an einen PowerPivot für SharePoint-Server in der Farm vornimmt. Während der Webdienst bei der Dienst-zu-Dienst-Kommunikation als eine Ansprüche unterstützende Anwendung fungiert, trifft dies für Datenverbindungsanforderungen, die an einen freigegebenen PowerPivot-Dienst in der Farm umgeleitet werden, nicht zu. Anforderungen zum Laden von PowerPivot-Daten werden nur für authentifizierte Verbindungen unterstützt, die unter Verwendung einer Windows-Identität von IIS gesendet werden. Die Anmeldung im klassischen Modus in der Webanwendung ermöglicht eine erfolgreiche Verbindung vom PowerPivot-Webdienst zu freigegebenen PowerPivot-Diensten in der Farm.  
  
 Obwohl die Anmeldung im klassischen Modus für das allgemeinere Datenzugriffsszenario (in dem PowerPivot-Daten aus derselben bereitstellenden Excel-Arbeitsmappe extrahiert werden) nicht erforderlich ist, verwenden Sie PowerPivot für SharePoint nicht mit SharePoint-Webanwendungen, die zur Verwendung anderer Authentifizierungsanbieter konfiguriert sind. Dies führt zu einem Verbindungsfehler, wenn Benutzer eine Verbindung mit PowerPivot-Arbeitsmappen als externe Datenquelle herstellen möchten.  
  
 Ohne klassische Modusanmeldung schlagen die folgenden Anforderungstypen, die vom PowerPivot-Webdienst behandelt werden, fehl:  
  
-   Jede Anforderung für PowerPivot-Daten, die von außerhalb der Farm stammt (z. B. Erstellen eines Berichts im Berichts-Designer oder Berichts-Generator, wo die Datenquelle eine SharePoint-URL für eine PowerPivot-Arbeitsmappe ist)  
  
-   Farminterne Anforderungen von einer Clientanwendung oder einem Bericht, die bzw. der die PowerPivot-Arbeitsmappe als externe Datenquelle verwendet (z B. Erstellen einer Arbeitsmappe in der Excel-Desktopanwendung, wobei als Datenquelle eine zweite veröffentlichte Excel-Arbeitsmappe mit PowerPivot-Daten verwendet wird)  
  
### <a name="how-to-check-the-authentication-provider-for-your-application"></a>So überprüfen Sie den Authentifizierungsanbieter für eine Anwendung  
 Aktivieren Sie bei der Erstellung einer neuen Webanwendung auf der Seite „Neue Webanwendung erstellen“ die Option **Klassischer Authentifizierungsmodus** .  
  
 Für vorhandene Webanwendungen befolgen Sie die folgenden Anweisungen, um sicherzustellen, dass die Webanwendung für die Verwendung der Windows-Authentifizierung konfiguriert sind.  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Webanwendungen verwalten**.  
  
2.  Wählen Sie die Webanwendung aus.  
  
3.  Klicken Sie auf **Authentifizierungsanbieter**.  
  
4.  Überprüfen Sie, ob es einen Anbieter für jede Zone gibt und die Standardzone auf Windows festgelegt ist.  
  
##  <a name="UserConnections"></a> PowerPivot-Vorgänge, die eine Benutzerautorisierung erfordern  
 Die SharePoint-Autorisierung wird ausschließlich für alle Zugriffsebenen für die PowerPivot-Abfrage- und -Datenverarbeitung verwendet.  
  
 Das rollenbasierte Analysis Services-Autorisierungsmodell wird nicht unterstützt. Für PowerPivot-Daten steht keine rollenbasierte Autorisierung auf Zellen-, Zeilen- oder Tabellenebene zur Verfügung. Sie können nicht verschiedene Teile der Arbeitsmappe sichern, um ausgewählten Benutzern Zugriff auf vertrauliche Daten in der Datenquelle zu gewähren oder zu verweigern. Eingebettete PowerPivot-Daten sind für Benutzer mit Anzeigeberechtigungen für die Excel-Arbeitsmappe in einer SharePoint-Bibliothek uneingeschränkt verfügbar.  
  
 PowerPivot für SharePoint nimmt in den folgenden Fällen die Identität eines SharePoint-Benutzers an:  
  
-   Abfragen an PivotTables oder PivotCharts, die über Datenverbindungen mit einer PowerPivot-Datenbank verfügen. Dabei stellt eine PowerPivot-Dienstanwendung im Namen eines Benutzers Verbindungen mit einer bestimmten freigegebenen PowerPivot-Dienstinstanz her, die die Daten verarbeitet.  
  
-   Das Laden von PowerPivot-Daten aus dem Zwischenspeicher oder einer Bibliothek, wenn die Daten andernfalls nicht verfügbar sind. Wenn eine Datenverbindungsanforderung für eine PowerPivot-Datenquelle ausgegeben wird, die noch nicht in das System geladen wurde, nimmt die [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]-Instanz die Identität eines SharePoint-Benutzers an, um die Datenquelle aus einer Inhaltsbibliothek abzurufen und in den Arbeitsspeicher zu laden.  
  
-   Datenaktualisierungsvorgänge, bei denen eine aktualisierte Kopie der Datenquelle in der Arbeitsmappe in einer Inhaltsbibliothek gespeichert wird. In diesem Fall wird ein aktuelles Protokoll für den Vorgang unter Verwendung des Benutzernamens und des Kennworts ausgeführt, der/das aus einer Zielanwendung in Secure Store Service abgerufen wird. Die Anmeldeinformationen können das Konto der unbeaufsichtigten PowerPivot-Datenaktualisierung oder die Anmeldeinformationen sein, die zusammen mit dem Datenaktualisierungszeitplan bei seiner Erstellung gespeichert wurden. Weitere Informationen finden Sie unter [konfigurieren gespeicherter Anmeldeinformationen für die PowerPivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41; ](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md) und [konfigurieren Sie die PowerPivot-datenaktualisierungskonto &#40; PowerPivot für SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md).  
  
##  <a name="Permissions"></a> SharePoint-Berechtigungen für PowerPivot-Datenzugriff  
 Die Veröffentlichung, Verwaltung und Sicherung einer PowerPivot-Arbeitsmappe wird nur durch die SharePoint-Integration unterstützt. SharePoint-Server bieten Authentifizierungs- und Autorisierungssubsysteme an, die den berechtigten Zugang zu Daten sicherstellen. Szenarien für die sichere Bereitstellung einer PowerPivot-Arbeitsmappe außerhalb einer SharePoint-Farm werden nicht unterstützt.  
  
 Der Benutzerzugriff auf PowerPivot-Daten ist auf dem Server schreibgeschützt und erfordert mindestens Anzeigeberechtigungen. Über Teilnahmeberechtigungen wird das Hinzufügen und Bearbeiten der Datei erlaubt. Änderungen an PowerPivot-Daten erfordern, dass Sie die Arbeitsmappe in eine Excel-Desktopanwendung herunterladen, in der PowerPivot für Excel installiert ist. Über die Teilnahmeberechtigungen für die Datei wird ermittelt, ob der Benutzer berechtigt ist, die Datei lokal herunterzuladen und Änderungen in SharePoint zurückzuspeichern.  
  
 Dies bedeutet, dass der effektive Berechtigungssatz für den Benutzerzugriff auf PowerPivot-Daten durch die Berechtigungsstufen Mitwirken und Anzeigen definiert wird. Andere Berechtigungsstufen können insofern verwendet werden, dass sie die gleichen Berechtigungen wie Mitwirken und Nur anzeigen beinhalten. (Beispiel: Da Lesen die Berechtigung Nur anzeigen einschließt, verfügt ein Benutzer, dem Lesen zugewiesen wird, über die gleiche Zugriffsebene wie ein Nur anzeigen.)  
  
 In der folgenden Tabelle werden die Berechtigungsebenen zusammengefasst, die den Zugriff auf PowerPivot-Daten- und -Servervorgänge bestimmen:  
  
|Berechtigungsstufe|Lässt diese Tasks zu|  
|----------------------|------------------------|  
|Farm- oder Dienstadministrator|Installieren, Aktivieren und Konfigurieren von Diensten und Anwendungen<br /><br /> Verwenden des PowerPivot-Management-Dashboards und Anzeigen von Administratorberichten|  
|Vollzugriff|Aktivieren der Integration von PowerPivot-Funktionen auf Website-Sammlungsebene<br /><br /> Erstellen Sie eine PowerPivot-katalogbibliothek.<br /><br /> Erstellen einer Datenfeedbibliothek|  
|Mitwirken|Hinzufügen, Bearbeiten, Löschen und Herunterladen von PowerPivot-Arbeitsmappen<br /><br /> Konfigurieren der Datenaktualisierung<br /><br /> Erstellen neuer Arbeitsmappen und Berichte auf Grundlage von PowerPivot-Arbeitsmappen auf einer SharePoint-Website<br /><br /> Erstellen von Datendienstdokumenten in einer Datenfeedbibliothek|  
|Leseberechtigung|Zugriff auf PowerPivot-Arbeitsmappen als externe Datenquelle, wobei die Arbeitsmappen-URL explizit in einem Verbindungsdialogfeld eingegeben wird (z. B. im Datenverbindungs-Assistenten von Microsoft Excel).|  
|Nur anzeigen|Anzeigen von PowerPivot-Arbeitsmappen<br /><br /> Anzeigen des Datenaktualisierungsverlaufs<br /><br /> Herstellen einer Verbindung mit einer PowerPivot-Arbeitsmappe auf einer SharePoint-Website, um die Daten auf andere Weise erneut zu nutzen<br /><br /> Laden Sie eine Momentaufnahme der Arbeitsmappe herunter. Die Momentaufnahme ist eine statische Kopie der Daten, ohne Slicer, Filter, Formeln oder Datenverbindungen. Der Inhalt der Momentaufnahme entspricht den Zellenwerten im Browserfenster.|  
  
##  <a name="excel"></a> Excel Services – sicherheitsüberlegungen für PowerPivot-Arbeitsmappen  
 Die serverseitige Verarbeitung von PowerPivot-Abfragen ist eng mit Excel Services verbunden. Die Produktintegration beginnt auf Dokumentebene, auf der PowerPivot-Arbeitsmappen als Excel-Arbeitsmappendateien (.xlsx) angesehen werden, die PowerPivot-Daten enthalten oder darauf verweisen. Es gibt keine separate Dateierweiterung für eine PowerPivot-Arbeitsmappe.  
  
 Wenn eine PowerPivot-Arbeitsmappe auf einer SharePoint-Website geöffnet wird, liest Excel Services die eingebettete PowerPivot-Datenverbindungszeichenfolge und leitet die Anforderung an den lokalen OLE DB-Anbieter für SQL Server Analysis Services weiter. Der Anbieter übergibt die Verbindungsinformationen daraufhin an einen PowerPivot-Server in der Farm. Damit die Anforderungen ungehindert zwischen den zwei Servern ausgetauscht werden können, muss Excel Services so konfiguriert werden, dass die für PowerPivot für SharePoint erforderlichen Einstellungen verwendet werden.  
  
 In Excel Services werden sicherheitsbezogene Konfigurationseinstellungen für Speicherorte, Datenanbieter und Datenverbindungsbibliotheken angegeben, die als vertrauenswürdig eingestuft wurden. In der folgenden Tabelle werden die Einstellungen beschrieben, die den PowerPivot-Datenzugriff aktivieren oder verbessern. Wenn eine Einstellung hier nicht aufgeführt wird, hat sie keine Auswirkungen auf PowerPivot-Serververbindungen. Anweisungen zum Angeben dieser Einstellungen Schritt für Schritt finden Sie im Abschnitt "Aktivieren von Excel Services" [Erstkonfiguration &#40;PowerPivot für SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md).  
  
> [!NOTE]  
>  Die meisten sicherheitsbezogenen Einstellungen gelten für vertrauenswürdige Speicherorte. Wenn Sie die Standardwerte beibehalten oder andere Werte für verschiedene Websites verwenden möchten, können Sie einen zusätzlichen vertrauenswürdigen Speicherort für Websites mit PowerPivot-Daten erstellen und dann die folgenden Einstellungen nur für diese Websites konfigurieren. Weitere Informationen finden Sie unter [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
|Bereich|Einstellung|Description|  
|----------|-------------|-----------------|  
|Webanwendung|Windows-Authentifizierungsanbieter|PowerPivot konvertiert ein von Excel Services abgerufenes Forderungstoken in eine Windows-Benutzeridentität. Jede Webanwendung, die Excel Services als Ressource verwendet, muss für die Verwendung des Anbieters der Windows-Authentifizierung konfiguriert sein.|  
|Vertrauenswürdiger Speicherort|Speicherorttyp|Für diesen Wert muss **Microsoft SharePoint Foundation**festgelegt werden. PowerPivot-Server rufen eine Kopie der XLSX-Datei ab und laden sie auf einen Analysis Services-Server in der Farm hoch. Der Server kann nur XLSX-Dateien aus einer Inhaltsbibliothek abrufen.|  
||Externe Daten zulassen|Für diesen Wert muss **Vertrauenswürdige Datenverbindungsbibliotheken und eingebettete Verbindungen**festgelegt werden. PowerPivot-Datenverbindungen sind in die Arbeitsmappe eingebettet. Wenn Sie keine eingebetteten Verbindungen zulassen, können Benutzer den PivotTable-Cache anzeigen, aber eine Interaktion mit PowerPivot-Daten kann nicht stattfinden.|  
||Beim Aktualisieren warnen|Dieser Wert sollte deaktiviert werden, wenn Sie Arbeitsmappen und Berichte mithilfe des PowerPivot-Katalogs speichern. Der PowerPivot-Katalog umfasst eine Dokumentvorschaufunktion, die am besten funktioniert, wenn Beim Öffnen aktualisieren und Beim Aktualisieren warnen deaktiviert sind.|  
|Vertrauenswürdige Datenanbieter|MSOLAP.4<br /><br /> MSOLAP.5|MSOLAP.4 ist standardmäßig eingeschlossen, aber der Zugriff auf PowerPivot-Daten erfordert, dass der MSOLAP.4-Anbieter der SQL Server 2008 R2-Version entspricht.<br /><br /> MSOLAP.5 wird mit der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version von PowerPivot für SharePoint installiert.<br /><br /> Entfernen Sie diese Anbieter nicht aus der Liste vertrauenswürdiger Datenanbieter. In einigen Fällen kann es erforderlich sein, zusätzliche Kopien dieses Anbieters auf weiteren SharePoint-Servern in der Farm zu installieren. Weitere Informationen finden Sie unter [Installieren des OLE DB-Anbieters für Analysis Services auf SharePoint-Servern](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).|  
|Vertrauenswürdige Datenverbindungsbibliotheken|Optional.|Sie können Office Data Connection (ODC)-Dateien in PowerPivot-Arbeitsmappen verwenden. Wenn Sie Verbindungsinformationen mithilfe von ODC-Dateien für lokale PowerPivot-Arbeitsmappen bereitstellen, können Sie der Bibliothek die gleichen ODC-Dateien hinzufügen.|  
|Benutzerdefinierte Funktionsassembly|Nicht verfügbar.|Benutzerdefinierte Funktionsassemblys, die Sie für Excel Services erstellen und bereitstellen, werden von PowerPivot für SharePoint ignoriert. Wenn Sie benutzerdefinierte Assemblys für ein bestimmtes Verhalten benötigen, beachten Sie, dass die von Ihnen erstellten benutzerdefinierten Funktionen bei der Verarbeitung von PowerPivot-Abfragen nicht verwendet werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von PowerPivot-Dienstkonten](configure-power-pivot-service-accounts.md)   
 [Konfigurieren des unbeaufsichtigten PowerPivot unbeaufsichtigte Datenaktualisierungskonto &#40;PowerPivot für SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)   
 [Erstellen eines vertrauenswürdigen Speicherorts für PowerPivot-Websites in der Zentraladministration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)   
 [PowerPivot-Sicherheitsarchitektur](http://go.microsoft.com/fwlink/?linkID=220970)  
  
  
