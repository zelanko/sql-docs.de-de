---
title: Claims to Windows Token Service (C2WTS) und Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e08be032df493913cc6cebf5ae29d583f26c86ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66096552"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Claims to Windows Token Service (C2WTS) und Reporting Services
  Claims to Windows Token Service (c2WTS) von SharePoint ist erforderlich, mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus sollten Sie Windows-Authentifizierung für Datenquellen verwenden, die außerhalb der SharePoint-Farm liegen. Dies gilt auch, wenn der Benutzer über die Windows-Authentifizierung auf die Datenquellen zugreift, weil die Kommunikation zwischen dem Web-Front-End (WFE) und dem gemeinsamen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienst immer der forderungsbasierten Authentifizierung unterliegt.  
  
 c2WTS wird auch dann benötigt, auch sich die Datenquelle(n) auf demselben Computer wie der gemeinsame Dienst befinden. In diesem Szenario ist jedoch keine eingeschränkte Delegierung erforderlich.  
  
 Die von c2WTS erstellten Token funktionieren nur bei der eingeschränkten Delegierung (Einschränkungen für bestimmte Dienste) und bei Verwendung der Konfigurationsoption "Beliebiges Authentifizierungsprotokoll verwenden". Wenn sich die Datenquellen auf demselben Computer wie der gemeinsame Dienst befinden, ist wie oben bereits erwähnt keine eingeschränkte Delegierung erforderlich.  
  
 Wenn in der Umgebung die eingeschränkte Kerberos-Delegierung verwendet wird, dann müssen sich der SharePoint Server-Dienst und externe Datenquellen in derselben Windows-Domäne befinden. Jeder Dienst, der auf C2WTS (Claims to Windows Token Service) basiert, muss die **eingeschränkte** Kerberos-Delegierung verwenden, damit C2WTS den Kerberos-Protokollübergang verwenden kann, um Ansprüche (Claims) in Windows-Anmeldeinformationen zu übersetzen. Diese Anforderungen gelten für alle gemeinsamen SharePoint-Dienste. Weitere Informationen finden Sie unter [Übersicht über die Kerberos-Authentifizierung für Microsoft SharePoint 2010-Produkte (https://technet.microsoft.com/library/gg502594.aspx)](https://technet.microsoft.com/library/gg502594.aspx).  
  
 Die Prozedur wird in diesem Thema zusammengefasst.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
> [!NOTE]  
>  Hinweis: Einige der Konfigurationsschritte ändern möglicherweise oder funktionieren möglicherweise nicht in bestimmten farmtopologien. Bei der Installation eines einzelnen Servers werden beispielsweise keine Windows Identity Foundations-c2WTS-Dienste unterstützt, sodass Claims to Windows Token-Delegierungsszenarien innerhalb dieser Farmkonfiguration nicht zulässig sind.  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>Grundlegende Schritte für die c2WTS-Konfiguration  
  
1.  Konfigurieren Sie das c2WTS-Dienstkonto. Fügen Sie das Dienstkonto der lokalen Administratorengruppe auf jedem Anwendungsserver, auf dem c2WTS ausgeführt wird, hinzu. Stellen Sie außerdem sicher, dass das Konto über die folgenden lokalen Sicherheitsrichtlinienrechte verfügt:  
  
    -   Einsetzen als Teil des Betriebssystems  
  
    -   Annehmen der Identität eines Clients nach der Authentifizierung  
  
    -   Anmelden als Dienst  
  
     Das Konto, das Sie für c2WTS verwenden, außerdem muss für die eingeschränkte Delegierung mit Protokollübergang konfiguriert werden und benötigt Berechtigungen, um die Delegierung an Dienste, die dies erforderlich ist, für die Kommunikation mit (d. h. SQL Server-Engine, SQL Server Analysis Services). Zum Konfigurieren der Delegierung können Sie das Active Directory-Benutzer und Computer-Snap-in.  
  
    1.  Klicken Sie mit der rechten Maustaste auf jedes Dienstkonto, und öffnen Sie das Eigenschaftendialogfeld. Klicken Sie im Dialogfeld auf die Registerkarte **Delegierung** .  
  
        > [!NOTE]  
        >  Hinweis: Die Registerkarte Delegierung ist nur sichtbar, wenn dem Objekt ein SPN zugewiesen wurde. C2WTS erfordert grundsätzlich keinen SPN für das C2WTS-Konto; ohne einen SPN ist die Registerkarte **Delegierung** jedoch nicht sichtbar. Eine Alternative zur Konfiguration der eingeschränkten Delegierung ist die Verwendung des Hilfsprogramms **ADSIEdit**.  
  
    2.  Wesentliche Konfigurationsoptionen auf der Registerkarte "Delegierung":  
  
        -   Wählen Sie "Benutzer bei Delegierungen angegebener Dienste vertrauen"  
  
        -   Wählen Sie "Beliebiges Authentifizierungsprotokoll verwenden"  
  
         Weitere Informationen finden Sie im Abschnitt "Konfigurieren der eingeschränkten Kerberos-Delegierung für Computer und Dienstkonten" im folgenden Whitepaper [Konfigurieren der Kerberos-Authentifizierung für SharePoint 2010 und SQL Server 2008 R2-Produkte](http://blogs.technet.com/b/tothesharepoint/archive/2010/07/22/whitepaper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products.aspx)  
  
2.  Konfigurieren von c2WTS 'AllowedCallers'  
  
     c2WTS erfordert explizit die Identitäten der 'Aufrufer' in der Konfigurationsdatei aufgelisteten **c2wtshost.exe.config**. c2WTS akzeptiert keine Anforderungen sämtlicher authentifizierter Benutzer im System, es sei denn, sie zu diesem Zweck konfiguriert ist. In diesem Fall entspricht der „Aufrufer“ der WSS_WPG-Windows-Gruppe. Die Datei c2wtshost.exe.config wird im folgenden Ordner gespeichert:  
  
     **\Program Files\Windows Identity Foundation\v3.5\c2wtshost.exe.config**  
  
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
  
3.  Starten Sie den c2WTS-Dienst des Betriebssystems:  
  
    1.  Konfigurieren Sie den Dienst für die Verwendung des Dienstkontos, das Sie im vorangehenden Schritt konfiguriert haben.  
  
    2.  Ändern Sie den Starttyp in "**automatische**", und starten Sie den Dienst.  
  
4.  Starten Sie die SharePoint-"Claims to Windows Token Service": Starten Sie den Claims to Windows Token Service über die SharePoint-Zentraladministration auf der Seite **Dienste auf dem Server verwalten**. Der Dienst sollte auf dem Server gestartet werden, auf dem die Aktion ausgeführt wird. Wenn Sie z.B. über einen WFE-Server und einen Anwendungsserver verfügen, auf dem der gemeinsame Dienst von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ausgeführt wird, müssen Sie C2WTS nur auf dem Anwendungsserver starten. c2WTS wird auf dem WFE-Server nicht benötigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Ansprüche an den Windows-Tokendienst (c2WTS) () (Übersicht)https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx)   
 [Übersicht über die Kerberos-Authentifizierung für Microsoft SharePoint 2010-Produkte)https://technet.microsoft.com/library/gg502594.aspx)](https://technet.microsoft.com/library/gg502594.aspx)  
  
  
