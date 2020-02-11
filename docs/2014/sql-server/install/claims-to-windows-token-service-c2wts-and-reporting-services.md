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
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 0ec82b7cca2062e1ed918e300eeb76dad16cbb20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75245622"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Claims to Windows Token Service (C2WTS) und Reporting Services
  Der SharePoint claims to Windows Token Service (c2WTS) ist im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus erforderlich, wenn Sie die Windows-Authentifizierung für Datenquellen verwenden möchten, die sich außerhalb der SharePoint-Farm befinden. Dies gilt auch, wenn der Benutzer über die Windows-Authentifizierung auf die Datenquellen zugreift, weil die Kommunikation zwischen dem Web-Front-End (WFE) und dem gemeinsamen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienst immer der forderungsbasierten Authentifizierung unterliegt.  
  
 c2WTS wird auch dann benötigt, auch sich die Datenquelle(n) auf demselben Computer wie der gemeinsame Dienst befinden. In diesem Szenario ist jedoch keine eingeschränkte Delegierung erforderlich.  
  
 Die von c2WTS erstellten Token funktionieren nur bei der eingeschränkten Delegierung (Einschränkungen für bestimmte Dienste) und bei Verwendung der Konfigurationsoption "Beliebiges Authentifizierungsprotokoll verwenden". Wenn sich die Datenquellen auf demselben Computer wie der gemeinsame Dienst befinden, ist wie oben bereits erwähnt keine eingeschränkte Delegierung erforderlich.  
  
 Wenn in der Umgebung die eingeschränkte Kerberos-Delegierung verwendet wird, dann müssen sich der SharePoint Server-Dienst und externe Datenquellen in derselben Windows-Domäne befinden. Jeder Dienst, der auf C2WTS (Claims to Windows Token Service) basiert, muss die **eingeschränkte** Kerberos-Delegierung verwenden, damit C2WTS den Kerberos-Protokollübergang verwenden kann, um Ansprüche (Claims) in Windows-Anmeldeinformationen zu übersetzen. Diese Anforderungen gelten für alle gemeinsamen SharePoint-Dienste. Weitere Informationen finden Sie unter [Übersicht über die Kerberos-Authentifizierung für Microsoft SharePoint 2010https://technet.microsoft.com/library/gg502594.aspx)-Produkte (](https://technet.microsoft.com/library/gg502594.aspx).  
  
 Die Prozedur wird in diesem Thema zusammengefasst.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
> [!NOTE]  
>  Hinweis: Einige der Konfigurationsschritte ändern sich möglicherweise oder funktionieren nicht in bestimmten Farmtopologien. Bei der Installation eines einzelnen Servers werden beispielsweise keine Windows Identity Foundations-c2WTS-Dienste unterstützt, sodass Claims to Windows Token-Delegierungsszenarien innerhalb dieser Farmkonfiguration nicht zulässig sind.  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>Grundlegende Schritte für die c2WTS-Konfiguration  
  
1.  Konfigurieren Sie das c2WTS-Dienstkonto. Fügen Sie das Dienstkonto der lokalen Administratorengruppe auf jedem Anwendungsserver, auf dem c2WTS ausgeführt wird, hinzu. Stellen Sie außerdem sicher, dass das Konto über die folgenden lokalen Sicherheitsrichtlinienrechte verfügt:  
  
    -   Einsetzen als Teil des Betriebssystems  
  
    -   Annehmen der Identität eines Clients nach der Authentifizierung  
  
    -   Anmelden als Dienst  
  
     Das Konto, das Sie für c2WTS verwenden, muss außerdem für die eingeschränkte Delegierung mit Protokoll Übergang konfiguriert werden. Außerdem benötigt es Berechtigungen zum Delegieren an die Dienste, mit denen es kommunizieren muss (d. h. SQL Server-Engine SQL Server Analysis Services). Zum Konfigurieren der Delegierung können Sie das Snap-in "Active Directory-Benutzer und-Computer" verwenden.  
  
    1.  Klicken Sie mit der rechten Maustaste auf jedes Dienstkonto, und öffnen Sie das Eigenschaftendialogfeld. Klicken Sie im Dialogfeld auf die Registerkarte **Delegierung** .  
  
        > [!NOTE]  
        >  Hinweis: Die Registerkarte Delegierung ist nur sichtbar, wenn dem Objekt ein SPN zugewiesen wurde. c2WTS erfordert keinen Dienst Prinzipal Namen (SPN) für das c2WTS-Konto. die Registerkarte " **Delegierung** " ist jedoch nicht sichtbar. Eine Alternative zur Konfiguration der eingeschränkten Delegierung ist die Verwendung des Hilfsprogramms **ADSIEdit**.  
  
    2.  Wesentliche Konfigurationsoptionen auf der Registerkarte "Delegierung":  
  
        -   Wählen Sie "diesen Benutzer nur bei Delegierungen angegebener Dienste vertrauen" aus.  
  
        -   Wählen Sie "beliebiges Authentifizierungsprotokoll verwenden" aus.  
  
         Weitere Informationen finden Sie im Abschnitt "Konfigurieren der eingeschränkten Kerberos-Delegierung für Computer und Dienst Konten" im folgenden Whitepaper: [Konfigurieren der Kerberos-Authentifizierung für SharePoint 2010-und SQL Server 2008 R2-Produkte](https://blogs.technet.com/b/tothesharepoint/archive/2010/07/22/whitepaper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products.aspx) .  
  
2.  Konfigurieren von c2WTS ' ' ' Zuweisung ' '  
  
     c2WTS erfordert, dass die Identitäten der "Aufrufer" in der Konfigurationsdatei **Datei c2wtshost. exe. config**explizit aufgeführt sind. c2WTS akzeptiert keine Anforderungen von allen authentifizierten Benutzern im System, es sei denn, dies ist dafür konfiguriert. In diesem Fall entspricht der „Aufrufer“ der WSS_WPG-Windows-Gruppe. Die Datei c2wtshost.exe.config wird im folgenden Ordner gespeichert:  
  
     **\Programme\Windows Identity foundation\v3.5 \c2wtshost.exe.config**  
  
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
  
    2.  Ändern Sie den Starttyp in "**automatisch**", und starten Sie den Dienst.  
  
4.  Starten Sie den SharePoint-claims to Windows Token Service (claims to Windows Token Service): Starten Sie den Claims to Windows Token Service über die SharePoint-zentral Administration auf der Seite **Dienste auf dem Server verwalten** . Der Dienst sollte auf dem Server gestartet werden, auf dem die Aktion ausgeführt wird. Wenn Sie z.B. über einen WFE-Server und einen Anwendungsserver verfügen, auf dem der gemeinsame Dienst von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ausgeführt wird, müssen Sie C2WTS nur auf dem Anwendungsserver starten. c2WTS wird auf dem WFE-Server nicht benötigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über claims to Windows Token Service (c2WTS) (https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx)   
 [Übersicht über die Kerberos-Authentifizierung für Microsoft SharePoint 2010-Produkte (https://technet.microsoft.com/library/gg502594.aspx)](https://technet.microsoft.com/library/gg502594.aspx)  
  
