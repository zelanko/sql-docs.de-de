---
title: Konfigurieren der Reporting Services für die Verwendung eines alternativen Antragstellernamens (Subject Alternative Name, SAN) | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie die SQL Server Reporting Services und den Power BI-Berichtsserver für die Verwendung eines alternativen Antragstellernamens konfigurieren, indem Sie die Datei „rsreportserver.config“ ändern und das Tool „Netsh.exe“ verwenden.
ms.date: 09/27/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cf1db4f6e07609ce6da38569732f7dba333f86ff
ms.sourcegitcommit: b93beb4f03aee2c1971909cb1d15f79cd479a35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91497204"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name-san"></a>Konfigurieren der Reporting Services für die Verwendung eines alternativen Antragstellernamens (Subject Alternative Name, SAN)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

In diesem Artikel wird erklärt, wie Sie die Reporting Services (SSRS) und den Power BI-Berichtsserver für die Verwendung eines alternativen Antragstellernamens (SAN) konfigurieren, indem Sie die Datei „rsreportserver.config“ ändern und das Tool „Netsh.exe“ verwenden.

Diese Anleitung gilt sowohl für die Webdienst-URL als auch für die Webportal-URL im Berichtsserver-Konfigurations-Manager-Tool.

Zum Verwenden eines SAN muss das TLS/SSL-Zertifikat auf dem Server registriert und signiert sein und über den privaten Schlüssel verfügen. Sie können keine selbstsignierten Zertifikate verwenden.

URLs in den Reporting Services und dem Power BI-Berichtsserver können für die Verwendung eines TLS/SSL-Zertifikats konfiguriert werden. Ein Zertifikat verfügt normalerweise nur über einen Antragstellernamen, der nur eine URL für eine TLS-Sitzung (Transport Layer Security, früher als Secure Sockets Layer, SSL, bezeichnet) zulässt. Der SAN ist ein zusätzliches Feld im Zertifikat, über das ein TLS-Zertifikat auf viele URLs lauschen kann. Außerdem kann der TLS-Port dadurch mit anderen Anwendungen gemeinsam verwendet werden. Ein SAN kann z. B. so aussehen: `www.myreports.com`.

Weitere Informationen zu TLS-Einstellungen für Reporting Services finden Sie unter [Konfigurieren von TLS-Verbindungen auf einem Berichtsserver im einheitlichen Modus](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).  
  
## <a name="configure-to-use-a-subject-alternative-name-for-web-service-url"></a>Konfigurieren für die Verwendung eines alternativen Antragstellernamens für die Webdienst-URL
  
1.  Starten Sie den Berichtsserver-Konfigurations-Manager.  
  
     Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).  
  
2.  Wählen Sie auf der Seite **Webdienst-URL** einen TLS/SSL-Port und ein TLS/SSL-Zertifikat aus.  
  
     ![Reporting Services-Konfigurations-Manager](../../reporting-services/report-server-sharepoint/media/reportingservices-configurationmanager.png "Reporting Services-Konfigurations-Manager")  
  
     Der Konfigurations-Manager registriert das TLS/SSL-Zertifikat für den Port.  
  
3.  Öffnen Sie die Datei rsreportserver.config.  
  
     Für SSRS 2016 im einheitlichen Modus befindet sich die Datei standardmäßig im folgenden Ordner:  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
     Für SSRS 2017 und höher befindet sich die Datei standardmäßig im folgenden Ordner:  
  
    ```  
    \Program Files\Microsoft SQL Server Reporting Services\SSRS\ReportServer  
    ```  
    
     Für den Power BI-Berichtsserver befindet sich die Datei standardmäßig im folgenden Ordner:  
  
    ```  
    \Program Files\Microsoft Power BI Report Server\PBIRS\ReportServer  
    ```  
  
4.  Kopieren Sie den URL-Abschnitt für die Anwendung **ReportServerWebService**.
  
     Im Folgenden wird beispielsweise der Original-URL-Abschnitt dargestellt:  
  
    ```  
        <URL>  
         <UrlString>https://+:443</UrlString>  
         <AccountSid>S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051</AccountSid>  
         <AccountName>NT Service\ReportServer</AccountName>  
        </URL>  
  
    ```  
  
     Im Folgenden wird der modifizierte URL-Abschnitt dargestellt:
  
    ```  
    <URL>  
         <UrlString>https://+:443</UrlString>  
         <AccountSid>S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051</AccountSid>  
         <AccountName>NT Service\ReportServer</AccountName>  
        </URL>  
        <URL>  
         <UrlString>https://www.myreports.com:443</UrlString>  
         <AccountSid>S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051/AccountSid>  
         <AccountName>NT Service\ReportServer</AccountName>  
        </URL>  
  
    ```  
  
  > [!TIP]  
>  * Für SSRS 2017 und höher ist der Wert für `AccountSid` `S-1-5-80-4050220999-2730734961-1537482082-519850261-379003301` und der Wert für `AccountName` `NT SERVICE\SQLServerReportingServices`.
>  * Für den Power BI-Berichtsserver ist der Wert für `AccountSid` `S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663` und der Wert für `AccountName` `NT SERVICE\PowerBIReportServer`.
  
5.  Speichern Sie die Datei rsreportserver.config.  
  
6.  Starten Sie eine Eingabeaufforderung über **Als Administrator ausführen**, und führen Sie das Tool Netsh.exe aus.  
  
    ```  
    C:\windows\system32\netsh  
    ```  
  
7.  Wechseln Sie zum HTTP-Kontext, indem Sie Folgendes eingeben.  
  
    ```  
    Netsh>http  
    ```  
  
8.  Zeigen Sie die vorhandenen URL-ACLs an, indem Sie Folgendes eingeben:
  
    ```  
    Netsh http>show urlacl  
    ```  
  
     Ein Eintrag wie der folgenden wird angezeigt.  
  
    ```  
    Reserved URL            : https://+:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051)  
    ```  
  
     Eine URL-ACL ist eine besitzverwaltete Zugriffssteuerungsliste (Discretionary Access Control List, DACL) für eine reservierte URL.  
  
9. Erstellen Sie einen neuen Eintrag für den alternativen Antragstellernamen mit denselben Werten für Benutzer und SDDL wie beim vorhandenen Eintrag, indem Sie Folgendes eingeben:  
  
    ```  
    netsh http>add urlacl  url=https://www.myreports.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051)  
  
    ```  
  
10. Erstellen Sie für die **Webportal-URL** einen neuen Eintrag für den alternativen Antragstellernamen, indem Sie Folgendes eingeben:

    ```  
    netsh http>add urlacl  url=https://www.myreports.com:443/Reports  
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051)  
  
    ```  
> [!TIP]  
>  * Für SSRS 2017 und höher ist der Wert für `user` `NT SERVICE\SQLServerReportingServices` und der Wert für `sddl` `D:(A;;GX;;;S-1-5-80-4050220999-2730734961-1537482082-519850261-379003301)`.
>  * Für den Power BI-Berichtsserver ist der Wert für `user` `NT SERVICE\PowerBIReportServer` und der Wert für `sddl` `S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663`.

> [!NOTE]  
> Für den Power BI-Berichtsserver müssen Sie zwei weitere Einträge für den alternativen Antragstellernamen erstellen, indem Sie Folgendes eingeben:
>  * `add urlacl url=https://www.myreports.com:443/PowerBI user="NT SERVICE\PowerBIReportServer" sddl=D:(A;;GX;;;S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663)`
>  * `add urlacl url=https://www.myreports.com:443/wopi user="NT SERVICE\PowerBIReportServer" sddl=D:(A;;GX;;;S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663)`

11. Klicken Sie im Berichtsserver-Konfigurations-Manager auf der Seite **Berichtsserverstatus** auf **Beenden**, und klicken Sie dann auf **Starten**, um den Berichtsserver neu zu starten.  
  
## <a name="see-also"></a>Weitere Informationen

 [RsReportServer.config-Konfigurationsdatei](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Konfigurations-Manager für Reporting Services](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Ändern einer Reporting Services-Konfigurationsdatei](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [Konfigurieren von Berichtsserver-URLs](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
