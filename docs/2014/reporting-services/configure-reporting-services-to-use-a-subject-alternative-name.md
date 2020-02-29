---
title: Konfigurieren Reporting Services für die Verwendung eines alternativen Antragsteller namens | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ce458f9f-4b4f-4a58-aa75-9a90dda1e622
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5bbbf363c8d6ebb452f6628676de1b8918e6f245
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78173926"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a>Konfigurieren der Reporting Services für die Verwendung eines alternativen Antragstellernamens
  In diesem Thema wird erklärt, wie Sie [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) für die Verwendung eines alternativen Antragstellernamens (Subject Alternative Name, SAN) konfigurieren, indem Sie die Datei „rsreportserver.config“ ändern und das Tool „Netsh.exe“ verwenden.

||
|-|
|**[!INCLUDE[applies](../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im einheitlichen Modus|

 Die Anweisungen gelten sowohl für die Berichtsdienst-URL als auch die Webdienst-URL.

 Zum Verwenden eines SAN muss das SSL-Zertifikat auf dem Server registriert und signiert sein und über den privaten Schlüssel verfügen. Sie können kein selbstsigniertes Zertifikat verwenden.

 URLs in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] können für die Verwendung eines SSL-Zertifikats konfiguriert werden. Ein Zertifikat verfügt normalerweise nur über einen Antragstellernamen, der nur eine URL für eine SSL-Sitzung (Secure Sockets Layer) zulässt. Der SAN ist ein zusätzliches Feld im Zertifikat, über das ein SSL-Zertifikat viele URLs überwachen und für diese gültig sein kann. Außerdem kann der SSL-Port dann mit anderen Anwendungen gemeinsam verwendet werden. Der SAN sieht wie folgt aus: www.s2.com.

 Weitere Informationen zu SSL-Einstellungen für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]finden Sie unter [Konfigurieren von SSL-Verbindungen auf einem Berichtsserver im einheitlichen Modus](security/configure-ssl-connections-on-a-native-mode-report-server.md).

### <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a>Konfigurieren von SSRS für die Verwendung eines alternativen Antragstellernamens für die Webdienst-URL

1.  Starten Sie den Konfigurations-Manager für Reporting Services.

     Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md).

2.  Wählen Sie auf der Seite **Webdienst-URL** einen SSL-Port und ein SSL-Zertifikat aus.

     ![Reporting Services-Konfigurations-Manager](media/reportingservices-configurationmanager.png "Reporting Services-Konfigurations-Manager")

     Der Konfigurations-Manager registriert das SSL-Zertifikat für den Port.

3.  Öffnen Sie die Datei rsreportserver.config.

     Für den einheitlichen SSRS-Modus befindet sich die Datei standardmäßig in folgendem Ordner.

    ```
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer
    ```

4.  Kopieren Sie den URL-Abschnitt für die Berichtsserver-Webdienstanwendung.

     Im Folgenden ist beispielsweise der Original-URL-Abschnitt dargestellt.

    ```
        <URL>
         <UrlString>https://localhost:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>

    ```

     Im Folgenden sehen Sie den modifizierten URL-Abschnitt.

    ```
    <URL>
         <UrlString>https://www.s1.com:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>
        <URL>
         <UrlString>https://www.s2.com:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>

    ```

5.  Speichern Sie die Datei rsreportserver.config.

6.  Starten Sie eine Eingabeaufforderung als Administrator, und führen Sie das Tool Netsh.exe aus.

    ```
    C:\windows\system32\netsh
    ```

7.  Wechseln Sie zum HTTP-Kontext, indem Sie Folgendes eingeben.

    ```
    Netsh>http
    ```

8.  Zeigen Sie die vorhandenen URL-ACLs an, indem Sie Folgendes eingeben.

    ```
    Netsh http>show urlacl
    ```

     Ein Eintrag wie der folgenden wird angezeigt.

    ```
    Reserved URL            : https:// www.s1.com:443/ReportServer/
        User: NT SERVICE\ReportServer
            Listen: Yes
            Delegate: No
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)
    ```

     Eine URL-ACL ist eine besitzverwaltete Zugriffssteuerungsliste (Discretionary Access Control List, DACL) für eine reservierte URL.

9. Erstellen Sie einen neuen Eintrag für den alternativen Antragstellernamen mit demselben Benutzer und derselben SDDL wie beim vorhandenen Eintrag, indem Sie Folgendes eingeben.

    ```
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer  
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)

    ```

10. Klicken Sie im Konfigurations-Manager für Reporting Services auf der Seite **Berichtsserverstatus** auf **Beenden** , und klicken Sie dann auf **Starten** , um den Berichtsserver neu zu starten.

## <a name="see-also"></a>Weitere Informationen
 [RSReportServer-Konfigurationsdatei](report-server/rsreportserver-config-configuration-file.md) [Konfigurations-Manager für Reporting Services &#40;einheitlichen Modus&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) [eine Reporting Services Konfigurationsdatei &#40;"RSReportServer. config" ändern](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)&#41;[Konfigurieren von Berichts Server-URLs &#40;SSRS Configuration Manager](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)&#41;


