---
title: Dienst Konto (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serviceaccount.F1
ms.assetid: face8120-4d32-4c6c-a1e8-99f27d1ff15d
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: db98f9806f48699af996a33675138150803e8812
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952396"
---
# <a name="service-account-ssrs-native-mode"></a>Dienstkonto (einheitlicher SSRS-Modus)
  Auf der Seite Dienstkonto können Sie angeben, unter welchem Konto der Berichtsserverdienst ausgeführt wird. Dieses Konto wird ursprünglich beim Setup konfiguriert. Sie können es ändern, wenn Sie das Konto oder das Kennwort ändern möchten. Der Report Server-Webdienst, der Berichts-Manager und die Hintergrundverarbeitungsanwendung werden unter der Dienstidentität ausgeführt, die auf dieser Seite angegeben wird.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus.  
  
 Das Konto, das Sie für den Berichtsserver-Dienst angeben, muss über entsprechende Berechtigungen verfügen, um auf die Registrierung, die Berichtsserver-Programmdateien und die Berichtsserver-Datenbank zugreifen zu können. Die Berechtigungen für das Konto werden beim Festlegen des Kontos mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager automatisch konfiguriert. Wenn Sie das Dienst Konto verwenden, um eine Verbindung mit der Berichts Server-Datenbank herzustellen, erstellt der Configuration Manager einen Daten Bank Anmelde Namen für das Konto und konfiguriert die Daten Bank Berechtigungen, indem er das Konto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Rolle RSExecRole für die Instanz zuweist, die die Berichts Server-Datenbank hostet. Die Berichtsserver-Datenbank ist der einzige Datenspeicher, in den ein Berichtsserver schreibt. Das Dienstkonto benötigt keine Berechtigungen für andere Datenspeicher.  
  
 Um diese Seite zu öffnen, starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, und klicken Sie auf den Link im Navigationsbereich. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
> [!IMPORTANT]  
>  Es wird nachdrücklich empfohlen, immer den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager zum Aktualisieren des Kontos oder des Kennworts zu verwenden. Mithilfe des Konfigurations-Managers wird sichergestellt, dass andere interne Einstellungen, die von der Dienstidentität abhängen, automatisch aktualisiert werden.  
  
## <a name="options"></a>Tastatur  
 **Verwenden eines integrierten Kontos**  
 Wählen Sie **Netzwerkdienst**, **Lokales System**oder **Lokaler Dienst** aus der Liste aus. Es wird empfohlen, die Einstellung **Netzwerkdienst** zu verwenden; Sie können das Konto jedoch für jedes verfügbare Konto konfigurieren.  
  
 **Verwenden eines anderen Kontos**  
 Wählen Sie diese Option aus, um ein Windows-Benutzerkonto anzugeben. Sie können ein lokales Windows-Benutzerkonto oder ein Domänen-Benutzerkonto eingeben. Geben Sie ein Domänen Konto im folgenden Format an: * \< \\ Domäne\>><Benutzer*. Geben Sie ein lokales Windows-Benutzerkonto im folgenden Format an: * \<Computername>\\ \><Benutzer*. Sie können nur ein vorhandenes Konto auswählen. Während der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfiguration kann kein neues Konto erstellt werden.  
  
 Die maximale Zeichenlänge für das Konto beträgt 20 Zeichen.  
  
 Wenn die Kerberos-Authentifizierung für das Netzwerk verwendet wird und der Berichtsserver für ein Domänenbenutzerkonto konfiguriert ist, müssen Sie den Dienst für das Benutzerkonto registrieren. Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens (SPN) für einen Berichtsserver](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
 Wenn Sie den Kontotyp wechseln (wenn Sie beispielsweise ein Windows-Konto durch ein anderes oder ein integriertes Konto durch ein Windows-Domänenkonto ersetzen), werden Sie aufgefordert, eine Sicherungskopie des Verschlüsselungsschlüssels zu erstellen. Die Sicherungskopie wird automatisch wiederhergestellt, sobald Sie das neue Konto auswählen.  
  
> [!NOTE]  
>  Jedes Mal, wenn Sie das Dienstkonto verändern, werden Sie vom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager aufgefordert, den Verschlüsselungsschlüssel zu sichern und wiederherzustellen. Diese Schritte sind notwendig, weil sie sicherstellen, dass der Berichtsserver weiterhin auf die verschlüsselten Daten zugreifen kann. Weitere Informationen zu diesen Aktionen finden Sie unter [Verschlüsselungsschlüssel &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md).  
  
 Falls Sie außerdem mit einem Berichtsserver arbeiten, der für die Ausführung im integrierten SharePoint-Modus konfiguriert ist, und Sie das Dienstkonto mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager ändern, müssen Sie außerdem die SharePoint-Zentraladministration öffnen und die Seite [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **in der** verwenden, um die Berichtsserver- und Instanzeneinstellungen erneut anzuwenden. Mit diesem Schritt wird dem neuen Dienstkonto Zugriff auf die SharePoint-Datenbanken gewährt. Dies ist für die Integration von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mit einem SharePoint-Produkt bzw. einer SharePoint-Technologie erforderlich. Weitere Informationen zum Gewähren des Datenbankzugriffs in der SharePoint-zentral Administration finden Sie unter [Konfiguration und Verwaltung eines Berichts Servers &#40;Reporting Services SharePoint-Modus&#41;](../../../2014/reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md) und [Reporting Services Installation im SharePoint-Modus &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
## <a name="choosing-an-account"></a>Auswählen eines Kontos  
 Geben Sie am besten ein Konto an, das über Berechtigungen für Netzwerkverbindungen verfügt und auf die Netzwerkdomänencontroller und die SMTP-Server oder -Gateways des Unternehmens zugreifen kann. In der folgenden Tabelle werden die Konten zusammengefasst und Empfehlungen für ihre Verwendung gegeben.  
  
|Konto|Erklärung|  
|-------------|-----------------|  
|Domänenbenutzerkonten|Wenn Sie über ein Windows-Domänenbenutzerkonto verfügen, das mindestens die für Berichtsservervorgänge erforderlichen Berechtigungen aufweist, sollten Sie dieses verwenden.<br /><br /> Ein Domänenbenutzerkonto wird empfohlen, da es den Berichtsserverdienst von anderen Anwendungen trennt. Wenn Sie mehrere Anwendungen unter einem freigegebenen Konto wie Netzwerkdienst ausführen, steigt das Risiko, dass böswillige Benutzer die Kontrolle über den Berichtsserver erlangen, da sich eine Sicherheitsverletzung in einer Anwendung leicht auf alle anderen Anwendungen auswirken kann, die unter diesem Konto ausgeführt werden.<br /><br /> Ein Domänenbenutzerkonto ist erforderlich, wenn Sie den Berichtsserver für eingeschränkte Delegierung konfiguieren oder für den integrierten SharePoint-Modus mit SharePoint 2010-Produkten, die Domänenbenutzerkonten eher als integrierte Computerkonten erfordern.<br /><br /> Wenn Sie ein Domänenbenutzerkonto verwenden, ist eine Änderung Ihres Kennworts in regelmäßigen Abständen erforderlich, sofern eine entsprechende Richtlinie von Ihrer Organisation angewendet wird. Möglicherweise müssen Sie auch den Dienst für das Benutzerkonto registrieren. Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens (SPN) für einen Berichtsserver](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).<br /><br /> Verwenden Sie kein lokales Windows-Benutzerkonto. Lokale Konten weisen in der Regel keine ausreichenden Berechtigungen für den Zugriff auf Ressourcen auf anderen Computern auf. Weitere Informationen über Einschränkungen der Berichtsserverfunktion bei Verwendung lokaler Konten finden Sie unter [Überlegungen zur Verwendung lokaler Konten](#localaccounts) in diesem Thema.|  
|**Netzwerkdienst**|**Netzwerkdienst** ist ein integriertes Konto mit geringsten Rechten, das über Berechtigungen für die Netzwerk Anmeldung verfügt. Dieses Konto wird empfohlen, wenn kein Domänenbenutzerkonto verfügbar ist oder wenn Sie mögliche Dienstausfälle aufgrund von Richtlinien zum Ablauf von Kennwörtern vermeiden möchten.<br /><br /> Versuchen Sie, die Anzahl der Dienste, die unter einem Konto ausgeführt werden, so gering wie möglich zu halten, wenn Sie **Netzwerkdienst**auswählen. Eine Sicherheitsverletzung bei einer Anwendung gefährdet die Sicherheit aller anderen Anwendungen, die unter diesem Konto ausgeführt werden.|  
|**Lokaler Dienst**|Der **lokale Dienst** ist ein integriertes Konto, das einem authentifizierten lokalen Windows-Benutzerkonto ähnelt. Bei Diensten, die unter dem Konto **Lokaler Dienst** ausgeführt werden, erfolgt der Zugriff auf Netzwerkressourcen als NULL-Sitzung ohne Anmeldeinformationen. Dieses Konto ist nicht für Bereitstellungsszenarien im Intranet geeignet, bei denen eine Verbindung zwischen dem Berichtsserver und einer Remoteberichtsserver-Datenbank oder einem Netzwerkdomänencontroller hergestellt werden muss, um einen Benutzer vor dem Öffnen eines Berichts oder vor dem Verarbeiten eines Abonnements zu authentifizieren.|  
|**Lokales System**|Das **lokale System** Konto ist ein Konto mit hohen Berechtigungen, das für die Ausführung eines Berichts Servers nicht erforderlich ist. Verwenden Sie dieses Konto nicht für Berichtsserverinstallationen. Wählen Sie stattdessen ein Domänenkonto oder einen **Netzwerkdienst** aus.|  
  
##  <a name="localaccounts"></a>Überlegungen zur Verwendung lokaler Konten  
 Die vorrangige Überlegung im Hinblick auf die Verwendung lokaler Konten ist, ob der Berichtsserver auf Remotedatenbankserver, Mailserver und Domänencontroller zugreifen muss. Wenn Sie den Berichtsserver als lokales Windows-Benutzerkonto, lokalen Dienst oder lokales System konfigurieren, müssen bestimmte Überlegungen bei anderen Konfigurationseinstellungen sowie bei der Erstellung und Übermittlung von Abonnements berücksichtigt werden:  
  
-   Durch die Ausführung des Dienstes unter einem lokalen Konto werden die Optionen eingeschränkt, die später beim Konfigurieren einer Verbindung mit einer Remoteberichtsserver-Datenbank verfügbar sind. Genauer gesagt: Wenn Sie eine Remoteberichtsserver-Datenbank verwenden, müssen Sie die Verbindung so konfigurieren, dass ein Domänenbenutzerkonto oder ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankbenutzer verwendet wird, das bzw. der über die Berechtigung zur Anmeldung an der Remoteinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügt.  
  
-   Mit der Ausführung des Dienstes unter einem lokalen Konto sind neue Anforderungen im Hinblick auf die Erstellung von Abonnements verbunden. Der Berichtsserver speichert Informationen zum Benutzer, der das Abonnement erstellt. Wenn der Benutzer das Abonnement erstellt, während er mit einem Domänenkonto angemeldet ist, versucht der Berichtsserver-Dienst, eine Verbindung mit einem Domänencontroller herzustellen, um den Benutzer zu authentifizieren, wenn das Abonnement verarbeitet wird. Wenn der Dienst unter einem lokalen Konto ausgeführt wird, löst die Authentifizierungsanforderung einen Fehler aus, wenn der Berichtsserver versucht, die Anforderung an einen Remotedomänencontroller zu senden. Sie können diese Beschränkung umgehen, indem Sie eine formularbasierte Authentifizierungserweiterung verwenden oder alle Benutzer anweisen, die Verbindung mit einem Berichtsserver über ein lokales Benutzerkonto herzustellen.  
  
-   Mit der Ausführung des Dienstes unter einem lokalen Konto sind neue Anforderungen im Hinblick auf die Übermittlung von Abonnements verbunden. Die Abonnementdefinitionen einiger Übermittlungserweiterungen enthalten Benutzerkontoinformationen. Wenn Sie Berichte an E-Mail-Adressen senden, die auf Domänenbenutzerkonten basieren, und den Berichtsserver-Dienst unter einem lokalen Konto ausführen, kann dieser zum Auflösen der Ziel-E-Mail-Konten nicht auf einen Remotedomänencontroller zugreifen.  
  
-   Integrierte Windows-Dienstkonten (Lokaler Dienst oder Netzwerkdienst) werden auf einem Domänencontrollercomputer nicht als Berichtsserver-Dienstkonten unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren eines Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)   
 [Konfigurations-Manager für Reporting Services F1-Hilfe Themen &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
