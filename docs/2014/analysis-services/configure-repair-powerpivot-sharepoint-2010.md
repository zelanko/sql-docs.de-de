---
title: Konfigurieren oder Reparieren von PowerPivot für SharePoint 2010 (PowerPivot-Konfigurationstool) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d61f49c5-efaa-4455-98f2-8c293fa50046
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3aad2530c6f8506dd3da6224c9d91f5ae46f9f27
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057371"
---
# <a name="configure-or-repair-powerpivot-for-sharepoint-2010-powerpivot-configuration-tool"></a>Konfigurieren oder Reparieren von PowerPivot für SharePoint 2010 (PowerPivot-Konfigurationstool)
  Verwenden Sie das PowerPivot-Konfigurationstool, um eine Installation von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] PowerPivot für SharePoint 2010 zu konfigurieren oder zu reparieren. Das Konfigurationstool durchsucht zunächst das System und gibt dann eine Liste von Aktionen zurück, die notwendig sind, um eine Installation abzuschließen oder zu reparieren. Die [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Setup-Assistent installiert das PowerPivot-Konfigurationstool für SharePoint 2010 sowie ein PowerPivot-Konfigurationstool für SharePoint 2013. In diesem Thema wird das PowerPivot-Konfigurationstool für SharePoint 2010 beschrieben. Weitere Informationen zu SharePoint 2010 finden Sie unter [konfigurieren oder Reparieren von PowerPivot für SharePoint 2013 &#40;PowerPivot-Konfigurationstool&#41;](power-pivot-sharepoint/configure-or-repair-power-pivot-for-sharepoint-2013.md).  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010  
  
 
  
##  <a name="bkmk_before"></a> Vorbereitungen  
 Das PowerPivot für SharePoint 2010-Konfigurationstool sucht nach Programmdateien, Registrierungseinstellungen und verfügbaren Ports. Lesen Sie die folgenden Ausführungen, um die Tools optimal zu nutzen.  
  
-   Allgemeine Anforderungen zum Ausführen des Konfigurationstools [PowerPivot-Konfigurationstools](power-pivot-sharepoint/power-pivot-configuration-tools.md).  
  
-   PowerPivot für SharePoint 2010 setzt voraus, dass Webanwendungen für die Authentifizierung im klassischen Modus konfiguriert werden. Wenn die Anwendung vom PowerPivot für SharePoint 2010-Konfigurationstool für Sie erstellt wird, ist sie für den klassischen Modus konfiguriert.  
  
-   Port 80 muss verfügbar sein, wenn eine der ausgewählten Aufgaben die Erstellung und Konfiguration einer Webanwendung vom Konfigurationstool erwartet.  
  
##  <a name="bkmk_using"></a> Mithilfe des PowerPivot-Konfigurationstools  
 Die erste Seite des Tools enthält eine Zusammenfassung der Eingabewerte, die zum Konfigurieren der SharePoint-Farm verwendet werden. Zusätzlich zu den von Ihnen angegebenen Eingabewerten werden Standardwerte zum Konfigurieren des Systems verwendet. Standardnamen werden für Dienstanwendungen, Dienstanwendungsdatenbanken und Dienstanwendungseigenschaften verwendet.  
  
> [!TIP]  
>  Wenn das PowerPivot-Konfigurationstool den Computer durchsucht und im linken Bereich eine leere Aufgabenliste zurückgibt, müssen keine Funktionen oder Einstellungen konfiguriert werden. Um die SharePoint- oder PowerPivot-Konfiguration zu ändern, verwenden Sie Windows PowerShell oder die Verwaltungsseiten in der SharePoint-Zentraladministration. Weitere Informationen finden Sie unter [PowerPivot-Serververwaltung und-Konfiguration in der Zentraladministration](power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md).  
  
 Werte für Dienstkonten werden für mehrere Dienste verwendet. Das PowerPivot-Konfigurationstool verwendet z. B. das Standardkonto auf der ersten Seite, um alle Anwendungspoolidentitäten festzulegen. Sie können später diese Konten ändern, indem Sie die Dienstanwendungseigenschaften in der Zentraladministration ändern.  
  
-   Eine Ausnahme von dieser Regel im PowerPivot für SharePoint 2010-Konfigurationstool ist das Analysis Services-Dienstkonto. Dieses Konto wird während des Setups angegeben, und geben Sie ein Kennwort für dieses Konto in der **registrieren Sie SQL Server Analysis Services (PowerPivot auf lokalen Server)** Aktion. Die Zusammenfassungsseite enthält kein Feld für dieses Kennwort, stellen Sie deshalb sicher, es auf der Seite für diese Aktion einzugeben.  
  
 Das Tool stellt eine Schnittstelle im Registerkartenformat bereit, die Parametereingaben, das Windows PowerShell-Skript und Statusmeldungen umfasst.  
  
 Das PowerPivot-Konfigurationstool verwendet Windows PowerShell, um den Server zu konfigurieren. Klicken Sie auf die **Skript** Tab, um das Windows PowerShell-Skript zu überprüfen der.  
  
 ![Benutzeroberfläche des Konfigurationstools](media/ssas-pctui.gif "-Konfigurationstool-Benutzeroberfläche")  
  
##  <a name="bkmk_steps"></a> Konfigurationsschritte  
 Der Link zum Konfigurationstool ist nur sichtbar, wenn PowerPivot für SharePoint 2010 auf dem lokalen Server installiert ist.  
  
1.  Auf der **starten** Sie im Menü **Programme**, klicken Sie auf [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], klicken Sie auf **Konfigurationstools**, und klicken Sie dann auf **PowerPivot-Konfigurationstool** .  
  
2.  Klicken Sie auf **PowerPivot für SharePoint konfigurieren oder reparieren**.  
  
3.  Erweitern Sie das Fenster auf Vollbildgröße. Am unteren Rand des Fensters wird eine Schaltflächenleiste angezeigt, die die Befehle **Überprüfen**, **Ausführen**und **Beenden** enthält.  
  
4.  **Standardkonto:** Geben Sie auf der Registerkarte **Parameter**ein Domänenbenutzerkonto für Benutzername für Standardkonto ein. Dieses Konto wird verwendet, um grundlegende Dienste bereitzustellen, einschließlich des PowerPivot-Dienstanwendungspools. Geben Sie kein integriertes Konto wie Network Service oder Local System an. Das Tool blockiert Konfigurationen, bei denen integrierte Konten angegeben werden.  
  
     **Passphrase:** Geben Sie eine Passphrase ein. Bei einer neuen SharePoint-Farm wird die Passphrase immer dann verwendet, wenn Sie der SharePoint-Farm einen neuen Server oder eine Anwendung hinzufügen. Wenn die Farm bereits vorhanden ist, geben Sie die Passphrase ein, die es Ihnen ermöglicht, der Farm eine Serveranwendung hinzuzufügen.  
  
5.  **Port:** Geben Sie optional eine Portnummer für die Verbindung mit der Webanwendung für die Zentraladministration an, oder verwenden Sie die bereitgestellte, zufällig generierte Nummer. Das Konfigurationstool überprüft, ob die Nummer verfügbar ist, bevor sie als Option angeboten wird.  
  
6.  Klicken Sie auf **SQL Server Analysis Services (PowerPivot) auf dem lokalen Server registrieren**.  
  
     Geben Sie das Kennwort des Analysis Services-Dienstkontos ein.  
  
7.  Überprüfen Sie optional die verbleibenden Eingabewerte, die zum Abschließen der jeweiligen Aktion verwendet werden. Weitere Informationen über die einzelnen Aktionen finden Sie unter [Eingabewerte für die Serverkonfiguration](#bkmk_input) in diesem Thema.  
  
8.  Entfernen Sie optional alle Aktionen, die Sie nicht verarbeiten möchten. Wenn Sie z. B. Secure Store Service später konfigurieren möchten, klicken Sie auf **Secure Store Service konfigurieren**, und deaktivieren Sie dann das Kontrollkästchen **Diese Aktion in Taskliste einschließen**.  
  
9. Klicken Sie auf **Überprüfen** , um zu überprüfen, ob das Tool genügend Informationen hat, um die Aktionen in der Liste zu verarbeiten.  
  
    > [!NOTE]  
    >  Wenn Sie einen Farmkonfigurationsfehler erhalten, kann dies daran liegen, dass SharePoint 2010 Server SP1 nicht installiert ist.  
  
10. Klicken Sie auf **Ausführen** , um alle Aktionen in der Aufgabenliste zu verarbeiten. Die Schaltfläche **Ausführen** ist aktiviert, nachdem Sie die Aktionen überprüft haben. Wenn **Ausführen** nicht aktiviert ist, klicken Sie zuerst auf **Überprüfen** .  
  
11. [Überprüfen der PowerPivot für SharePoint-Installation](instances/install-windows/verify-a-power-pivot-for-sharepoint-installation.md).  
  
##  <a name="bkmk_input"></a> Eingabewerte für die Serverkonfiguration  
 Das PowerPivot-Konfigurationstool verwendet eine Kombination von Eingabewerten, die Sie eingeben, und Standardwerten, die es erkennt oder automatisch verwendet.  
  
 Welche Aktionen im Konfigurationstool aufgelistet sind, hängt von der aktuellen Konfiguration der SharePoint-Farmen ab. Wenn die SharePoint-Farm beispielsweise bereits konfiguriert ist, sind im Tool keine Aktionen aufgeführt. Sie können das Tool jederzeit ausführen, um zu konfigurieren, zu reparieren oder Konfigurationsfehler zu erkennen. Wenn erforderliche Dienste wie Excel Services oder Secure Store Service nicht in der Farm ausgeführt werden, erkennt das Tool die fehlenden Dienste und stellt Optionen bereit, um sie zu aktivieren. Wenn keine Aktionen erforderlich sind, ist die Aufgabenliste leer.  
  
 In der folgenden Tabelle werden die Werte beschrieben, die für die Serverkonfiguration verwendet werden.  
  
|Seite|Eingabewert|Quelle|Description|  
|----------|-----------------|------------|-----------------|  
|**Konfigurieren oder Reparieren von PowerPivot für SharePoint**|Standardkonto|Aktueller Benutzer|Das Standardkonto ist ein Windows-Domänenbenutzerkonto, das verwendet wird, um gemeinsame Dienste in der Farm bereitzustellen. Es wird verwendet, um die PowerPivot-Dienstanwendung, Secure Store Service, Excel Services, die Webanwendungspoolidentität, den Websitesammlungsadministrator und das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot bereitzustellen.<br /><br /> Standardmäßig wird vom Tool das Domänenkonto des aktuellen Benutzers eingegeben. Außer wenn Sie einen Server zu Auswertungszwecken konfigurieren, sollten Sie das Konto durch ein anderes Domänenbenutzerkonto ersetzen.<br /><br /> Sie können Dienstidentitäten später auch in der Zentraladministration ändern.<br /><br /> Optional können Sie im PowerPivot-Konfigurationstool folgende dedizierte Konten angeben:<br /><br /> Webanwendung, anhand der Seite **Standardwebanwendung erstellen** (vorausgesetzt, das Tool erstellt eine Webanwendung für die Farm).<br /><br /> PowerPivot für die unbeaufsichtigte datenaktualisierung Kontos mit den **unbeaufsichtigtes Konto für Datenaktualisierung erstellen** Seite in diesem Tool.|  
||Datenbankserver|Lokale benannte PowerPivot-Instanz, falls verfügbar|Wenn eine Datenbank-Engine-Instanz als benannte PowerPivot-Instanz installiert ist, füllt das Tool das Datenbankserverfeld mit dieser Instanz auf. Wenn Sie die Datenbank-Engine nicht installiert haben, ist dieses Feld leer. Sie müssen eine Instanz bereitstellen. Es kann irgendeine Version oder eine Ausgabe von SQL Server sein, die für SharePoint-Farmen unterstützt wird.|  
||Passphrase|Benutzereingabe|Wenn Sie eine neue Farm erstellen, ist die Passphrase, die Sie eingeben, die Passphrase für die Farm. Wenn Sie PowerPivot für SharePoint zu einer vorhandenen Farm hinzufügen, müssen Sie die Passphrase bereitstellen, die für die Farm bei der Erstellung definiert wurde.|  
||SharePoint-Zentraladministration-Port|Standard, falls erforderlich|Wenn die Farm nicht konfiguriert ist, stellt das Tool Optionen zum Erstellen der Farm bereit, einschließlich eines HTTP-Endpunkts zur Zentraladministration. Es verwendet standardmäßig eine zufällig generierte Portnummer, die nicht in Gebrauch ist.|  
|**Neue Farm konfigurieren**|Datenbankserver<br /><br /> Farmkonto<br /><br /> Passphrase<br /><br /> SharePoint-Zentraladministration-Port|Standard, falls erforderlich|Es werden standardmäßig die Einstellungen übernommen, die Sie auf der Hauptseite eingegeben haben.|  
|**Lokale Dienstinstanz konfigurieren**|Analysis Services-Dienstkontokennwort|Benutzereingabe|Geben Sie das Kennwort des Analysis Services-Dienstkontos in der **registrieren Sie SQL Server Analysis Services (PowerPivot) auf dem lokalen Server** Seite.<br /><br /> Das Dienstkonto wurde während des Setups angegeben. Sie müssen jetzt das Kennwort als Eingabe zum Registrieren der lokalen Dienstinstanz bei SharePoint eingeben.|  
|**PowerPivot-Dienstanwendung erstellen**|PowerPivot-Dienstanwendungsname|Default|Der Standardname lautet PowerPivot-Standarddienstanwendung. Sie können einen anderen Wert im Tool ersetzen.|  
||Datenbankserver für die PowerPivot-Dienstanwendung|Default|Der Datenbankserver, von dem die Datenbank der PowerPivot-Dienstanwendung gehostet wird. Der Standardservername ist der Name des für die Farm verwendeten Datenbankservers. Sie können einen anderen Wert im Tool ersetzen.|  
||Datenbankname der PowerPivot-Dienstanwendung|Default|Der Standarddatenbankname basiert auf dem Dienstanwendungsnamen, gefolgt von einer GUID, um einen eindeutigen Namen sicherzustellen. Sie können einen anderen Wert im Tool ersetzen.|  
||Arbeitsmappen aktualisieren, um die Datenaktualisierung zuzulassen|Benutzereingabe|Die Datenaktualisierung schlägt fehl und wird nicht für SQL Server 2008 R2-PowerPivot-Arbeitsmappen unterstützt. Die Option **Aktualisieren von Arbeitsmappen aktualisieren, um Daten zu ermöglichen** aktualisiert die Arbeitsmappen auf SQL Server 2012 PowerPivot-Version.|  
|**Standardwebanwendung erstellen**|Name der Webanwendung|Standard, falls erforderlich|Wenn keine Webanwendungen vorhanden sind, erstellt das Tool eine. Die Webanwendung wird für die Authentifizierung im klassischen Modus und das Lauschen konfiguriert **port 80**. Die maximale Dateiuploadgröße wird auf 2.047 MB festgelegt, den von SharePoint zugelassenen Höchstwert. Die größere Dateiuploadgröße dient der Unterstützung großer PowerPivot-Dateien.|  
||URL|Standard, falls erforderlich|Das Tool erstellt eine URL auf Grundlage des Servernamens und verwendet die gleichen Dateinamenskonventionen wie SharePoint.|  
||Webanwendungspool|Standard, falls erforderlich|Das Tool erstellt in IIS einen Standardanwendungspool.|  
||Konto und Kennwort des Webanwendungspools|Standard, falls erforderlich|Das Anwendungspoolkonto basiert auf dem Standardkonto, aber Sie können es im Tool überschreiben.|  
||Webanwendungsdatenbankserver|Standard, falls erforderlich|Die Standarddatenbankinstanz ist vorausgewählt, um die Anwendungsdatenbank zu speichern, aber Sie können im Tool eine andere SQL Server-Instanz angeben.|  
||Webanwendungsdatenbankname|Standard, falls erforderlich|Der Datenbankname basiert auf den Dateinamenskonventionen von SharePoint, aber Sie können einen anderen Namen auswählen.|  
|**Webanwendungslösung bereitstellen**|URL|Standard, falls erforderlich|Die Standard-URL wird von der Standardwebanwendung übernommen.|  
||Maximale Dateigröße (in MB)|Standard, falls erforderlich|Die Standardeinstellung ist 2.047. SharePoint-Dokumentbibliotheken verfügen ebenfalls über eine maximale Größe, und die Einstellung der Dokumentbibliothek sollte von der PowerPivot-Einstellung nicht überschritten werden. Weitere Informationen finden Sie unter [konfigurieren Datei hochladen Maximalgröße &#40;PowerPivot für SharePoint&#41;](power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).|  
|**Websitesammlung erstellen**|Websiteadministrator|Standard, falls erforderlich|Das Tool verwendet das Standardkonto. Sie können es auf der Seite **Websitesammlung erstellen** überschreiben.|  
||Kontakt-E-Mail|Standard, falls erforderlich|Wenn Microsoft Outlook auf dem Server konfiguriert ist, verwendet das Tool die E-Mail-Adresse des aktuellen Benutzers. Andernfalls wird ein Platzhalterwert verwendet.|  
||Website-URL|Standard, falls erforderlich|Das Tool erstellt die Website-URL und verwendet die gleichen URL-Namenskonventionen wie SharePoint.|  
||Websitetitel|Standard, falls erforderlich|Das Tool fügt **PowerPivot-Website** als Standardtitel hinzu.|  
|**PowerPivot-Funktion in einer Websitesammlung aktivieren**|Website-URL||Die URL der Websitesammlung, für die Sie PowerPivot-Funktionen aktivieren.|  
||Premium-Funktion für diese Website aktivieren||Aktivieren Sie die SharePoint-Websitefunktion "PremiumSite".|  
|**Secure Store Service-Anwendung erstellen**|Name der Dienstanwendung||Geben Sie den Namen für die Secure Store Service-Anwendung ein.|  
||Datenbankserver||Geben Sie den Namen des Datenbankservers ein, der für die Secure Store Service-Anwendung verwendet werden soll.|  
|**Proxy für Secure Store Service-Anwendung erstellen**|Name der Dienstanwendung||Geben Sie den Namen für die Secure Store Service-Anwendung ein.|  
||Proxy für Dienstanwendung||Geben Sie den Namen für den Proxy der Secure Store Service-Anwendung ein.  Der Name wird in der Standardverbindungsgruppe angezeigt, über die Anwendungen den SharePoint-Inhaltswebanwendungen zugeordnet werden.|  
|**Secure Store Service-Hauptschlüssel aktualisieren**|Proxy für Dienstanwendung||Geben Sie den Namen für den Proxy der Secure Store Service-Anwendung ein.|  
||Passphrase||Der Hauptschlüssel wird für die Datenverschlüsselung verwendet. Die zum Generieren des Schlüssels verwendete Passphrase entspricht standardmäßig der Passphrase, die zum Bereitstellen neuer Server in der Farm verwendet wird. Sie können die Standardpassphrase durch eine eindeutige Passphrase ersetzen.|  
|**Unbeaufsichtigtes Konto für "datarefresh" erstellen**|Zielanwendungs-ID||Die Anwendungs-ID kann beschreibender Text sein.|  
||Anzeigename für die Zielanwendung|||  
||Benutzername und Kennwort des unbeaufsichtigten Kontos||Geben Sie die Anmeldeinformationen eines Windows-Benutzerkontos ein, das von der Zielanwendung verwendet und zur Ausführung einer unbeaufsichtigten Datenaktualisierung verwendet wird.|  
||Website-URL||Geben Sie die Website-URL der Websitesammlung ein, die der Zielanwendung zugeordnet ist. Um Zuordnungen mit zusätzlichen Websitesammlungen herzustellen, verwenden Sie die SharePoint-Zentraladministration.|  
|**Excel Services-Dienstanwendung erstellen**|Name der Dienstanwendung||Geben Sie einen Namen für die Dienstanwendung ein. Auf dem Datenbankserver der SharePoint-Farm wird für die Dienstanwendung eine Datenbank mit demselben Namen erstellt.|  
|**MSOLAP. 5 als vertrauenswürdigen Anbieter hinzufügen**|Name der Dienstanwendung||Excel Services in SharePoint 2010 verwenden den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] OLE DB-Anbieter, um eine Verbindung mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Daten herzustellen. Durch diesen Schritt wird die Version des OLE DB-Anbieters, der mit PowerPivot für SharePoint installiert wird, als vertrauenswürdiger Anbieter für Excel Services hinzugefügt.|  
||PowerPivot-Servername|||  
|||||  
  
 Wenn das PowerPivot-Konfigurationstool die Farm erstellt, legt es die erforderlichen Datenbanken auf dem Datenbankserver an und verwendet die gleichen Dateinamenskonventionen wie SharePoint. Sie können den Farmdatenbanknamen nicht ändern.  
  
 Wenn das Tool eine Websitesammlung erstellt, erstellt es eine Inhaltsdatenbank auf dem Datenbankserver und verwendet die gleichen Dateinamenskonventionen wie SharePoint. Sie können den Inhaltsdatenbanknamen nicht ändern.  
  
##  <a name="bkmk_nextsteps"></a> Nächste Schritte  
 Nach Abschluss einer Serverinstallation gibt es einige weitere Schritte, die Sie durchführen sollten:  
  
-   Gewähren Sie Einzelbenutzern und Gruppen SharePoint-Berechtigungen. Dieser Schritt ist notwendig, um den Zugriff auf Websites und Inhalte zu ermöglichen.  
  
-   Ändern Sie die Identitäten des Dienstanwendungspools für die Ausführung unter einem anderen Konto. Das Angeben verschiedener Identitäten für Dienste und Anwendungen ist ein bewährtes Verfahren für die sichere Bereitstellung von SharePoint.  
  
-   Erstellen Sie zusätzliche vertrauenswürdige Websites in Excel Services, damit Sie Berechtigungen und Konfigurationseinstellungen verändern können, die am besten für den PowerPivot-Datenzugriff funktionieren.  
  
-   Installieren Sie ADO.NET Data Services 3.5 SP1, um den Export von Datenfeeds aus SharePoint-Listen zu ermöglichen.  
  
-   Installieren Sie häufig verwendete Datenanbieter, um serverseitige Datenaktualisierung zu aktivieren.  
  
-   Laden Sie das PowerPivot-Erstellungstool auf Ihren Arbeitsstationscomputer herunter, um eine PowerPivot-Arbeitsmappe zu erstellen und dann in SharePoint zu veröffentlichen. Durch die Installation des Tools und die Veröffentlichung einer PowerPivot-Arbeitsmappe wird der Installationszyklus abgeschlossen und die Interoperabilität der soeben installierten Serverkomponenten überprüft.  
  
### <a name="grant-sharepoint-permissions-to-workbook-users"></a>Gewähren von SharePoint-Berechtigungen für Arbeitsmappenbenutzer  
 Benutzer benötigen SharePoint-Berechtigungen, bevor sie Arbeitsmappen veröffentlichen oder anzeigen können. Achten Sie darauf, dass Sie gewähren **Ansicht** Berechtigungen für Benutzer, die veröffentlichte Arbeitsmappen anzeigen müssen und **mitwirken** Berechtigungen für Benutzer, die Arbeitsmappen veröffentlichen oder verwalten. Sie müssen Websitesammlungsadministrator sein, um Berechtigungen erteilen zu können.  
  
1.  Klicken Sie auf der Website auf **Websiteaktionen**.  
  
2.  Klicken Sie auf **Websiteberechtigungen**.  
  
3.  Erstellen Sie Gruppen nach Bedarf, wenn Sie eine Gruppe von Benutzern mit der Berechtigung **Teilnehmen** und eine andere Gruppe einrichten möchten, in der Benutzer nur über die Berechtigung **Anzeigen** verfügen.  
  
4.  Geben Sie die Windows-Domänenbenutzer- oder -Gruppenkonten ein, die in den Gruppen enthalten sein sollen. Verwenden Sie wie zuvor keine E-Mail-Adressen bzw. keine Verteilergruppe, wenn die Anwendung für die klassische Authentifizierung konfiguriert wurde.  
  
### <a name="install-adonet-data-services-35-sp1"></a>Installieren von ADO.NET Data Services 3.5 SP1  
 ADO.NET Data Services sind für einen Datenfeedexport von SharePoint-Listen erforderlich. Da diese Komponente nicht im Programm PrerequisiteInstaller von SharePoint 2010 enthalten ist, müssen Sie sie manuell installieren.  
  
1.  Wechseln Sie zu den Hardware- und softwareanforderungen für SharePoint 2010 [bestimmen von Hardware- und Softwareanforderungen (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  Suchen Sie unter Installieren der erforderlichen Software den Link für ADO.NET Data Services 3.5, der dem verwendeten Betriebssystem entspricht.  
  
3.  Klicken Sie auf den Link, und führen Sie das Setupprogramm aus, durch das der Dienst installiert wird.  
  
### <a name="install-data-providers-used-in-data-refresh-and-check-user-permissions"></a>Installieren von in der Datenaktualisierung verwendeten Datenanbietern und Überprüfen von Benutzerberechtigungen  
 Die serverseitige Datenaktualisierung ermöglicht Benutzern das erneute Importieren aktualisierter Daten in ihre Arbeitsmappen in unbeaufsichtigtem Modus. Für die erfolgreiche Ausführung der Datenaktualisierung muss auf dem Server der gleiche Datenanbieter wie für den ursprünglichen Import der Daten vorhanden sein. Darüber hinaus sind für das Benutzerkonto, unter dem die Datenaktualisierung ausgeführt wird, oft Leseberechtigungen für die externen Datenquellen erforderlich. Überprüfen Sie die Anforderungen für das Aktivieren und Konfigurieren der Datenaktualisierung, um ein erfolgreiches Ergebnis sicherzustellen. Weitere Informationen finden Sie unter [PowerPivot-Datenaktualisierung mit SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md).  
  
### <a name="change-application-pool-and-service-identities-in-sharepoint"></a>Ändern des Anwendungspools und der Dienstidentitäten in SharePoint  
 Das PowerPivot-Konfigurationstool stellt Farmfunktionen, Anwendungen und Dienste zur Ausführung unter einem einzelnen Konto bereit. Dies vereinfacht die Installation, führt aber nicht zu einer Bereitstellung, die die Sicherheitsanforderungen einer SharePoint-Farm erfüllt. Um eine stabilere Bereitstellung zu erzielen, ändern Sie die Anwendungspools und Dienstidentitäten so, dass sie unter anderen Konten ausgeführt werden, nachdem das Setup abgeschlossen ist. Weitere Informationen finden Sie unter [Konfigurieren von PowerPivot-Dienstkonten](power-pivot-sharepoint/configure-power-pivot-service-accounts.md).  
  
### <a name="create-additional-trusted-sites-in-excel-services"></a>Erstellen von zusätzlichen vertrauenswürdigen Websites in Excel Services  
 Sie können vertrauenswürdige Websites in Excel Services hinzufügen, um die Berechtigungen und Konfigurationseinstellungen auf Websites zu variieren, die Excel-Arbeitsmappen und PowerPivot-Daten bereitstellen. Weitere Informationen finden Sie unter [Create a trusted location for PowerPivot sites in Central Administration](power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
### <a name="add-servers-or-applications"></a>Hinzufügen von Servern oder Anwendungen  
 Wenn Sie mit der Zeit feststellen, dass zusätzlicher Datenspeicher und zusätzliche Verarbeitungskapazität erforderlich sind, können Sie der Farm eine zweite Serverinstanz mit PowerPivot für SharePoint hinzufügen. Anweisungen hierzu finden Sie unter [Bereitstellungsprüfliste: Horizontales durch Hinzufügen von PowerPivot-Servern zu einer SharePoint 2010-Farm](../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).  
  
## <a name="additional-resources"></a>Zusätzliche Ressourcen  
 ![SharePoint-Einstellungen](media/as-sharepoint2013-settings-gear.gif "SharePoint Einstellungen") [Submit Feedback und Kontaktinformationen Informationen über Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Konfigurationstools](power-pivot-sharepoint/power-pivot-configuration-tools.md)   
 [PowerPivot-Serververwaltung und -konfiguration in der Zentraladministration](power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  