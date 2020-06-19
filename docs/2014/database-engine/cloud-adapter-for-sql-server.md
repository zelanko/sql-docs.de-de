---
title: Cloudadapter für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cloud adapter
- Deploy to Azure
ms.assetid: 82ed0d0f-952d-4d49-aa36-3855a3ca9877
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 44fce4aba87968a9b7e6acc3e18ae5d966f70d07
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936021"
---
# <a name="cloud-adapter-for-sql-server"></a>Cloud-Adapter für SQL Server
  Der Cloudadapter-Dienst wird als Teil der Bereitstellung [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einer Azure-VM erstellt. Der Cloud-Adapterdienst generiert bei der ersten Ausführung ein selbstsigniertes Zertifikat und wird danach unter dem Konto **Lokales System** ausgeführt. Er generiert eine Konfigurationsdatei, die für die eigene Konfiguration verwendet wird. Der Cloudadapter erstellt außerdem eine Windows-Firewall-Regel, um eingehende TCP-Verbindungen über den Standardport 11435 zuzulassen.  
  
 Der Cloud-Adapter ist ein zustandsloser, synchroner Dienst, der Nachrichten von der lokalen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz empfängt. Beim Beenden des Cloud-Adapterdiensts wird der Remotezugriff für Cloud-Adapter beendet, die Bindung des SSL-Zertifikats aufgehoben und die Windows-Firewall-Regel deaktiviert.  
  
## <a name="cloud-adapter-requirements"></a>Cloud-Adapter-Anforderungen  
 Beachten Sie die folgenden Anforderungen für die Installation, Aktivierung und Ausführung des Cloud-Adapters für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
-   Der Cloud-Adapter wird ab [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 unterstützt. In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 erfordert der Cloud-Adapter für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] SQL Management Objects für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012.  
  
-   Der Cloud-Adapterwebdienst wird unter dem Konto **Lokales System** ausgeführt und überprüft die Clientanmeldeinformationen vor der Ausführung eines Tasks. Die vom Client bereitgestellten Anmelde Informationen müssen zu dem Konto gehören, das Mitglied der lokalen **Administratoren** Gruppe auf dem Remote Computer ist.  
  
-   Der Cloud-Adapter unterstützt nur die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung.  
  
-   Cloud-Adapter verwendet kein sa-Konto, sondern das lokale Administratorkonto der VM, um Befehle auf dem lokalen Computer auszuführen.  
  
-   Cloud-Adapter wartet auf TCP/IP-Verbindungen. Der Standardport ist 11435.  
  
-   Cloud-Adapter muss über Berechtigungen zum Erstellen und Ändern von Windows-Firewall-Regeln verfügen.  
  
## <a name="cloud-adapter-configuration-settings"></a>Cloud-Adapter-Konfigurationseinstellungen  
 Verwenden Sie die folgenden Konfigurationsdetails für Cloud-Adapter, um die Einstellungen für einen Cloud-Adapter zu ändern.  
  
-   **Standardpfad für die Konfigurationsdatei** : c:\Programme\Microsoft SQL server\120\tools\cloudadapter\  
  
-   **Konfigurationsdatei Parameter** -  
  
    -   \<configuration>  
  
        -   \<appSettings>  
  
            -   \<add key="WebServicePort" value="" />  
  
            -   \<add key="WebServiceCertificate" value="GUID" />  
  
            -   \<add key="ExposeExceptionDetails" value="true" />  
  
        -   \</appSettings>  
  
    -   \</configuration>  
  
-   **Zertifikat Details** : das Zertifikat weist die folgenden Werte auf:  
  
    -   Subject-"CN = cloudadapter \<VMName> , DC = SQL Server, DC = Microsoft"  
  
    -   Für das Zertifikat darf nur die Serverauthentifizierung EKU aktiviert sein.  
  
    -   Die Zertifikatschlüssellänge beträgt 2048.  
  
 **Werte der Konfigurationsdatei**:  
  
|Einstellung|Werte|Standard|Kommentare|  
|-------------|------------|-------------|--------------|  
|WebServicePort|1-65535|11435|Wenn nicht angegeben, wird 11435 verwendet.|  
|WebServiceCertificate|Fingerabdruck|Empty|Bei einem leeren Wert wird ein neues selbstsigniertes Zertifikat generiert.|  
|ExposeExceptionDetails|TRUE/FALSE|False||  
  
## <a name="cloud-adapter-troubleshooting"></a>Cloud-Adapter-Problembehandlung  
 Verwenden Sie die folgenden Informationen zur Problembehandlung beim Cloud-Adapter für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
-   **Fehlerbehandlung und Protokollierung** : Fehler und Statusmeldungen werden in das Anwendungs Ereignisprotokoll geschrieben.  
  
-   Ablauf **Verfolgung, Ereignisse** : alle Ereignisse werden in das Anwendungs Ereignisprotokoll geschrieben.  
  
-   **Steuerung, Konfiguration** : Verwenden Sie die Konfigurationsdatei, die sich unter befindet: c:\Programme\Microsoft SQL server\120\tools\cloudadapter \\ .  
  
|Fehler|Fehler-ID|Ursache|Lösung|  
|-----------|--------------|-----------|----------------|  
|Ausnahme beim Hinzufügen des Zertifikats zum Zertifikatspeicher. {Exception text}.|45560|Computer Zertifikat Speicher-Berechtigungen|Stellen Sie sicher, dass der Cloudadapter-Dienst über Berechtigungen zum Hinzufügen von Zertifikaten zum Zertifikat Speicher des Computers verfügt.|  
|Ausnahme bei dem Versuch, die SSL-Bindung für Port {Port number} und Zertifikat {Thumbprint} zu konfigurieren. {Exception}.|45561|Eine andere Anwendung verwendet bereits den Port oder hat ein Zertifikat an diesen gebunden.|Entfernen Sie alle vorhandenen Bindungen, oder ändern Sie in der Konfigurationsdatei den Port für Cloud-Adapter.|  
|Das SSL-Zertifikat [{Thumbprint}] wurde im Zertifikatspeicher nicht gefunden.|45564|Der Fingerabdruck des Zertifikats ist in der Konfigurationsdatei verfügbar, aber das Zertifikat ist im persönlichen Zertifikatspeicher für den Dienst nicht enthalten.<br /><br /> Unzureichende Berechtigungen.|Stellen Sie sicher, dass das Zertifikat im persönlichen Zertifikatspeicher für den Dienst vorhanden ist.<br /><br /> Stellen Sie sicher, dass der Dienst über die erforderlichen Berechtigungen für den Speicher verfügt.|  
|Fehler beim Starten des Webdiensts. {Exception text}.|45570|Wird in der Ausnahme beschrieben.|Aktivieren Sie ExposeExceptionDetails, und lesen Sie die erweiterten Informationen in der Ausnahme.|  
|Das Zertifikat [{Thumbprint}] ist abgelaufen.|45565|In der Konfigurationsdatei wird auf ein abgelaufenes Zertifikat verwiesen.|Fügen Sie ein gültiges Zertifikat hinzu, und aktualisieren Sie die Konfigurationsdatei mit dem Fingerabdruck.|  
|Webdienst Fehler: {0} .|45571|Wird in der Ausnahme beschrieben.|Aktivieren Sie ExposeExceptionDetails, und lesen Sie die erweiterten Informationen in der Ausnahme.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereitstellen einer SQL Server-Datenbank auf einem virtuellen Microsoft Azure-Computer](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)  
  
  
