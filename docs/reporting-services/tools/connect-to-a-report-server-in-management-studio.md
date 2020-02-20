---
title: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio | Microsoft-Dokumentation
ms.date: 05/07/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.connecttors.connectionproperties.f1
- sql13.swb.connecttors.login.f1
- sql13.swb.connection.login.reportserver.f1
helpviewer_keywords:
- report servers [Reporting Services], connections
- connections [Reporting Services], report server
- registering report servers
- report servers [Reporting Services], registering
- Connect to Server dialog box, Reporting Services
ms.assetid: c875ff87-ee7d-443a-a702-bdb4b6c27c6e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 602c939c382bc5946e64340736f73bb88f17c655
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "65574110"
---
# <a name="connect-to-a-report-server-in-management-studio"></a>Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] stellt einen Objekt-Explorer bereit, mit dem Sie eine Verbindung zu einem beliebigen Server der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Familie herstellen und dessen Inhalte grafisch durchsuchen können. Für Reporting Services können Sie den Objekt-Explorer für Folgendes verwenden:

- Aktivieren von Berichtsserverfunktionen.

- Festlegen von Serverstandards und Konfigurieren von Rollendefinitionen.

- Verwalten von ausgeführten Aufträgen.

- Verwalten von Auftragszeitplänen

 Sie können eine Verbindung zu einem Berichtsserver, der im einheitlichen Modus oder im integrierten SharePoint-Modus ausgeführt wird, herstellen. Die Verbindungssyntax und die Vorgänge, die Sie durchführen können, variieren je nach Servermodus des Berichtsservers und Ihren Berechtigungen. Wenn Sie keine Verbindung mit dem Berichtsserver herstellen können oder bei bestimmten Aufgaben Probleme auftreten, verfügen Sie wahrscheinlich nicht über die notwendigen Berechtigungen oder haben den Namen des Berichtsservers falsch angegeben. Weitere Informationen zu Berechtigungen und zur Verbindungssyntax finden Sie in der Tabelle am Ende dieses Artikels.

 Sie können mit dem Objekt-Explorer den Berichtsserverinhalt nicht anzeigen oder verwalten. Die Inhaltsverwaltung erfolgt über das Webportal, wenn der Berichtsserver im einheitlichen Modus ausgeführt wird, oder über eine SharePoint-Website, wenn der Berichtsserver im integrierten SharePoint-Modus ausgeführt wird.

 Mit dem Objekt-Explorer können Sie Verbindungen zu mehreren Serverinstanzen im selben Arbeitsbereich herstellen, solange die Server in derselben Servergruppe registriert sind. Bevor Sie eine Verbindung mit einem Berichtsserver in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]herstellen können, muss der Server registriert werden. Wenn der Berichtsserver bereits registriert ist, können Sie diesen Schritt überspringen. Anweisungen zum Registrieren von Berichtsservern finden Sie am Ende dieses Artikels.

### <a name="to-connect-to-a-native-mode-report-server"></a>So stellen Sie eine Verbindung mit einem Berichtsserver im einheitlichen Modus her

1. Wenn der Objekt-Explorer noch nicht geöffnet ist, öffnen Sie ihn über das Menü **Ansicht**.

2. Klicken Sie auf **Verbinden**, um die Liste der Servertypen anzuzeigen, und wählen Sie dann **Reporting Services** aus.

3. Geben Sie im Dialogfeld **Verbindung mit Server herstellen** den Namen der Berichtsserverinstanz ein. Die Namen von Berichtsserverinstanzen basieren auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanznamen. Standardmäßig ist der Instanzname eines lokalen Berichtsservers der Computername. Wenn Sie den Berichtsserver als benannte Instanz installiert haben, müssen Sie den Server mit der folgenden Syntax angeben: *\<Servername>[\\<Instanzname\>]* .

4. Wählen Sie den **Authentifizierungstyp** aus. Wenn Sie die Windows-Authentifizierung verwenden, stellen Sie die Verbindung mit Ihren Anmeldeinformationen her. Wenn Sie die Standardauthentifizierung oder die Formularauthentifizierung auswählen, geben Sie das Konto und das Kennwort ein.  
  
5. Wählen Sie **Verbinden**. Der Berichtsserver wird im Objekt-Explorer angezeigt.  

6. Klicken Sie mit der rechten Maustaste auf den Serverknoten, um Systemeigenschaften und Standardeinstellungen für den Server festzulegen. Weitere Informationen finden Sie unter [Festlegen von Berichtsservereigenschaften (Management Studio)](../../reporting-services/tools/set-report-server-properties-management-studio.md).

### <a name="to-connect-to-a-sharepoint-integrated-mode-report-server"></a>So stellen Sie eine Verbindung mit einem Berichtsserver im integrierten SharePoint-Modus her  

1. Wenn der Objekt-Explorer noch nicht geöffnet ist, öffnen Sie ihn über das Menü **Ansicht**.

2. Klicken Sie auf **Verbinden**, um die Liste der Servertypen anzuzeigen, und wählen Sie dann **Reporting Services** aus.

3. Geben Sie im Dialogfeld **Verbindung mit Server herstellen** eine URL zu einer SharePoint-Website ein. Das folgende Beispiel veranschaulicht die Syntax: `https://<web server>/sites/<site>`.

4. Wählen Sie den **Authentifizierungstyp** aus. Wenn Sie die Windows-Authentifizierung verwenden, müssen Sie die Verbindung mit Ihren Anmeldeinformationen herstellen. Wenn Sie die Standardauthentifizierung oder die Formularauthentifizierung auswählen, geben Sie das Konto und das Kennwort ein.

5. Wählen Sie **Verbinden**. Der Berichtsserver wird im Objekt-Explorer angezeigt.

6. Klicken Sie mit der rechten Maustaste auf den Serverknoten, um Systemeigenschaften und Standardeinstellungen für den Server festzulegen. Weitere Informationen finden Sie unter [Festlegen von Berichtsservereigenschaften (Management Studio)](../../reporting-services/tools/set-report-server-properties-management-studio.md).

### <a name="to-register-a-report-server"></a>So registrieren Sie einen Berichtsserver

1. Wenn Sie keine Verbindung zu einem Berichtsserver herstellen können, verfügen Sie nicht über die Berechtigungen für den Zugriff, oder der Server ist noch nicht registriert. Klicken Sie auf **Ansicht** > **Registrierte Server**, um den Server zu registrieren.

2. Klicken Sie auf das Symbol für **Reporting Services**.

3. Klicken Sie mit der rechten Maustaste auf **Reporting Services** > **Neu** > **Serverregistrierung**. Das Dialogfeld **Neue Serverregistrierung** wird angezeigt.

4. Geben Sie für **Servername**einen Wert ein. Geben Sie den Wert je nach Servermodus an:

    - Geben Sie für einen Berichtsserver im einheitlichen Modus den Namen der Berichtsserverinstanz ein. Die Namen von Berichtsserverinstanzen basieren auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanznamen. Standardmäßig ist der Instanzname eines lokalen Berichtsservers der Computername. Wenn Sie den Berichtsserver als benannte Instanz installiert haben, müssen Sie den Server mit der folgenden Syntax angeben: *\<Servername>[\\<Instanzname\>]* .

    - Bei einem Server, der im integrierten SharePoint-Modus ausgeführt wird, müssen Sie eine Verbindung mit der SharePoint-Website herstellen, mit der der Berichtsserver verbunden ist. Stellen Sie eine Verbindung mit der SharePoint-Website her, damit Sie die Berechtigungsstufen überprüfen können. Über die Berechtigungen wird der Zugriff auf die Berichtsserverinhalte und -vorgänge gesteuert. Sie können eine beliebige Site in der Siteauflistung angeben. Das folgende Beispiel veranschaulicht die Syntax: `https://mysharepointsite`.

5. Wählen Sie unter **Authentifizierung** den Authentifizierungsmodus aus, der bereits vom Berichtsserver verwendet wird.

   - Wenn Sie die Standardsicherheitseinstellungen verwenden, wählen Sie **Windows-Authentifizierung** aus.
   - Wenn eine benutzerdefinierte Sicherheitserweiterung installiert und bereitgestellt wurde, wählen Sie **Formularauthentifizierung**aus.
   - Wenn Sie den Berichtsserver für die Standardauthentifizierung konfiguriert haben, wählen Sie **Standardauthentifizierung**.
   - Wenn der Berichtsserver für den integrierten SharePoint-Modus konfiguriert ist, wählen Sie **Windows-Authentifizierung**.

6. Klicken Sie auf **Testen**, um die Verbindung zu überprüfen.

7. Klicken Sie in der Aufforderung auf **OK** und dann auf **Speichern**.

## <a name="connection-syntax-and-permissions"></a>Verbindungssyntax und Berechtigungen

 In der folgenden Tabelle werden die Verbindungssyntax, Schritte und Berechtigungen zusammengefasst, die zum Ausführen bestimmter Aufgaben erforderlich sind.

 Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] als Servertyp im Dialogfeld **Verbindung mit Server herstellen** angeben, können Sie einen Berichtsservernamen oder einen Endpunkt zum Webdienst festlegen.

|Verbinden mit|   Aufgaben   |   Berechtigungen   |
|----------|-----------|-----------------|  
|Berichtsserver im einheitlichen Modus, die als Standardinstanz oder benannte Instanz verbunden sind:<br /><br /> \<servername>\<_instanz><br /><br /> Die Verbindung zum Berichtsserver wird durch den Berichtsserver-WMI-Anbieter hergestellt.|Servereigenschaften und -standardeinstellungen anzeigen und festlegen.<br /><br /> Aufträge anzeigen und abbrechen.<br /><br /> Gemeinsame Zeitpläne erstellen und verwalten.<br /><br /> Rollendefinitionen erstellen, ändern oder löschen.|Der Systemadministratorrolle zugewiesen.|  
|Berichtsserver im einheitlichen Modus, die als Standardinstanz oder benannte Instanz über den Endpunkt zum Report Server-Webdienst verbunden sind:<br /><br /> `https://<servername>/reportserver`<br /><br /> Das Angeben einer URL zum Berichtsserver ist eine alternative Möglichkeit, eine Verbindung mit dem Berichtsserver herzustellen.|Servereigenschaften und -standardeinstellungen anzeigen und festlegen.<br /><br /> Aufträge anzeigen und abbrechen.<br /><br /> Gemeinsame Zeitpläne erstellen und verwalten.<br /><br /> Rollendefinitionen erstellen, ändern oder löschen.|Der Systemadministratorrolle zugewiesen.|  
|Berichtsserver im integrierten SharePoint-Modus, konfiguriert über die SharePoint-Website:<br /><br /> `https://<webserver>/<SharePointSite>`|Servereigenschaften und -standardeinstellungen anzeigen und festlegen.<br /><br /> Aufträge anzeigen und abbrechen.<br /><br /> Erstellen und Verwalten gemeinsamer Zeitpläne, die für die verbundene Website definiert sind<br /><br /> Anzeigen der Berechtigungsstufen für die verbundene Website|Vollzugriffsebene der Berechtigung für die verbundene SharePoint-Website|
|Berichtsserver im integrierten SharePoint-Modus, verbunden über den Namen der Berichtsserverinstanz:<br /><br /> \<servername>\<_instanz>|Servereigenschaften und -standardeinstellungen anzeigen und festlegen.<br /><br /> Aufträge anzeigen und abbrechen.|Berechtigungs-Vollzugriffsebene für die SharePoint-Website, die in den Berichtsserver integriert ist.<br /><br /> Beachten Sie, dass bei der Verbindung mit dem Berichtsserver statt mit der SharePoint-Website die Anzahl der durchführbaren Aufgaben reduziert ist. Dies ist darauf zurückzuführen, dass der Berichtsserver nur Anwendungsdaten zurückgeben kann, die in der Berichtsserver-Datenbank gespeichert oder verwaltet werden, jedoch nicht die Anwendungsdaten in den SharePoint-Konfigurations- und -Inhaltsdatenbanken.|

## <a name="see-also"></a>Weitere Informationen

 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 [Reporting Services in SQL Server Management Studio (SSRS)](../../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)
