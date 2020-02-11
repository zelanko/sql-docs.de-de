---
title: Übersicht über Claims to Windows Token Service (C2WTS) und Reporting Services | Microsoft-Dokumentation
author: maggiesMSFT
ms.author: maggies
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint
ms.topic: conceptual
ms.date: 09/15/2017
ms.openlocfilehash: 2ed9c2a5070a1034970f2f34f5e7bf88a77e8533
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68264999"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Claims to Windows Token Service (C2WTS) und Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Claims to Windows Token Service (C2WTS) von SharePoint ist erforderlich, wenn Sie Berichte im einheitlichen Modus im [SQL Server Reporting Services-Berichts-Viewer-Webpart](../report-server-sharepoint/deploy-report-viewer-web-part.md) abrufen möchten.

C2WTS ist außerdem im SharePoint-Modus von SQL Server Reporting Services erforderlich, wenn Sie die Windows-Authentifizierung für Datenquellen verwenden möchten, die außerhalb der SharePoint-Farm liegen. C2WTS wird auch dann benötigt, auch sich die Datenquelle(n) auf demselben Computer wie der gemeinsame Dienst befinden. In diesem Szenario ist jedoch keine eingeschränkte Delegierung erforderlich.

> [!NOTE]
> Die Integration von Reporting Services in SharePoint ist nach SQL Server 2016 nicht mehr möglich.

## <a name="report-viewer-native-mode-web-part-configuration"></a>Konfiguration des Report Viewer-Webparts (einheitlicher Modus)

Das Berichts-Viewer-Webpart kann verwendet werden, um SQL Server Reporting Services-Berichte im einheitlichen Modus in Ihre SharePoint-Website einzubetten. Dieses Webpart ist für SharePoint 2013 und SharePoint 2016 verfügbar. Sowohl SharePoint 2013 als auch SharePoint 2016 verwenden die Forderungsauthentifizierung. Aus diesem Grund muss C2WTS ordnungsgemäß konfiguriert werden. Reporting Services muss für die Kerberos-Authentifizierung konfiguriert werden, damit die Berichte korrekt gerendert werden.

1. Konfigurieren Sie Ihre Reporting Services-Instanz (einheitlicher Modus) für die Kerberos-Authentifizierung, indem Sie das SSRS-Dienstkonto bestimmen, einen SPN festlegen und die Datei „rsreportserver.config“ so aktualisieren, dass der Authentifizierungstyp „RSWindowsNegotiate“ verwendet wird. [Register a Service Principal Name (SPN) for a Report Server (Registrieren eines Dienstprinzipalnamens (SPON) für einen Berichtsserver)](https://docs.microsoft.com/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server)

2. Ausführen der [grundlegenden Schritte für die C2WTS-Konfiguration](https://docs.microsoft.com/sql/reporting-services/install-windows/claims-to-windows-token-service-c2wts-and-reporting-services?view=sql-server-2017#steps-needed-to-configure-c2wts)
 

## <a name="sharepoint-mode-integration"></a>Integration des SharePoint-Modus

**Dieser Abschnitt gilt nur für SQL Server 2016 Reporting Services und früher.**

Der SharePoint-Dienst Claims to Windows Token Service (C2WTS) ist im SharePoint-Modus von SQL Server Reporting Services erforderlich, wenn Sie die Windows-Authentifizierung für Datenquellen verwenden möchten, die außerhalb der SharePoint-Farm liegen. Dies gilt auch, wenn der Benutzer über die Windows-Authentifizierung auf die Datenquellen zugreift, weil die Kommunikation zwischen dem Web-Front-End und dem gemeinsamen Reporting Services-Dienst immer der Forderungsauthentifizierung unterliegt.

## <a name="steps-needed-to-configure-c2wts"></a>Grundlegende Schritte für die C2WTS-Konfiguration

Die von C2WTS erstellten Token funktionieren nur bei der eingeschränkten Delegierung (Einschränkungen für bestimmte Dienste) und bei Verwendung der Konfigurationsoption „Beliebiges Authentifizierungsprotokoll verwenden“ (Protokollübergang).

Wenn in der Umgebung die eingeschränkte Kerberos-Delegierung verwendet wird, dann müssen sich der SharePoint Server-Dienst und externe Datenquellen in derselben Windows-Domäne befinden. Jeder Dienst, der auf C2WTS (Claims to Windows Token Service) basiert, muss die **eingeschränkte** Kerberos-Delegierung verwenden, damit C2WTS den Kerberos-Protokollübergang verwenden kann, um Ansprüche (Claims) in Windows-Anmeldeinformationen zu übersetzen. Diese Anforderungen gelten für alle gemeinsamen SharePoint-Dienste. Weitere Informationen finden Sie unter [Planen der Kerberos-Authentifizierung in SharePoint 2013](https://technet.microsoft.com/library/ee806870.aspx).  

1. Konfigurieren Sie das C2WTS-Dienstdomänenkonto. 

    **C2WTS sollte mit einer eigenen Domänenidentität ausgeführt werden.**

    * Erstellen Sie ein Active Directory-Konto, und registrieren Sie das Konto als verwaltetes Konto in SharePoint Server. Weitere Informationen zu verwalteten Konten finden Sie unter [Managed Accounts in SharePoint](https://blog.wbaer.net/2010/04/11/managed-accounts-in-sharepoint-2010/) (Verwaltete Konten in SharePoint).
   
    * Konfigurieren Sie den C2WTS-Dienst für die Verwendung des verwalteten Kontos über „SharePoint Zentraladministration > Sicherheit > Dienstkonten konfigurieren > Windows-Dienst – Claims to Windows Token Service“.

    Fügen Sie das C2WTS-Dienstkonto der lokalen Administratorgruppe auf jedem Server hinzu, auf dem C2WTS ausgeführt wird. Für das **Berichts-Viewer-Webpart** sind das die Web-Front-End-Server (WFE). Für den **integrierten SharePoint-Modus** sind das die Anwendungsserver, auf denen der Reporting Services-Dienst ausgeführt wird.
    * Gewähren Sie dem C2WTS-Konto unter „Lokale Richtlinien > Zuweisen von Benutzerrechten“ die folgenden Berechtigungen in der lokalen Sicherheitsrichtlinie:
        * Einsetzen als Teil des Betriebssystems
        * Annehmen der Identität eines Clients nach der Authentifizierung
        * Anmelden als Dienst

    
2. Konfigurieren Sie die Delegierung für das C2WTS-Dienstkonto.

    Das Konto muss für die eingeschränkte Delegierung mit Protokollübergang konfiguriert werden. Außerdem benötigt es Berechtigungen für die Delegierung an Dienste, mit denen es kommunizieren muss (d.h. SQL Server-Datenbank-Engine oder SQL Server Analysis Services). Verwenden Sie das Snap-In „Active Directory-Benutzer und -Computer“, um die Delegierung zu konfigurieren. Dafür müssen Sie als Domänenadministrator angemeldet sein.

    > [!IMPORTANT]
    > Alle Einstellungen, die Sie für das C2WTS-Dienstkonto auf der Registerkarte „Delegierung“ konfigurieren, müssen dem Hauptdienstkonto entsprechen. Für das **Berichts-Viewer-Webpart** ist dies das Dienstkonto für die SharePoint-Webanwendung. Für den **integrierten SharePoint-Modus** ist dies das Reporting Services-Dienstkonto.
    >
    > Wenn Sie dem C2WTS-Dienstkonto beispielsweise erlauben, Delegierungen an einen SQL-Dienst durchzuführen, müssen Sie auf dem Reporting Services-Dienstkonto für den integrierten SharePoint-Modus dieselbe Konfiguration verwenden.

    * Klicken Sie mit der rechten Maustaste auf jedes Dienstkonto, und öffnen Sie das Eigenschaftendialogfeld. Klicken Sie im Dialogfeld auf die Registerkarte **Delegierung** .

        Die Registerkarte „Delegierung“ ist nur sichtbar, wenn dem Objekt ein Dienstprinzipalname (Service Principal Name, SPN) zugewiesen wurde. C2WTS erfordert grundsätzlich keinen SPN für das C2WTS-Konto. Ohne einen SPN ist die Registerkarte **Delegierung** jedoch nicht sichtbar. Eine Alternative zur Konfiguration der eingeschränkten Delegierung ist die Verwendung des Hilfsprogramms **ADSIEdit**.

    * Wesentliche Konfigurationsoptionen auf der Registerkarte "Delegierung":

        * Klicken Sie auf **Benutzer bei Delegierungen angegebener Dienste vertrauen**.
        * Klicken Sie auf **Beliebiges Authentifizierungsprotokoll verwenden**.

    * Wählen Sie **Hinzufügen** zum Hinzufügen eines Dienstes, an den Sie delegieren können.

    * Klicken Sie auf **Benutzer oder Computer...&#42;** , und geben Sie das Konto ein, das den Dienst hostet. Wenn ein SQL Server beispielsweise unter einem Konto namens *sqlservice* ausgeführt wird, geben Sie `sqlservice` ein. 
      Für das **Report Viewer-Webpart** ist dies das Dienstkonto für die Reporting Services-Instanz (einheitlicher Modus).

    * Wählen Sie die Darstellung des Diensts. Dadurch werden die SPNs angezeigt, die über dieses Konto verfügbar sind. Wenn der Dienst unter diesem Konto nicht angezeigt wird, fehlt er möglicherweise oder befindet auf einem anderen Konto. Sie können das SetSPN-Dienstprogramm verwenden, um die SPNs anzupassen. Für das **Report Viewer-Webpart** finden Sie den konfigurierten HTTP-SPN unter [Konfiguration des Report Viewer-Webparts](https://docs.microsoft.com/sql/reporting-services/install-windows/claims-to-windows-token-service-c2wts-and-reporting-services?view=sql-server-2017#report-viewer-native-mode-web-part-configuration).

    * Wählen Sie „OK“ aus, um die Dialogfelder zu verlassen.

3. Konfigurieren Sie C2WTS-*AllowedCallers* (Zulässige Aufrufer).

    C2WTS erfordert, dass die Identitäten der „Callers“ in der Konfigurationsdatei **c2WTShost.exe.config** explizit aufgeführt werden. C2WTS akzeptiert keine Anforderungen sämtlicher authentifizierter Benutzer im System, es sei denn, der Dienst wurde entsprechend konfiguriert. In diesem Fall entspricht der „Aufrufer“ der WSS_WPG-Windows-Gruppe. Die Datei „C2WTShost.exe.config“ wird im folgenden Ordner gespeichert:

    Durch die Änderung des Dienstkontos für den C2WTS-Dienst in der SharePoint-Zentraladministration wird das Konto der Gruppe „WSS_WPG“ hinzugefügt.

    **\Programme\Windows Identity Foundation\v3.5 \c2WTShost.exe.config**

    Im folgenden Beispiel wird die Konfigurationsdatei gezeigt:

    ```
    <configuration>
      <windowsTokenService>
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->
        <allowedCallers>
          <clear/>
          <add value="WSS_WPG" />
        </allowedCallers>
      </windowsTokenService>
    </configuration>
    ```

4. Starten Sie den Claims to Windows Token Service über die SharePoint-Zentraladministration auf der Seite **Dienste auf dem Server verwalten**. Falls der Dienst bereits gestartet ist, beenden Sie ihn, und starten Sie ihn neu. Der Dienst sollte auf dem Server gestartet werden, auf dem die Aktion ausgeführt wird. Wenn Sie z.B. über einen WFE-Server und einen Anwendungsserver verfügen, auf dem der gemeinsame Dienst von SQL Server Reporting Services ausgeführt wird, müssen Sie C2WTS nur auf dem Anwendungsserver starten. C2WTS ist nur für einen WFE-Server erforderlich, wenn Sie das Berichts-Viewer-Webpart ausführen.

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
