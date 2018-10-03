---
title: Dienstkonto (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serviceaccount.F1
ms.assetid: face8120-4d32-4c6c-a1e8-99f27d1ff15d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 96cee57e82cc9fbb01a43dc1ec13bf0691f737fc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079126"
---
# <a name="service-account-ssrs-native-mode"></a>Dienstkonto (einheitlicher SSRS-Modus)
  Auf der Seite Dienstkonto können Sie angeben, unter welchem Konto der Berichtsserverdienst ausgeführt wird. Dieses Konto wird ursprünglich beim Setup konfiguriert. Sie können es ändern, wenn Sie das Konto oder das Kennwort ändern möchten. Der Report Server-Webdienst, der Berichts-Manager und die Hintergrundverarbeitungsanwendung werden unter der Dienstidentität ausgeführt, die auf dieser Seite angegeben wird.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Das Konto, das Sie für den Berichtsserver-Dienst angeben, muss über entsprechende Berechtigungen verfügen, um auf die Registrierung, die Berichtsserver-Programmdateien und die Berichtsserver-Datenbank zugreifen zu können. Alle Berechtigungen für das Konto automatisch konfiguriert bei der Verwendung der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager, um das Konto festzulegen. Wenn Sie das Dienstkonto für die Verbindung mit der Berichtsserver-Datenbank verwenden, den Konfigurations-Manager eine datenbankanmeldung für das Konto erstellt und konfiguriert Berechtigungen für die Datenbank durch Zuweisen des Kontos zur RSExecRole für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her, hostet die Berichtsserver-Datenbank. Die Berichtsserver-Datenbank ist der einzige Datenspeicher, in den ein Berichtsserver schreibt. Das Dienstkonto benötigt keine Berechtigungen für andere Datenspeicher.  
  
 Um diese Seite zu öffnen, starten die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager, und klicken Sie auf den Link im Navigationsbereich. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
> [!IMPORTANT]  
>  Wenn Sie das Konto oder Kennwort aktualisieren müssen, es wird dringend empfohlen, dass Sie verwenden die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager. Mithilfe des Konfigurations-Managers wird sichergestellt, dass andere interne Einstellungen, die von der Dienstidentität abhängen, automatisch aktualisiert werden.  
  
## <a name="options"></a>Tastatur  
 **Verwenden eines integrierten Kontos**  
 Wählen Sie **Netzwerkdienst**, **Lokales System**oder **Lokaler Dienst** aus der Liste aus. Es wird empfohlen, die Einstellung **Netzwerkdienst** zu verwenden; Sie können das Konto jedoch für jedes verfügbare Konto konfigurieren.  
  
 **Ein anderes Konto verwenden**  
 Wählen Sie diese Option aus, um ein Windows-Benutzerkonto anzugeben. Sie können ein lokales Windows-Benutzerkonto oder ein Domänen-Benutzerkonto eingeben. Geben Sie ein Domänenkonto im folgenden Format:  *\<Domäne >\\< Benutzer\>*. Geben Sie ein lokales Windows-Benutzerkonto im folgenden Format:  *\<Computername >\\< Benutzer\>*. Sie können nur ein vorhandenes Konto auswählen. Während der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfiguration kann kein neues Konto erstellt werden.  
  
 Die maximale Zeichenlänge für das Konto beträgt 20 Zeichen.  
  
 Wenn die Kerberos-Authentifizierung für das Netzwerk verwendet wird und der Berichtsserver für ein Domänenbenutzerkonto konfiguriert ist, müssen Sie den Dienst für das Benutzerkonto registrieren. Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens (SPN) für einen Berichtsserver](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
 Wenn Sie den Kontotyp wechseln (wenn Sie beispielsweise ein Windows-Konto durch ein anderes oder ein integriertes Konto durch ein Windows-Domänenkonto ersetzen), werden Sie aufgefordert, eine Sicherungskopie des Verschlüsselungsschlüssels zu erstellen. Die Sicherungskopie wird automatisch wiederhergestellt, sobald Sie das neue Konto auswählen.  
  
> [!NOTE]  
>  Jedes Mal, wenn Sie das Dienstkonto verändern, werden Sie vom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager aufgefordert, den Verschlüsselungsschlüssel zu sichern und wiederherzustellen. Diese Schritte sind notwendig, weil sie sicherstellen, dass der Berichtsserver weiterhin auf die verschlüsselten Daten zugreifen kann. Weitere Informationen zu diesen Aktionen finden Sie unter [Verschlüsselungsschlüssel &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md).  
  
 Darüber hinaus, wenn Sie einen Berichtsserver haben, ist so konfiguriert, dass die Ausführung im integrierten SharePoint-Modus, und Sie das Dienstkonto ändern mithilfe der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager müssen Sie auch SharePoint-Zentraladministration öffnen und verwenden Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **Gewähren von Datenbankzugriff** Seite, um die Einstellungen für Server und die Instanz erneut anwenden. Dieser Schritt wird den neuen Dienstkontenzugriff auf die SharePoint-Datenbanken ist erforderlich, für die Integration von gewährt [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mit einem SharePoint-Produkt oder Technologie. Weitere Informationen über das Gewähren des Datenbankzugriffs in der SharePoint-Zentraladministration finden Sie unter [Konfiguration und Verwaltung eines Berichtsservers &#40;Reporting Services SharePoint Mode&#41; ](../../../2014/reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md) und [ Installation von SharePoint-Modus von Reporting Services &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
## <a name="choosing-an-account"></a>Auswählen eines Kontos  
 Geben Sie am besten ein Konto an, das über Berechtigungen für Netzwerkverbindungen verfügt und auf die Netzwerkdomänencontroller und die SMTP-Server oder -Gateways des Unternehmens zugreifen kann. In der folgenden Tabelle werden die Konten zusammengefasst und Empfehlungen für ihre Verwendung gegeben.  
  
|Konto|Erklärung|  
|-------------|-----------------|  
|Domänenbenutzerkonten|Wenn Sie über ein Windows-Domänenbenutzerkonto verfügen, das mindestens die für Berichtsservervorgänge erforderlichen Berechtigungen aufweist, sollten Sie dieses verwenden.<br /><br /> Ein Domänenbenutzerkonto wird empfohlen, da es den Berichtsserverdienst von anderen Anwendungen trennt. Wenn Sie mehrere Anwendungen unter einem freigegebenen Konto wie Netzwerkdienst ausführen, steigt das Risiko, dass böswillige Benutzer die Kontrolle über den Berichtsserver erlangen, da sich eine Sicherheitsverletzung in einer Anwendung leicht auf alle anderen Anwendungen auswirken kann, die unter diesem Konto ausgeführt werden.<br /><br /> Ein Domänenbenutzerkonto ist erforderlich, wenn Sie den Berichtsserver für eingeschränkte Delegierung konfiguieren oder für den integrierten SharePoint-Modus mit SharePoint 2010-Produkten, die Domänenbenutzerkonten eher als integrierte Computerkonten erfordern.<br /><br /> Wenn Sie ein Domänenbenutzerkonto verwenden, ist eine Änderung Ihres Kennworts in regelmäßigen Abständen erforderlich, sofern eine entsprechende Richtlinie von Ihrer Organisation angewendet wird. Möglicherweise müssen Sie auch den Dienst für das Benutzerkonto registrieren. Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens (SPN) für einen Berichtsserver](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).<br /><br /> Verwenden Sie kein lokales Windows-Benutzerkonto. Lokale Konten weisen in der Regel keine ausreichenden Berechtigungen für den Zugriff auf Ressourcen auf anderen Computern auf. Weitere Informationen über Einschränkungen der Berichtsserverfunktion bei Verwendung lokaler Konten finden Sie unter [Überlegungen zur Verwendung lokaler Konten](#localaccounts) in diesem Thema.|  
|**Netzwerkdienst**|**Netzwerkdienst** ist ein integriertes Konto mit Minimalprivilegien, das über Berechtigungen für die Netzwerkanmeldung verfügt. Dieses Konto wird empfohlen, wenn kein Domänenbenutzerkonto verfügbar ist oder wenn Sie mögliche Dienstausfälle aufgrund von Richtlinien zum Ablauf von Kennwörtern vermeiden möchten.<br /><br /> Versuchen Sie, die Anzahl der Dienste, die unter einem Konto ausgeführt werden, so gering wie möglich zu halten, wenn Sie **Netzwerkdienst**auswählen. Eine Sicherheitsverletzung bei einer Anwendung gefährdet die Sicherheit aller anderen Anwendungen, die unter diesem Konto ausgeführt werden.|  
|**Lokaler Dienst**|**Lokaler Dienst** ist ein integriertes Konto, das einem authentifizierten lokalen Windows-Benutzerkonto entspricht. Bei Diensten, die unter dem Konto **Lokaler Dienst** ausgeführt werden, erfolgt der Zugriff auf Netzwerkressourcen als NULL-Sitzung ohne Anmeldeinformationen. Dieses Konto ist nicht für Bereitstellungsszenarien im Intranet geeignet, bei denen eine Verbindung zwischen dem Berichtsserver und einer Remoteberichtsserver-Datenbank oder einem Netzwerkdomänencontroller hergestellt werden muss, um einen Benutzer vor dem Öffnen eines Berichts oder vor dem Verarbeiten eines Abonnements zu authentifizieren.|  
|**Lokales System**|**Lokales System** ist ein Konto mit weit reichenden Berechtigungen, das für die Ausführung eines Berichtsservers nicht erforderlich ist. Verwenden Sie dieses Konto nicht für Berichtsserverinstallationen. Wählen Sie stattdessen ein Domänenkonto oder einen **Netzwerkdienst** aus.|  
  
##  <a name="localaccounts"></a> Überlegungen zur Verwendung lokaler Konten  
 Die vorrangige Überlegung im Hinblick auf die Verwendung lokaler Konten ist, ob der Berichtsserver auf Remotedatenbankserver, Mailserver und Domänencontroller zugreifen muss. Wenn Sie den Berichtsserver als lokales Windows-Benutzerkonto, lokalen Dienst oder lokales System konfigurieren, müssen bestimmte Überlegungen bei anderen Konfigurationseinstellungen sowie bei der Erstellung und Übermittlung von Abonnements berücksichtigt werden:  
  
-   Durch die Ausführung des Dienstes unter einem lokalen Konto werden die Optionen eingeschränkt, die später beim Konfigurieren einer Verbindung mit einer Remoteberichtsserver-Datenbank verfügbar sind. Genauer gesagt: Wenn Sie eine Remoteberichtsserver-Datenbank verwenden, müssen Sie die Verbindung so konfigurieren, dass ein Domänenbenutzerkonto oder ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankbenutzer verwendet wird, das bzw. der über die Berechtigung zur Anmeldung an der Remoteinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügt.  
  
-   Mit der Ausführung des Dienstes unter einem lokalen Konto sind neue Anforderungen im Hinblick auf die Erstellung von Abonnements verbunden. Der Berichtsserver speichert Informationen zum Benutzer, der das Abonnement erstellt. Wenn der Benutzer das Abonnement erstellt, während er mit einem Domänenkonto angemeldet ist, versucht der Berichtsserver-Dienst, eine Verbindung mit einem Domänencontroller herzustellen, um den Benutzer zu authentifizieren, wenn das Abonnement verarbeitet wird. Wenn der Dienst unter einem lokalen Konto ausgeführt wird, löst die Authentifizierungsanforderung einen Fehler aus, wenn der Berichtsserver versucht, die Anforderung an einen Remotedomänencontroller zu senden. Sie können diese Beschränkung umgehen, indem Sie eine formularbasierte Authentifizierungserweiterung verwenden oder alle Benutzer anweisen, die Verbindung mit einem Berichtsserver über ein lokales Benutzerkonto herzustellen.  
  
-   Mit der Ausführung des Dienstes unter einem lokalen Konto sind neue Anforderungen im Hinblick auf die Übermittlung von Abonnements verbunden. Die Abonnementdefinitionen einiger Übermittlungserweiterungen enthalten Benutzerkontoinformationen. Wenn Sie Berichte an E-Mail-Adressen senden, die auf Domänenbenutzerkonten basieren, und den Berichtsserver-Dienst unter einem lokalen Konto ausführen, kann dieser zum Auflösen der Ziel-E-Mail-Konten nicht auf einen Remotedomänencontroller zugreifen.  
  
-   Integrierte Windows-Dienstkonten (Lokaler Dienst oder Netzwerkdienst) werden auf einem Domänencontrollercomputer nicht als Berichtsserver-Dienstkonten unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren eines Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)   
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
