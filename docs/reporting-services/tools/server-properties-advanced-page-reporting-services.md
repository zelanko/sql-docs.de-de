---
title: Servereigenschaften – Seite „Erweitert“ | Microsoft-Dokumentation
description: Verwenden Sie die Seite mit erweiterten Servereigenschaften, um Systemeigenschaften auf dem Berichtsserver festzulegen. Dieses Tool stellt eine grafische Benutzeroberfläche bereit, sodass Sie Eigenschaften festlegen können, ohne Code schreiben zu müssen.
author: maggiesMSFT
ms.author: maggies
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
ms.date: 01/28/2020
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: d1bfbb7a1abb13df05ce402fa79a1598ee04ca1f
ms.sourcegitcommit: cf8db6330be0d89bbec362e4c7e187b5461026f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "77054836"
---
# <a name="server-properties-advanced-page---power-bi-report-server--reporting-services"></a>Servereigenschaften – Seite „Erweitert“: Power BI-Berichtsserver und Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Verwenden Sie diese Seite, um Systemeigenschaften auf dem Berichtsserver festzulegen. Es gibt eine Anzahl von Möglichkeiten, Systemeigenschaften festzulegen. Dieses Tool stellt eine grafische Benutzeroberfläche bereit, so dass Sie Eigenschaften festlegen können, ohne Code schreiben zu müssen.

Öffnen Sie diese Seite, indem Sie SQL Server Management Studio starten und eine Verbindung mit einer Berichtsserverinstanz herstellen. Klicken Sie mit der rechten Maustaste auf den Namen des Berichtsservers, und klicken Sie anschließend auf **Eigenschaften**. Klicken Sie auf **Erweitert**, um diese Seite zu öffnen.

## <a name="options"></a>Tastatur

### <a name="accesscontrolallowcredentials"></a>AccessControlAllowCredentials
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Gibt an, ob die Antwort auf eine Clientanforderung verfügbar gemacht werden kann, wenn das `credentials`-Flag auf „true“ festgelegt ist. Der Standardwert ist **false**.

### <a name="accesscontrolallowheaders"></a>AccessControlAllowHeaders
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Eine durch Trennzeichen getrennte Liste von Headern, die der Server zulässt, wenn ein Client eine Anforderung sendet. Diese Eigenschaft kann aus einer leeren Zeichenfolge bestehen, wobei * angibt, dass alle Header zulässig sind.

### <a name="accesscontrolallowmethods"></a>AccessControlAllowMethods
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Eine durch Trennzeichen getrennte Liste von HTTP-Methoden, die der Server zulässt, wenn ein Client eine Anforderung sendet. Die Standardwerte sind GET, PUT, POST, PATCH, DELETE, wobei * angibt, dass alle Methoden zulässig sind.

### <a name="accesscontrolalloworigin"></a>AccessControlAllowOrigin
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Eine durch Trennzeichen getrennte Liste von Ursprüngen, die der Server zulässt, wenn ein Client eine Anforderung sendet. Der Standardwert ist leer, wodurch sämtliche Anforderungen verhindert werden. Wenn * angegeben wird, sind alle Ursprünge zulässig, wenn keine Anmeldeinformationen festgelegt sind. Wenn hingegen Anmeldeinformationen festgelegt sind, muss eine explizite Liste von Ursprüngen angegeben werden.

### <a name="accesscontrolexposeheaders"></a>AccessControlExposeHeaders
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Eine durch Trennzeichen getrennte Liste von Headern, die der Server für Clients verfügbar macht. Für diese Einstellung gibt es keinen Standardwert.

### <a name="accesscontrolmaxage"></a>AccessControlMaxAge
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Gibt an, wie viele Sekunden lang die Ergebnisse der Preflightanforderung zwischengespeichert werden können. Der Standardwert ist 600 (10 Minuten).

### <a name="allowedresourceextensionsforupload"></a>AllowedResourceExtensionsForUpload
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Legt Erweiterungen von Ressourcen fest, die auf den Berichtsserver hochgeladen werden können. Erweiterungen für integrierte Dateitypen wie &ast;.rdl und &ast;.pbix müssen nicht einbezogen werden. Der Standardwert lautet „&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx“.

### <a name="customheaders"></a>CustomHeaders 

(Nur Power BI-Berichtsserver, Version Januar 2020, sowie Reporting Services 2019 und höher)

Hiermit werden Headerwerte für alle URLs festgelegt, die dem angegebenen RegEx-Muster entsprechen. Benutzer können den CustomHeaders-Wert mit gültigem XML-Code aktualisieren, um Headerwerte für ausgewählte Anforderungs-URLs festzulegen. Administratoren können dem XML-Code eine beliebige Anzahl von Headern hinzufügen. Standardmäßig sind keine benutzerdefinierten Header vorhanden, und der Wert ist leer. 

> [!NOTE]
> Zu viele Header können sich auf die Leistung auswirken. 

Es empfiehlt sich, die Konfiguration der Topologie zu überprüfen, um sicherzustellen, dass die Header mit Ihrer Bereitstellung von Reporting Services kompatibel sind. Es kann passieren, dass Einstellungen ausgewählt werden, die Fehler in Browsern verursachen, wenn die Browser nicht auch über die entsprechenden Einstellungen verfügen. Sie sollten beispielsweise keine HSTS-Konfiguration hinzufügen, wenn Ihr Server nicht für HTTPS konfiguriert ist. Nicht kompatible Header können zu Renderfehlern im Browser führen.

#### <a name="customheaders-xml-format"></a>CustomHeaders-XML-Format

```xml
<CustomHeaders>
    <Header>
        <Name>{Name of the header}</Name>
        <Pattern>{Regex pattern to match URLs}</Pattern>
        <Value>{Value of the header}</Value>
    </Header>
</CustomHeaders>
```

#### <a name="setting-the-customheaders-property"></a>Festlegen der CustomHeaders-Eigenschaft

- Sie können die Eigenschaft mithilfe des SOAP-Endpunkts [SetSystemProperties](https://docs.microsoft.com/dotnet/api/reportservice2010.reportingservice2010.setsystemproperties) festlegen, indem Sie die CustomHeaders-Eigenschaft als Parameter übergeben.
- Sie können den REST-Endpunkt [UpdateSystemProperties](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0#/System/UpdateSystemProperties) (`/System/Properties`) verwenden und die CustomHeaders-Eigenschaft übergeben.

#### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie den HSTS-Header und andere benutzerdefinierte Header für URLs mit übereinstimmendem RegEx-Muster festlegen.

```xml
<CustomHeaders>
    <Header>
        <Name>Strict-Transport-Security</Name>
        <Pattern>\/Reports\/mobilereport</Pattern>
        <Value>max-age=86400</Value>
    </Header>
    <Header>
        <Name>Embed</Name>
        <Pattern>(.+)(/reports/)(.+)(rs:embed=true)</Pattern>
        <Value>True</Value>
    </Header>
</CustomHeaders>
```

Der erste Header im obigen XML-Code fügt den Header `Strict-Transport-Security: max-age=86400` zu den übereinstimmenden Anforderungen hinzu.
- http://adventureworks/Reports/mobilereport/New%20Mobile%20Report: RegEx stimmt überein und legt HSTS-Header fest
- http://adventureworks/ReportServer/mobilereport/New%20Mobile%20Report: keine Übereinstimmung

Der zweite Header im obigen XML-Code fügt den Header `Embed: True` für die URL hinzu, die die Abfrageparameter `/reports/` und `rs:embed=true` enthält.
- https://adventureworks/reports/mobilereport/New%20Mobile%20Report?rs:embed=true: Übereinstimmung
- https://adventureworks/reports/mobilereport/New%20Mobile%20Report?rs:embed=false: keine Übereinstimmung

### <a name="editsessioncachelimit"></a>EditSessionCacheLimit
Gibt die Anzahl von Datencacheeinträgen an, die in einer Berichtsbearbeitungssitzung aktiv sein können. Die Standardanzahl ist 5.  

### <a name="editsessiontimeout"></a>EditSessionTimeout
Gibt die Anzahl der Sekunden bis zum Timeout einer Berichtsbearbeitungssitzung an. Der Standardwert ist 7.200 Sekunden (zwei Stunden). 

### <a name="enablecdnvisuals"></a>EnableCDNVisuals 
(Nur Power BI-Berichtsserver) Wenn diese Option aktiviert ist, laden Power BI-Berichte die neuesten zertifizierten benutzerdefinierten Visuals aus einem von Microsoft gehosteten Content Delivery Network (CDN). Wenn Ihr Server keinen Zugriff auf Internetressourcen hat, können Sie diese Option deaktivieren. In diesem Fall werden benutzerdefinierte Visuals aus dem Bericht geladen, der auf dem Server veröffentlicht wurde. Der Standardwert ist **true**.  

###  <a name="enableclientprinting"></a>EnableClientPrinting  
Bestimmt, ob das RSClientPrint-ActiveX-Steuerelement zum Herunterladen vom Berichtsserver verfügbar ist. Gültige Werte sind **true** und **false**. Der Standardwert lautet **true**. Weitere Informationen zu zusätzlichen Einstellungen, die für dieses Steuerelement erforderlich sind, finden Sie unter [Aktivieren und Deaktivieren des clientseitigen Drucks für Reporting Services](../../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  

### <a name="enablecustomvisuals"></a>EnableCustomVisuals 
(Nur Power BI-Berichtsserver) Dient zum Aktivieren der Anzeige von benutzerdefinierten Power BI-Visuals. Mögliche Werte sind TRUE/FALSE. *Der Standardwert ist TRUE.*  

###  <a name="enableexecutionlogging"></a>EnableExecutionLogging  
Gibt an, ob die Protokollierung der Berichtsausführung aktiviert ist. Der Standardwert lautet **true**. Weitere Informationen zum Berichtsserver-Ausführungsprotokoll finden Sie unter [Berichtsserver-Ausführungsprotokoll und die ExecutionLog3-Ansicht](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  

### <a name="enableintegratedsecurity"></a>EnableIntegratedSecurity
Bestimmt, ob die integrierte Sicherheit von Windows für Berichtsdatenquellen-Verbindungen unterstützt wird. Der Standardwert ist **True**. Die folgenden Werte sind gültig:

|Werte|BESCHREIBUNG|
|---------|---------|
|**Wahr**|Die integrierte Sicherheit von Windows ist aktiviert.|
|**False**|Die integrierte Sicherheit von Windows ist nicht aktiviert. Berichtsdatenquellen, die für die Verwendung der integrierten Sicherheit von Windows konfiguriert sind, werden nicht ausgeführt.|

### <a name="enableloadreportdefinition"></a>EnableLoadReportDefinition
Wählen Sie diese Option, um anzugeben, ob Benutzer eine ungeplante Berichtsausführung eines Berichts des Berichts-Generators durchführen können. Durch Festlegen dieser Option wird der Wert der **EnableLoadReportDefinition** -Eigenschaft auf dem Berichtsserver bestimmt.  

Wenn Sie diese Option deaktivieren, wird die Eigenschaft auf FALSE festgelegt. Der Berichtsserver generiert keine Berichte mit Durchklicken für Berichte, die ein Berichtsmodell als Datenquelle verwenden. Alle Aufrufe der LoadReportDefinition-Methode werden blockiert.  

Die Deaktivierung dieser Option führt zu einem Sicherheitsrisiko, weil böswillige Benutzer einen Denial-of-Service-Angriff ausführen können, bei dem der Berichtsserver mit LoadReportDefinition-Anforderungen überlastet wird.  

### <a name="enablemyreports"></a>EnableMyReports  
Gibt an, ob die Funktion <legacyBold>Meine Berichte</legacyBold> aktiviert ist. Der Wert **true** gibt an, dass die Funktion aktiviert ist.  

### <a name="enablepowerbireportexportdata"></a>EnablePowerBIReportExportData 
(Nur Power BI-Berichtsserver) Aktivieren Sie den Export von Power BI-Berichtsserverdaten aus Power BI-Visuals. Die Werte sind TRUE und FALSE.  Der Standardwert lautet "True". 

### <a name="enablepowerbireportexportunderlyingdata"></a>EnablePowerBIReportExportUnderlyingData 
(Nur Power BI-Berichtsserver) Gibt an, ob ein Kunde zugrunde liegende Daten aus Power BI-Visuals zum Power BI-Berichtsserver exportieren kann. Der Wert TRUE gibt an, dass die Funktion aktiviert ist.

### <a name="enableremoteerrors"></a>EnableRemoteErrors
Nimmt externe Fehlerinformationen (beispielsweise Fehlerinformationen zu Berichtsdatenquellen) in die Fehlermeldungen auf, die für Benutzer zurückgegeben werden, die Berichte von Remotecomputern anfordern. Gültige Werte sind **true** und **false**. Der Standardwert ist **false**. Weitere Informationen finden Sie unter [Aktivieren von Remotefehlern &#40;Reporting Services&#41;](../../reporting-services/report-server/enable-remote-errors-reporting-services.md).  

### <a name="enabletestconnectiondetailederrors"></a>EnableTestConnectionDetailedErrors
Gibt an, ob ausführliche Fehlermeldungen an den Clientcomputer gesendet werden sollen, wenn Benutzer Datenquellverbindungen mit dem Berichtsserver testen. Der Standardwert lautet **true**. Wenn die Option auf **false**festgelegt wird, werden nur generische Fehlermeldungen gesendet.

###  <a name="executionlogdayskept"></a>ExecutionLogDaysKept  
Die Anzahl von Tagen, in denen die Berichtsausführungsdaten im Ausführungsprotokoll verbleiben. Gültige Werte für diese Eigenschaft sind **-1** bis **2**,**147**,**483**,**647**. Wenn der Wert **–1** ist, werden Einträge nicht aus der Ausführungsprotokolltabelle gelöscht. Der Standardwert lautet **60**.  

> [!NOTE]
> Wenn Sie den Wert auf **0** (null) festlegen, werden alle Einträge aus dem Ausführungsprotokoll *gelöscht*. Bei einem Wert von **–1** werden die Einträge des Ausführungsprotokolls beibehalten statt gelöscht.

### <a name="executionloglevel"></a>ExecutionLogLevel
Hiermit wird der Protokolliergrad der Ausführung festgelegt. *Der Standardwert ist „Normal“.*

### <a name="externalimagestimeout"></a>ExternalImagesTimeout
Legt den Zeitraum fest, innerhalb dessen eine externe Bilddatei abgerufen werden muss, bevor bei der Verbindung ein Timeout auftritt. Der Standardwert ist **600** Sekunden.  

### <a name="interprocesstimeoutminutes"></a>InterProcessTimeoutMinutes
(Nur Power BI-Berichtsserver, Reporting Services 2019 und höher) Dient zum Festlegen des Prozesstimeouts in Minuten. *Der Standardwert ist 30.*

### <a name="maxfilesizemb"></a>MaxFileSizeMb
Dient zum Festlegen der maximalen Dateigröße des Berichts in MB. *Der Standardwert ist 1000.  Der Höchstwert ist 2000.*

### <a name="modelcleanupcycleminutes"></a>ModelCleanupCycleMinutes 
(Nur Power BI-Berichtsserver) Hiermit wird die Häufigkeit der Prüfung auf nicht verwendete Modelle im Arbeitsspeicher in Minuten festgelegt. *Der Standardwert ist 15.*

### <a name="modelexpirationminutes"></a>ModelExpirationMinutes 
(Nur Power BI-Berichtsserver) Hiermit wird die Häufigkeit der Entfernung nicht verwendeter Modelle aus dem Arbeitsspeicher in Minuten festgelegt. *Der Standardwert ist 60.*

###  <a name="myreportsrole"></a>MyReportsRole  
Der Name der Rolle, die beim Erstellen von Sicherheitsrichtlinien für die Ordner <legacyBold>Meine Berichte</legacyBold> des Benutzers verwendet wird. Der Standardwert lautet **My Reports Role**.  

### <a name="officeaccesstokenexpirationseconds"></a>OfficeAccessTokenExpirationSeconds 
(Nur Power BI-Berichtsserver, Reporting Services 2019 und höher) Legt fest, nach wie vielen Sekunden das Office-Zugriffstoken ablaufen soll. *Der Standardwert ist 60.*

### <a name="officeonlinediscoveryurl"></a>OfficeOnlineDiscoveryURL 
(Nur Power BI-Berichtsserver) Legen Sie die Adresse Ihrer Office Online-Serverinstanz für die Anzeige von Excel-Arbeitsmappen fest.

### <a name="rdlxreporttimetout"></a>RDLXReportTimetout
Der Timeoutwert für die Verarbeitung des RDLX-Berichts *(Power View-Berichte in einer SharePoint Server-Instanz)* in Sekunden für alle im Namespace des Berichtsservers verwalteten Berichte. Dieser Wert kann auf Berichtsebene überschrieben werden. Ist diese Eigenschaft festgelegt, versucht der Berichtsserver, die Verarbeitung eines Berichts zu beenden, sobald der angegebene Zeitraum überschritten wird. Gültige Werte sind **-1** bis **2**.**147**.**483**.**647**. Wenn der Wert **-1**ist, tritt bei Berichten im Namespace während der Verarbeitung kein Timeout auf. Der Standardwert lautet **1800**.

### <a name="requireintune"></a>RequireIntune
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Hiermit wird festgelegt, ob Intune über die mobile Power BI-App auf die Berichte Ihrer Organisation zugreift. *Der Standardwert ist FALSE.*

### <a name="restrictedresourcemimetypeforupload"></a>RestrictedResourceMimeTypeForUpload
(Nur Power BI-Berichtsserver, Version Januar 2019, sowie Reporting Services 2017 und höher) Gruppe von MIME-Typen, mit denen Benutzer keine Inhalte hochladen dürfen. Ressourcen, die bereits mit einem eingeschränkten MIME-Typ gespeichert sind, können nur als Anwendungs-/Oktettdatenstrom heruntergeladen werden, anstatt vom Browser geöffnet oder ausgeführt zu werden.  Standardmäßig befinden sich keine eingeschränkten Elemente in dieser Liste, es wird Organisationen aber empfohlen, diese Liste aufzufüllen, um eine möglichst sichere Funktionalität zu gewährleisten.

### <a name="schedulerefreshtimeoutminutes"></a>ScheduleRefreshTimeoutMinutes 
(Nur Power BI-Berichtsserver) Timeout bei der Datenaktualisierung in Minuten für die geplante Aktualisierung von Power BI-Berichten mit eingebetteten AS-Modellen. Der Standardwert ist 120 Minuten.

### <a name="sessiontimeout"></a>SessionTimeout
Der Zeitraum in Sekunden, in dem die Sitzung aktiv bleibt. Der Standardwert lautet **600**.  

### <a name="sharepointintegratedmode"></a>SharePointIntegratedMode
Diese schreibgeschützte Eigenschaft gibt den Servermodus an. Wenn dieser Wert False ist, wird der Berichtsserver im einheitlichen Modus ausgeführt.  

### <a name="showdownloadmenu"></a>ShowDownloadMenu
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Aktiviert das Downloadmenü für Clienttools. *Der Standardwert ist TRUE.*

### <a name="sitename"></a>SiteName
Der Name der Berichtsserversite, der im Seitentitel des Webportals angezeigt wird. Der Standardwert ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Diese Eigenschaft kann eine leere Zeichenfolge sein. Die maximale Länge beträgt 8,000 Zeichen.  

### <a name="snapshotcompression"></a>SnapshotCompression
Definiert, wie Momentaufnahmen komprimiert werden. Der Standardwert lautet **SQL**. Die folgenden Werte sind gültig:

|Werte|BESCHREIBUNG|
|---------|---------|
|**SQL**|Momentaufnahmen werden komprimiert, wenn sie in der Berichtsserver-Datenbank gespeichert werden. Diese Komprimierung entspricht dem aktuellen Verhalten.|
|**None**|Momentaufnahmen werden nicht komprimiert.|
|**Alle**|Momentaufnahmen werden bei allen Speicheroptionen komprimiert. Dazu gehören auch die Berichtsserver-Datenbank oder das Dateisystem.|

### <a name="storedparameterslifetime"></a>StoredParametersLifetime
Gibt die maximale Anzahl von Tagen an, während derer ein gespeicherter Parameter gespeichert werden kann. Gültige Werte sind **-1**, **+1** bis **2.147.483.647**. Der Standardwert ist **180** Tage.  

### <a name="storedparametersthreshold"></a>StoredParametersThreshold
Gibt die maximale Anzahl von Parameterwerten an, die von dem Berichtsserver gespeichert werden können. Gültige Werte sind **-1**, **+1** bis **2.147.483.647**. Der Standardwert lautet **1500**.  

### <a name="supportedhyperlinkschemes"></a>SupportedHyperlinkSchemes 
(Nur Power BI-Berichtsserver, Version Januar 2019, sowie Reporting Services 2019 und höher) Legt eine durch Trennzeichen getrennte Liste mit den URI-Schemas fest, die für Hyperlinkaktionen definiert werden dürfen, für die ein Rendering zulässig ist. Durch Angabe von „&ast;“ werden alle Hyperlinkschemas erlaubt. Mit der Einstellung „http,https“ sind beispielsweise Links zu „https://www. contoso.com“ zulässig. Links zu „mailto:bill@contoso.com“ oder „javascript:window.open(‘ www.contoso.com’, ‘_blank’)“ werden dagegen entfernt. Die Standardeinstellung ist „&ast;“.

### <a name="systemreporttimeout"></a>SystemReportTimeout
Der Standard-Timeoutwert für die Berichtsverarbeitung in Sekunden für alle im Berichtsserver-Namespace verwalteten Berichte. Dieser Wert kann auf Berichtsebene überschrieben werden. Ist diese Eigenschaft festgelegt, versucht der Berichtsserver, die Verarbeitung eines Berichts zu beenden, sobald der angegebene Zeitraum überschritten wird. Gültige Werte sind **-1** bis **2**.**147**.**483**.**647**. Wenn der Wert **-1**ist, tritt bei Berichten im Namespace während der Verarbeitung kein Timeout auf. Der Standardwert lautet **1800**.  

### <a name="systemsnapshotlimit"></a>SystemSnapshotLimit
Die maximale Anzahl an Momentaufnahmen, die für einen Bericht gespeichert werden. Gültige Werte sind **-1** bis **2**.**147**.**483**.**647**. Lautet der Wert **-1**, so ist die Anzahl von Momentaufnahmen nicht einschränkt.  

### <a name="timerinitialdelayseconds"></a>TimerInitialDelaySeconds
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Legt fest, um wie viele Sekunden die Anfangszeit verzögert werden soll. *Der Standardwert ist 60.*

### <a name="trustedfileformat"></a>TrustedFileFormat
(Nur Power BI-Berichtsserver, Reporting Services 2017 und höher) Legt alle externen Dateiformate fest, die sich auf der Reporting Services-Portalwebsite im Browser öffnen lassen. Bei hier nicht aufgeführten Dateiformaten wird der Benutzer aufgefordert, die Datei im Browser herunterzuladen. Die Standardwerte sind JPG, JPEG, JPE, WAV, BMP, PDF, IMG, GIF, JSON, MP4, WEB, PNG.

### <a name="usesessioncookies"></a>UseSessionCookies
Gibt an, ob der Berichtsserver beim Kommunizieren mit Clientbrowsern Sitzungscookies verwenden soll. Der Standardwert lautet **true**.  

## <a name="see-also"></a>Weitere Informationen

[Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
[Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
[Eigenschaften von Reporting Services](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties.md)   
[Berichtsserver im Management Studio (F1-Hilfe)](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
[Berichtsserver-Systemeigenschaften](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)   
[Skripts für Bereitstellungs- und Verwaltungsaufgaben](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)   
[Aktivieren und Deaktivieren von "Meine Berichte"](../../reporting-services/report-server/enable-and-disable-my-reports.md)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
