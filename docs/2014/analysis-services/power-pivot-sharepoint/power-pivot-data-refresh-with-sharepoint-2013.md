---
title: PowerPivot-Datenaktualisierung mit SharePoint 2013 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 34f03407-2ec4-4554-b16b-bc9a6c161815
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04c366bc668fe09d1ebf57d169587ec11476f707
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62749708"
---
# <a name="powerpivot-data-refresh-with-sharepoint-2013"></a>PowerPivot-Datenaktualisierung mit SharePoint 2013
  Beim Aktualisieren von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Datenmodellen in SharePoint 2013 wird standardmäßig Excel Services als Hauptkomponente zum Laden und Aktualisieren von Datenmodellen auf einer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz verwendet, die im SharePoint-Modus ausgeführt wird. Der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server wird außerhalb der SharePoint-Farm ausgeführt.  
  
 Bei der vorherigen Datenaktualisierungsarchitektur wurden Datenmodelle in einer im SharePoint-Modus ausgeführten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz ausschließlich mithilfe des PowerPivot-Systemdiensts geladen und aktualisiert. Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz wurde lokal auf dem PowerPivot-Anwendungsserver ausgeführt. In der neuen Architektur wird außerdem eine neue Methode eingeführt, um Zeitplaninformationen als Metadaten des Arbeitsmappenelements in der Dokumentbibliothek zu verwalten. Die Architektur in SharePoint 2013 Excel Services unterstützt sowohl die **interaktive Datenaktualisierung** als auch die **planmäßige Datenaktualisierung**.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013  
  
 **In diesem Thema:**  
  
-   [Interactive Data Refresh](#bkmk_interactive_refresh)  
  
-   [Windows-Authentifizierung mit Arbeitsmappen-Datenverbindungen und interaktiver Datenaktualisierung](#bkmk_windows_auth_interactive_data_refresh)  
  
-   [Scheduled Data Refresh](#bkmk_scheduled_refresh)  
  
-   [Architektur der geplante Datenaktualisierung in SharePoint 2013](#bkmk_refresh_architecture)  
  
-   [Zusätzliche Überlegungen zur Authentifizierung](#datarefresh_additional_authentication)  
  
-   [Weitere Informationen](#bkmk_moreinformation)  
  
## <a name="background"></a>Hintergrund  
 SharePoint Server 2013 Excel Services verwaltet die Datenaktualisierung für Excel 2013-Arbeitsmappen und löst die datenmodellverarbeitung auf einem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server, der im SharePoint-Modus ausgeführt wird. Für Excel 2010-Arbeitsmappen verwaltet Excel Services auch das Laden und Speichern von Arbeitsmappen und Datenmodellen. Allerdings verwendet Excel Services den PowerPivot-Systemdienst, um die Verarbeitungsbefehle an das Datenmodell zu senden. In der folgenden Tabelle werden die Komponenten zusammengefasst, die Verarbeitungsbefehle für die Datenaktualisierung senden, aufgeschlüsselt nach Version der Arbeitsmappe. Als Umgebung wird eine SharePoint 2013-Farm angenommen, die für die Verwendung eines [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis-Servers im SharePoint-Modus konfiguriert ist.  
  
||||  
|-|-|-|  
||Excel 2013-Arbeitsmappen|Excel 2010-Arbeitsmappen|  
|Datenaktualisierung auslösen|**Interaktive:** Authenticated User<br /><br /> **Geplant:** PowerPivot-Systemdienst|PowerPivot-Systemdienst|  
|Arbeitsmappe aus Inhaltsdatenbanken laden|SharePoint 2013 Excel Services|SharePoint 2013 Excel Services|  
|Datenmodell in Analysis Services-Instanz laden|SharePoint 2013 Excel Services|SharePoint 2013 Excel Services|  
|Verarbeitungsbefehle an Analysis Services-Instanz senden|SharePoint 2013 Excel Services|PowerPivot-Systemdienst|  
|Arbeitsmappendaten aktualisieren|SharePoint 2013 Excel Services|SharePoint 2013 Excel Services|  
|Arbeitsmappe und Datenmodell in Inhaltsdatenbank speichern|**Interaktive:** Nicht zutreffend<br /><br /> **Geplant:** SharePoint 2013 Excel Services|SharePoint 2013 Excel Services|  
  
 In der folgenden Tabelle werden die unterstützten Aktualisierungsfunktionen in einer SharePoint 2013-Farm zusammengefasst, die für die Verwendung eines [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis-Servers im SharePoint-Modus konfiguriert ist:  
  
|Arbeitsmappe erstellt in|planmäßige Datenaktualisierung|Interaktive Datenaktualisierung|  
|-------------------------|----------------------------|-------------------------|  
|2008 R2 PowerPivot für Excel|Wird nicht unterstützt. Arbeitsmappe upgraden **(\*)**|Wird nicht unterstützt. Arbeitsmappe upgraden **(\*)**|  
|2012 PowerPivot für Excel|Supported|Wird nicht unterstützt. Arbeitsmappe upgraden **(\*)**|  
|Excel 2013|Supported|Supported|  
  
 **(\*)** Weitere Informationen zum Upgraden von Arbeitsmappen finden Sie unter [Upgraden von Arbeitsmappen und planmäßige Datenaktualisierungen &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
##  <a name="bkmk_interactive_refresh"></a> Interactive Data Refresh  
 Bei der interaktiven oder manuellen Datenaktualisierung in SharePoint Server 2013 Excel Services können Datenmodelle mit Daten aus der ursprünglichen Datenquelle aktualisiert werden. Die interaktive Datenaktualisierung ist verfügbar, nachdem Sie eine Excel Services-Anwendung konfiguriert haben, indem Sie einen im SharePoint-Modus ausgeführten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server registrieren. Weitere Informationen finden Sie unter [Verwalten von Excel Services-Datenmodelleinstellungen (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx).  
  
> [!NOTE]  
>  Die interaktive Datenaktualisierung ist nur für Arbeitsmappen verfügbar, die in Excel 2013 erstellt wurden. Wenn Sie versuchen, eine Excel 2010-Arbeitsmappe zu aktualisieren, zeigt Excel Services eine Fehlermeldung ähnlich wie "PowerPivot-Vorgang fehlgeschlagen: Die Arbeitsmappe in einer früheren Version von Excel erstellt wurde, und PowerPivot kann nicht aktualisiert werden, bis die Datei aktualisiert wird". Weitere Informationen zum Upgraden von Arbeitsmappen finden Sie unter [Upgraden von Arbeitsmappen und planmäßige Datenaktualisierungen &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
 **Wichtige Punkte zur interaktiven Aktualisierung:**  
  
-   Bei der interaktiven Datenaktualisierung werden nur die Daten in der aktuellen Benutzersitzung aktualisiert. Die Daten werden nicht automatisch wieder im Arbeitsmappenelement in der SharePoint-Inhaltsdatenbank gespeichert.  
  
-   **Anmeldeinformationen:** Interaktive datenaktualisierung kann die Identität des aktuell angemeldeten Benutzers als Anmeldeinformationen oder gespeicherte Anmeldeinformationen verwenden, für die Verbindung mit der Datenquelle. Welche Anmeldeinformationen verwendet werden, hängt von den Excel Services-Authentifizierungseinstellungen ab, die für die Verbindung der Arbeitsmappe mit der externen Datenquelle definiert sind.  
  
-   **Unterstützte Arbeitsmappen:**  In Excel 2013 erstellte Arbeitsmappen.  
  
 **So aktualisieren Sie Daten:**  
  
-   Beachten Sie die Abbildung nach den Schritten.  
  
1.  Öffnen Sie in einer SharePoint-Dokumentbibliothek eine PowerPivot-Arbeitsmappe im Browser.  
  
2.  Klicken Sie im Browserfenster auf das Menü **Daten** und dann auf **Ausgewählte Verbindung aktualisieren** oder **Alle Verbindungen aktualisieren**.  
  
3.  Excel Services lädt die PowerPivot-Datenbank, verarbeitet sie und fragt sie anschließend ab, um den Excel-Arbeitsmappencache zu aktualisieren.  
  
4.  **Hinweis**: Die aktualisierte Arbeitsmappe wird nicht automatisch wieder in die Dokumentbibliothek gespeichert.  
  
 ![interaktive Datenaktualisierung](../media/as-interactive-datarefresh-sharepoint2013.gif "interaktive Datenaktualisierung")  
  
###  <a name="bkmk_windows_auth_interactive_data_refresh"></a> Windows-Authentifizierung mit Arbeitsmappen-Datenverbindungen und interaktiver Datenaktualisierung  
 Excel Services sendet dem Analysis Services-Server einen Verarbeitungsbefehl, der den Server anweist, die Identität eines Benutzerkontos anzunehmen. Um ausreichende Systemrechte zum Delegieren des Benutzeridentitätswechsels zu erhalten, benötigt das Analysis Services-Dienstkonto die Berechtigung **Einsetzen als Teil des Betriebssystems** auf dem lokalen Server. Der Analysis Services-Server muss auch in der Lage sein, die Anmeldeinformationen des Benutzers für Datenquellen zu delegieren. Das Abfrageergebnis wird an Excel Services gesendet.  
  
 Typische benutzererfahrung: Wenn ein Kunde "Alle Verbindungen aktualisieren" in einer Excel 2013-Arbeitsmappe, die ein PowerPivot-Modell enthält auswählt, eine Fehlermeldung ähnlich der folgenden angezeigt:  
  
-   **Fehler bei der Aktualisierung der externen Daten:** Fehler beim Arbeiten am Datenmodell in der Arbeitsmappe. Wiederholen Sie den Vorgang. Eine oder mehrere Datenverbindungen in dieser Arbeitsmappe können nicht aktualisiert werden.  
  
 Abhängig vom jeweiligen Datenanbieter werden im ULS-Protokoll Meldungen ähnlich den folgenden angezeigt.  
  
 **Bei SQL Native Client:**  
  
-   Fehler beim Erstellen einer externen Verbindung oder beim Ausführen einer Abfrage. Anbietermeldung: Line-of-Objekt 'DataSource', Verweis auf die ID(s) ' 20102481-39 c 8-4-d 21-bf63-68f583ad22bb', wurde angegeben, jedoch nicht verwendet wurde.  OLEDB- oder ODBC-Fehler: Ein netzwerkbezogener oder Instanzspezifischer Fehler beim Herstellen einer Verbindung mit SQL Server. Der Server wurde nicht gefunden, oder auf ihn kann nicht zugegriffen werden. Überprüfen Sie, ob der Instanzname richtig ist und ob SQL Server Remoteverbindungen zulässt. Weitere Informationen finden Sie unter SQL Server-Onlinedokumentation.; 08001; SSL-Anbieter: Das angeforderte Sicherheitspaket ist nicht vorhanden; 08001; Client kann keine Verbindung herstellen 08001; Verschlüsselung wird auf dem Client nicht unterstützt.; 08001.  , Verbindungsname: ThisWorkbookDataModel, Arbeitsmappe: Mappe1.xlsx.  
  
 **Bei Microsoft OLE DB-Anbieter für SQL Server:**  
  
-   Fehler beim Erstellen einer externen Verbindung oder beim Ausführen einer Abfrage. Anbietermeldung: Line-of-Objekt 'DataSource', auf die ID(s) '6e711bfa-b62f-4879-a177-c5dd61d9c242', wurde angegeben, jedoch nicht verwendet wurde. OLE DB- oder ODBC-Fehler. , Verbindungsname: ThisWorkbookDataModel, Arbeitsmappe: OLEDB Provider.xlsx.  
  
 **Bei .NET Framework-Datenanbieter für SQL Server:**  
  
-   Fehler beim Erstellen einer externen Verbindung oder beim Ausführen einer Abfrage. Anbietermeldung: Objekt 'DataSource', auf die ID(s) 'f5fb916c-3eac - 4D 07-a542-531524c0d44a ' verweist, aus der Zeile wurde angegeben, jedoch nicht verwendet wurde.  Fehler in der relationalen Engine. Die folgende Ausnahme ist aufgetreten, während die verwaltete IDbConnection-Schnittstelle verwendet wurde: Konnte nicht geladen werden, Datei oder Assembly ' System.Transactions, Version = 4.0.0.0, Culture = Neutral, PublicKeyToken = b77a5c561934e089' oder eine ihrer Abhängigkeiten. Entweder wurde eine geforderte Identitätswechselebene nicht geliefert, oder die gelieferte Identitätswechselebene ist unzulässig. (Ausnahme von HRESULT: 0x80070542).  , Verbindungsname: ThisWorkbookDataModel, Arbeitsmappe: NETProvider.xlsx.  
  
 **Zusammenfassung der Konfigurationsschritte** zum Konfigurieren der Berechtigung **Einsetzen als Teil des Betriebssystems** auf dem lokalen Server:  
  
1.  Fügen Sie auf dem im SharePoint-Modus ausgeführten Analysis Services-Server das Analysis Services-Dienstkonto der Berechtigung**Einsetzen als Teil des Betriebssystems**hinzu:  
  
    1.  Führen Sie "`secpol.msc`"  
  
    2.  Klicken Sie auf **Lokale Sicherheitsrichtlinie**, klicken Sie dann auf **Lokale Richtlinien**und anschließend auf **Zuweisen von Benutzerrechten**.  
  
    3.  Fügen Sie das Dienstkonto hinzu.  
  
2.  Starten Sie Excel Services neu, und führen Sie einen Neustart des Analysis Services-Servers durch.  
  
3.  Die Delegierung vom Excel Services-Dienstkonto oder vom Claims to Windows Token Service (C2WTS) zur Analyse Services-Instanz ist nicht erforderlich. Daher ist keine Konfiguration für KCD von Excel Services oder C2WTS für PowerPivot AS-Dienst erforderlich. Wenn sich die Backend-Datenquelle auf demselben Server wie die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz befindet, ist keine eingeschränkte Kerberos-Delegierung erforderlich. Allerdings benötigt das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Dienstkonto das Recht, als Teil des Betriebssystems zu agieren.  
  
 ![as_interactive_data_refresh2012SP1_windowsauth](../media/as-interactive-data-refresh2012sp1-windowsauth.gif "as_interactive_data_refresh2012SP1_windowsauth")  
  
 Weitere Informationen finden Sie unter [einsetzen als Teil des Betriebssystems](https://technet.microsoft.com/library/cc784323\(WS.10\).aspx).  
  
##  <a name="bkmk_scheduled_refresh"></a> Scheduled Data Refresh  
 **Wichtige Punkte zur geplanten Datenaktualisierung:**  
  
-   Erfordert die Bereitstellung des PowerPivot für SharePoint-Add-Ins. Weitere Informationen finden Sie unter [installieren oder Deinstallieren des PowerPivot für SharePoint-Add-in &#40;SharePoint 2013&#41;](../instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).  
  
-   Ein Benutzer konfiguriert einen Aktualisierungszeitplan für eine Arbeitsmappe. Zum geplanten Zeitpunkt sendet der PowerPivot-Systemdienst eine Anforderung an Excel Services für folgende Aktionen:  
  
    -   Laden und Verarbeiten der PowerPivot-Datenbank  
  
    -   Aktualisieren der Arbeitsmappe  
  
    -   Erneutes Speichern der Arbeitsmappe in der Inhaltsdatenbank  
  
-   **Anmeldeinformationen:** Verwendet gespeicherte Anmeldeinformationen. Verwendet nicht die Identität des aktuellen Benutzers.  
  
-   **Unterstützte Arbeitsmappen:** Arbeitsmappen erstellt wurden, mit der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot-add-in für Excel 2010 oder mit Excel 2013. In Excel 2010 mit dem [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] PowerPivot-Add-In erstellte Arbeitsmappen werden nicht unterstützt. Aktualisieren Sie die Arbeitsmappe mindestens auf das [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot-Format. Weitere Informationen zum Upgraden von Arbeitsmappen finden Sie unter [Upgraden von Arbeitsmappen und planmäßige Datenaktualisierungen &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
 So zeigen Sie die Seite **Datenaktualisierung verwalten** an:  
  
-   Beachten Sie die Abbildung nach den Schritten.  
  
1.  Klicken Sie in einer SharePoint-Dokumentbibliothek auf das Menü **Öffnen** (**...**) für eine PowerPivot-Arbeitsmappe.  
  
2.  Klicken Sie auf das zweite Menü **Öffnen** , und klicken Sie dann auf **PowerPivot-Datenaktualisierung verwalten**.  
  
3.  Klicken Sie auf der Seite **Datenaktualisierung verwalten** auf **Aktivieren** , und konfigurieren Sie dann den Aktualisierungszeitplan.  
  
4.  Zum angegebenen Zeitpunkt sendet der PowerPivot-Systemdienst eine Anforderung an Excel Services für folgende Aktionen:  
  
    -   Laden und Verarbeiten des PowerPivot-Datenmodells  
  
    -   Aktualisieren der Arbeitsmappe  
  
    -   Erneutes Speichern der Arbeitsmappe in der Inhaltsdatenbank  
  
 ![Verwalten von Data Refresh-Kontextmenü](../media/as-manage-datarefresh-sharepoint2013.gif "datenkontextmenü für die datenaktualisierung verwalten")  
  
> [!TIP]  
>  Informationen zum Aktualisieren von Arbeitsmappen aus SharePoint online finden Sie unter [Aktualisieren von Excel-Arbeitsmappen mit eingebundenen PowerPivot-Modellen aus SharePoint Online (Whitepaper)](https://technet.microsoft.com/library/jj992650.aspx) (https://technet.microsoft.com/library/jj992650.aspx).  
  
##  <a name="bkmk_refresh_architecture"></a> Architektur der geplante Datenaktualisierung in SharePoint 2013  
 In der folgenden Abbildung wird die Datenaktualisierungsarchitektur in SharePoint 2013 und SQL Server 2012 SP1 zusammengefasst dargestellt.  
  
 ![Architektur von SQL Server 2012 SP1 datenaktualisierung](../media/as-scheduled-data-refresh2012sp1-architecture.gif "Architektur von SQL Server 2012 SP1 datenaktualisierung")  
  
||Description||  
|-|-----------------|-|  
|**(1)**|Analysis Services-Engine|Ein [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server, der im SharePoint-Modus ausgeführt wird. Der Server wird außerhalb der SharePoint-Farm ausgeführt.|  
|**(2)**|Benutzeroberfläche|Die Benutzeroberfläche besteht aus zwei Seiten. Auf einer Seite wird der Zeitplan definiert, auf der zweiten Seite wird der Aktualisierungsverlauf angezeigt. Die Seiten greifen nicht direkt auf die PowerPivot-Dienstanwendungsdatenbanken zu, sondern über den PowerPivot-Systemdienst.|  
|**(3)**|PowerPivot-Systemdienst|Der Dienst wird installiert, wenn Sie das PowerPivot für SharePoint-Add-In bereitstellen. Der Dienst wird für Folgendes verwendet:<br /><br /> Dieser Dienst hostet die Aktualisierungsplanungs-Engine, die Excel Services-APIs für die Datenaktualisierung von Excel 2013-Arbeitsmappen aufruft. Für Excel 2010-Arbeitsmappen führt der Dienst die Datenmodellverarbeitung direkt aus, verwendet für das Laden des Datenmodells und das Aktualisieren der Arbeitsmappe jedoch weiterhin Excel Services.<br /><br /> Dieser Dienst stellt Methoden für Komponenten bereit, wie z. B. die Benutzeroberflächenseiten, um mit dem Systemdienst zu kommunizieren.<br /><br /> Der Dienst verwaltet Anforderungen für den externen Zugriff auf Arbeitsmappen als Datenquelle, die vom PowerPivot-Webdienst empfangen werden.<br /><br /> Verwaltung geplanter Datenaktualisierungsanforderungen für Zeitgeberaufträge und Konfigurationsseiten. Der Dienst verwaltet Anforderungen zum Lesen von Daten in die und aus der Datenbank und zum Auslösen der Datenaktualisierung mit Excel Services.<br /><br /> Verwendungsanalyse und verwandter Zeitgeberauftrag.|  
|**(4)**|Dienste für Excel-Berechnungen|Zuständig für das Laden der Datenmodelle.|  
|**(5)**|Secure Store Service|Wenn die Authentifizierungseinstellungen in der Arbeitsmappe auf **Konto des authentifizierten Benutzers verwenden** oder **keine**, die in Secure Store zielanwendungs-ID gespeicherten Anmeldeinformationen für Daten verwendet werden aktualisieren. Weitere Informationen finden Sie im Abschnitt [Zusätzliche Überlegungen zur Authentifizierung](#datarefresh_additional_authentication) in diesem Thema.|  
|**(6)**|Zeitgeberauftrag für PowerPivot-Datenaktualisierung|Weist den PowerPivot-Systemdienst an, eine Verbindung mit Excel Services herzustellen, um Datenmodelle zu aktualisieren.|  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] benötigt entsprechende Datenanbieter und Clientbibliotheken, damit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus auf Datenquellen zugreifen kann.  
  
> [!NOTE]  
>  Da der PowerPivot-Systemdienst keine PowerPivot-Modelle mehr lädt oder speichert, gelten die meisten Einstellungen zum Zwischenspeichern von Modellen auf einem Anwendungsserver nicht für eine SharePoint 2013-Farm.  
  
## <a name="data-refresh-log-data"></a>Protokolldaten der Datenaktualisierung  
 **Verwendungsdaten:** Sie können Verwendungsdaten zur datenaktualisierung im PowerPivot-Management-Dashboard anzeigen. So zeigen Sie die Verwendungsdaten an:  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Allgemeine Anwendungseinstellungen** auf **PowerPivot-Management-Dashboard** .  
  
2.  Am unteren Rand des Dashboards, finden Sie unter den **Datenaktualisierung - letzte Aktivität** und **Datenaktualisierung - letzte Fehler**.  
  
3.  Weitere Informationen zu Verwendungsdaten und wie Sie diese aktivieren finden Sie unter [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
 **Diagnoseprotokolldaten:** Sie können SharePoint-diagnoseprotokolldaten zur datenaktualisierung anzeigen. Überprüfen Sie die Konfiguration der Diagnoseprotokollierung für den **PowerPivot-Dienst** auf der Seite **Überwachung** der SharePoint-Zentraladministration. Müssen Sie möglicherweise erhöhen Sie die Ebene der Protokollierung für das "unwichtigste Ereignis" anmelden. Legen Sie beispielsweise vorübergehend den Wert auf **Ausführlich** fest, und führen Sie dann die Datenaktualisierungsvorgänge erneut aus.  
  
 Die Protokolleinträge enthalten Folgendes:  
  
-   Den **Bereich** des **PowerPivot-Diensts**.  
  
-   Die Kategorie der **Datenaktualisierung**.  
  
 Überprüfen Sie die **Konfiguration der Diagnoseprotokollierung**. Weitere Informationen finden Sie unter [konfigurieren und Anzeigen von SharePoint-Protokolldateien und-diagnoseprotokollierung &#40;PowerPivot für SharePoint&#41;](configure-and-view-sharepoint-and-diagnostic-logging.md).  
  
##  <a name="datarefresh_additional_authentication"></a> Zusätzliche Überlegungen zur Authentifizierung  
 Die Einstellungen im Dialogfeld **Excel Services-Authentifizierungseinstellungen** in Excel 2013 bestimmen die Windows-Identität, die Excel Services und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für die Datenaktualisierung verwenden.  
  
-   **Konto des authentifizierten Benutzers verwenden**: Excel Services führt die datenaktualisierung unter der Identität des aktuell angemeldeten Benutzers.  
  
-   **Ein gespeichertes Konto verwenden**: Geht davon aus einer SharePoint Secure Store Service-Anwendungs-ID, die Excel Services verwendet, um den Benutzernamen und ein Kennwort zur Authentifizierung der datenaktualisierung Authentifizierung abzurufen.  
  
-   **None:** Die Excel Services **unbeaufsichtigte Dienstkonto** verwendet wird. Das Dienstkonto ist einem Secure Store Service-Proxy zugeordnet. Konfigurieren Sie die Einstellungen auf der Seite **Excel Services-Anwendungseinstellungen** im Abschnitt **Externe Daten** .  
  
 So öffnen Sie das Dialogfeld mit Authentifizierungseinstellungen:  
  
1.  Klicken Sie in Excel 2013 auf die Registerkarte **Daten** .  
  
2.  Klicken Sie im Menüband auf **Verbindungen** .  
  
3.  Wählen Sie im Dialogfeld **Arbeitsmappenverbindungen**die Verbindung aus, und klicken Sie auf **Eigenschaften**.  
  
4.  In der **Verbindungseigenschaften** Dialogfeld klicken Sie auf **Definition**, und klicken Sie dann auf die **Authentifizierungseinstellungen...**  Schaltfläche.  
  
 ![excel services authentication settings](../media/as-authentication-settings-4-ecs-in-excel2013.gif "excel services authentication settings")  
  
 Weitere Informationen zur Authentifizierung der Datenaktualisierung und zur Verwendung von Anmeldeinformationen finden Sie im Blogbeitrag [Refreshing PowerPivot Data in SharePoint 2013](https://blogs.msdn.com/b/analysisservices/archive/2012/12/21/refreshing-powerpivot-data-in-sharepoint-2013.aspx).  
  
##  <a name="bkmk_moreinformation"></a> Weitere Informationen  
 [Problembehandlung von PowerPivot-Daten](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx).  
  
 [Excel Services in SharePoint 2013](https://www.enjoysharepoint.com/configure-excel-service-application-in-sharepoint-2013/). 
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von Arbeitsmappen und geplanter Datenaktualisierung &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)   
 [PowerPivot für SharePoint 2013 Installation](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
  
