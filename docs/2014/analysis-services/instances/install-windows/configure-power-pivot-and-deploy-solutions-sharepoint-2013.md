---
title: Konfigurieren von Power Pivot und Bereitstellen von Lösungen (SharePoint 2013) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6401fd92-f43b-450e-8298-12db644c25bc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d835269f77e563b94c89c3a68c5c82844edc773
ms.sourcegitcommit: 1c3f56deaa4c1ffbe5d7f75752ebe10447c3e7af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "69493968"
---
# <a name="configure-powerpivot-and-deploy-solutions-sharepoint-2013"></a>Konfigurieren von PowerPivot und Bereitstellen von Lösungen (SharePoint 2013)
  In diesen Themen wird beschrieben, wie Erweiterungen der mittleren Ebene für die PowerPivot-Funktionen in [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] bereitgestellt und konfiguriert werden, z. B. PowerPivot-Katalog, planmäßige Datenaktualisierung, Management-Dashboard und Datenanbieter. Führen Sie das **PowerPivot für SharePoint 2013-Konfigurationstool** aus, um folgende Aufgaben auszuführen:  
  
-   Bereitstellen von SharePoint-Lösungsdateien  
  
-   Erstellen einer PowerPivot-Dienstanwendung  
  
-   Konfigurieren einer Excel Services-Anwendung für die Verwendung eines [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Servers im SharePoint-Modus Informationen zu Back-End-Diensten und [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] zum Installieren eines-Servers im SharePoint-Modus finden Sie unter [PowerPivot für SharePoint 2013-Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).  
  
 Informationen zum Installieren des PowerPivot für SharePoint 2013-Konfigurationstools finden [Sie unter Installieren oder Deinstallieren des PowerPivot für SharePoint Add &#40;-in Share&#41; Point 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) .  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [PowerPivot für SharePoint 2013-Konfiguration ausführen](#bkmk_run_configuration_tool)  
  
 [Überprüfen der Power Pivot-Konfiguration](#bkmk_verify_powerpivot)  
  
 [Problembehandlung](#bkmk_troubleshoot_issues)  
  
##  <a name="bkmk_run_configuration_tool"></a>PowerPivot für SharePoint 2013-Konfiguration ausführen  
 **Hinweis**: Der [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Setup-Assistent installiert zwei verschiedene Konfigurationstools [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)]für. Jedes Tool unterstützt eine andere SharePoint-Version.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|PowerPivot für SharePoint 2013-Konfigurationstool|SharePoint 2013|  
|PowerPivot-Konfigurationstool|SharePoint 2010 mit SharePoint 2010 Service Pack 1 (SP1)|  
  
 **Hinweis**: Sie müssen ein Farm Administrator sein, um die folgenden Schritte ausführen zu können. Angenommen, eine Fehlermeldung mit etwa folgendem Wortlaut wird ausgegeben:  
  
-   "Der Benutzer ist kein Farm Administrator. Beheben Sie die Überprüfungsfehler, und wiederholen Sie den Vorgang."  
  
 Melden Sie sich entweder mit dem Konto an, unter dem SharePoint installiert wurde, oder konfigurieren Sie das Setupkonto als primären Administrator der Website für die SharePoint-Zentraladministration.  
  
1.  Klicken Sie im Menü **Start** auf **Alle Programme**, und klicken Sie dann auf [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **Konfigurationstools**und auf **Konfiguration von PowerPivot für SharePoint 2013**. Das Tool wird nur aufgeführt, wenn PowerPivot für SharePoint auf dem lokalen Server installiert ist.  
  
2.  Klicken Sie auf **PowerPivot für SharePoint konfigurieren oder reparieren** , und klicken Sie dann auf **OK**.  
  
3.  Mithilfe des Tools wird der aktuelle Status von PowerPivot überprüft und ermittelt, welche Schritte zum Abschließen der Konfiguration erforderlich sind. Erweitern Sie das Fenster auf Vollbildgröße. Am unteren Rand des Fensters wird eine Schaltflächenleiste angezeigt, die die Befehle **Überprüfen**, **Ausführen**und **Beenden** enthält.  
  
4.  Registerkarte **Parameter** :  
  
    1.  **Benutzername für Standardkonto**: Geben Sie ein Domänen Benutzerkonto für das Standardkonto ein. Dieses Konto wird verwendet, um Dienste bereitzustellen, einschließlich des PowerPivot-Dienstanwendungspools. Geben Sie kein integriertes Konto wie Network Service oder Local System an. Das Tool blockiert Konfigurationen, bei denen integrierte Konten angegeben werden.  
  
    2.  **Daten Bank Server**: Sie können SQL Server Datenbank-Engine verwenden, das für die SharePoint-Farm unterstützt wird.  
  
    3.  **Passphrase**: Geben Sie eine Passphrase ein. Wenn Sie eine neue SharePoint-Farm erstellen, wird die Passphrase immer dann verwendet, wenn Sie der SharePoint-Farm einen Server oder eine Anwendung hinzufügen. Wenn die Farm bereits vorhanden ist, geben Sie die Passphrase ein, die Ihnen ermöglicht, der Farm eine Serveranwendung hinzuzufügen.  
  
    4.  **Power Pivot-Server für Excel Services**: Geben Sie den Namen eines [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Servers im SharePoint-Modus ein. Bei einer Bereitstellung auf einem einzelnen Server entspricht dieser dem Datenbankserver. `[ServerName]\powerpivot`  
  
    5.  Klicken Sie im linken Fenster auf **Websitesammlung erstellen** . Notieren Sie sich die **Website-URL** , damit Sie sie später zur Hand haben. Wenn der SharePoint-Server noch nicht konfiguriert ist, verwendet der Konfigurations-Assistent für die URL der Webanwendung und Websitesammlung standardmäßig den Stamm von `http://[ServerName]`. Überprüfen Sie die folgenden Seiten im linken Fenster, um die Standardwerte zu ändern: **Standardweb Anwendung erstellen** und **Webanwendungslösung** bereitstellen  
  
5.  Überprüfen Sie optional die verbleibenden Eingabewerte, die zum Abschließen der jeweiligen Aktion verwendet werden. Klicken Sie im linken Fenster auf die einzelnen Aktionen, um die Details zur Aktion anzuzeigen und zu überprüfen. Weitere Informationen zu den einzelnen Informationen finden Sie im Abschnitt "Eingabewerte, die zum Konfigurieren des Servers in [konfigurieren oder reparieren PowerPivot für SharePoint &#40;2010 Power Pivot-&#41; Konfigurationstools](../../configure-repair-powerpivot-sharepoint-2010.md) in diesem Thema verwendet werden.  
  
6.  Entfernen Sie optional alle Aktionen, die Sie zu dieser Zeit nicht verarbeiten wollen. Wenn Sie z. B. Secure Store Service später konfigurieren möchten, klicken Sie auf **Secure Store Service konfigurieren**, und deaktivieren Sie dann das Kontrollkästchen **Diese Aktion in Taskliste einschließen**.  
  
7.  Klicken Sie auf **Überprüfen** , um zu überprüfen, ob das Tool genügend Informationen hat, um die Aktionen in der Liste zu verarbeiten. Wenn Überprüfungsfehler auftreten, klicken Sie auf die Warnungen im linken Bereich, um Details zum Überprüfungsfehler anzuzeigen. Korrigieren Sie alle Überprüfungsfehler, und klicken Sie dann erneut auf **Überprüfen** .  
  
8.  Klicken Sie auf **Ausführen** , um alle Aktionen in der Aufgabenliste zu verarbeiten. Beachten Sie, dass **Ausführen** verfügbar wird, nachdem Sie die Aktionen überprüft haben. Wenn **Ausführen** nicht aktiviert ist, klicken Sie zuerst auf **Überprüfen** .  
  
 Weitere Informationen finden Sie unter [konfigurieren oder reparieren PowerPivot für SharePoint 2010 &#40;Power Pivot-Konfigurations&#41; Tools](../../configure-repair-powerpivot-sharepoint-2010.md)  
  
##  <a name="bkmk_verify_powerpivot"></a>Überprüfen der Power Pivot-Konfiguration  
 **Dienste:**  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Dienste auf dem Server verwalten**.  
  
2.  Überprüfen Sie, ob **SQL Server Analysis Services** und **SQL Server PowerPivot System Service** gestartet wurden.  
  
 **Farmfunktion:**  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Farmfunktionen verwalten**.  
  
2.  Überprüfen Sie, ob **Funktion zur PowerPivot-Integration** auf **Aktiv**festgelegt ist.  
  
 **Websitesammlungsfunktion:**  
  
1.  Navigieren Sie zu der vom Konfigurationstool erstellten Website-URL.  
  
     Klicken Sie auf **Einstellungen**![SharePoint]-Einstellungen(https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint-Einstellungen"), und klicken Sie dann auf **Website Einstellungen**.  
  
     Klicken Sie auf **Websitesammlungs-Features**.  
  
2.  Stellen Sie sicher, dass **Funktion zur PowerPivot-Integration für Websitesammlungen** auf **Aktiv**festgelegt ist.  
  
 **Power Pivot-Dienst Anwendung:**  
  
1.  Klicken Sie in der Zentraladministration unter **Anwendungsverwaltung**auf **Dienstanwendungen verwalten**.  
  
2.  Vergewissern Sie sich, dass der Status der Dienstanwendung **Gestartet**lautet. Der Standardname lautet **PowerPivot-Standarddienstanwendung**.  
  
     Klicken Sie auf den Namen der Dienstanwendung, um das PowerPivot-Management-Dashboard für die Dienstanwendung zu öffnen. Bei seiner ersten Verwendung dauert das Laden des Dashboards einige Minuten.  
  
 Weitere Informationen finden Sie unter [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).  
  
##  <a name="bkmk_troubleshoot_issues"></a> Problembehandlung  
 Um Unterstützung bei der Problembehandlung zu erhalten, empfiehlt es sich, die Diagnoseprotokollierung zu aktivieren.  
  
1.  Klicken Sie in der SharePoint-Zentraladministration auf **Überwachung** und dann auf **Verwendungs- und Integritätsdatenerfassung konfigurieren**.  
  
2.  Achten Sie darauf, dass **Verwendungsdatenerfassung aktivieren** ausgewählt ist.  
  
3.  Überprüfen Sie, ob die folgenden Ereignisse ausgewählt sind:  
  
    -   Definition der Verwendungsfelder für Schulungstelemetrie  
  
    -   PowerPivot-Verbindungen  
  
    -   Verwendung von PowerPivot-Datenladevorgängen  
  
    -   Verwendung von PowerPivot-Abfragen  
  
    -   Verwendung von PowerPivot-Datenentladevorgängen  
  
4.  Achten Sie darauf, dass **Integritätsdatenerfassung aktivieren** ausgewählt ist.  
  
5.  Klicken Sie auf **OK**.  
  
 Weitere Informationen zu Problemen beim Durchsuchen der Datenaktualisierung finden Sie unter Problembehandlung beihttps://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx)der [Power Pivot-Datenaktualisierung](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) (.  
  
 Weitere Informationen zum Konfigurationstool finden Sie unter [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).  
  
  
