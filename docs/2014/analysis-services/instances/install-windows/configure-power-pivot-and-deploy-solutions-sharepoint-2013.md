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
ms.openlocfilehash: e26faf2ef80f416858665893e14e405eab7254d6
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543902"
---
# <a name="configure-powerpivot-and-deploy-solutions-sharepoint-2013"></a>Konfigurieren von PowerPivot und Bereitstellen von Lösungen (SharePoint 2013)
  In diesen Themen wird beschrieben, wie Erweiterungen der mittleren Ebene für die PowerPivot-Funktionen in [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] bereitgestellt und konfiguriert werden, z. B. PowerPivot-Katalog, planmäßige Datenaktualisierung, Management-Dashboard und Datenanbieter. Führen Sie das **PowerPivot für SharePoint 2013-Konfigurationstool** aus, um folgende Aufgaben auszuführen:  
  
-   Bereitstellen von SharePoint-Lösungsdateien  
  
-   Erstellen einer PowerPivot-Dienstanwendung  
  
-   Konfigurieren einer Excel Services-Anwendung für die Verwendung eines [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Servers im SharePoint-Modus Informationen zu Back-End-Diensten und zum Installieren eines- [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Servers im SharePoint-Modus finden Sie unter [PowerPivot für SharePoint 2013-Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).  
  
 Informationen zum Installieren des PowerPivot für SharePoint 2013-Konfigurationstools finden [Sie unter Installieren oder Deinstallieren des PowerPivot für SharePoint-Add-ins &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Ausführen der Konfiguration von PowerPivot für SharePoint 2013](#bkmk_run_configuration_tool)  
  
 [Überprüfen der PowerPivot-Konfiguration](#bkmk_verify_powerpivot)  
  
 [Beheben von Problemen](#bkmk_troubleshoot_issues)  
  
##  <a name="run-powerpivot-for-sharepoint-2013-configuration"></a><a name="bkmk_run_configuration_tool"></a>PowerPivot für SharePoint 2013-Konfiguration ausführen  
 **Hinweis:** Vom Setup-Assistenten für [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] werden zwei unterschiedliche Konfigurationstools für [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)]installiert. Jedes Tool unterstützt eine andere SharePoint-Version.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|Konfiguration von PowerPivot für SharePoint 2013|SharePoint 2013|  
|PowerPivot-Konfigurationstool|SharePoint 2010 mit SharePoint 2010 Service Pack 1 (SP1)|  
  
 **Hinweis:** Die folgenden Schritte können nur von einem Farmadministrator ausgeführt werden. Angenommen, eine Fehlermeldung mit etwa folgendem Wortlaut wird ausgegeben:  
  
-   "Der Benutzer ist kein Farm Administrator. Beheben Sie die Überprüfungsfehler, und wiederholen Sie den Vorgang."  
  
 Melden Sie sich entweder mit dem Konto an, unter dem SharePoint installiert wurde, oder konfigurieren Sie das Setupkonto als primären Administrator der Website für die SharePoint-Zentraladministration.  
  
1.  Klicken Sie im Menü **Start** auf **Alle Programme**, und klicken Sie dann auf [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **Konfigurationstools**und auf **Konfiguration von PowerPivot für SharePoint 2013**. Das Tool wird nur aufgeführt, wenn PowerPivot für SharePoint auf dem lokalen Server installiert ist.  
  
2.  Klicken Sie auf **PowerPivot für SharePoint konfigurieren oder reparieren** , und klicken Sie dann auf **OK**.  
  
3.  Mithilfe des Tools wird der aktuelle Status von PowerPivot überprüft und ermittelt, welche Schritte zum Abschließen der Konfiguration erforderlich sind. Erweitern Sie das Fenster auf Vollbildgröße. Am unteren Rand des Fensters wird eine Schaltflächenleiste angezeigt, die die Befehle **Überprüfen**, **Ausführen**und **Beenden** enthält.  
  
4.  Registerkarte **Parameter** :  
  
    1.  **Benutzername für Standardkonto**: Geben Sie ein Domänenbenutzerkonto für das Standardkonto ein. Dieses Konto wird verwendet, um Dienste bereitzustellen, einschließlich des PowerPivot-Dienstanwendungspools. Geben Sie kein integriertes Konto wie Network Service oder Local System an. Das Tool blockiert Konfigurationen, bei denen integrierte Konten angegeben werden.  
  
    2.  **Datenbankserver**: Sie können die für die SharePoint-Farm unterstützte SQL Server-Datenbank-Engine verwenden.  
  
    3.  **Passphrase**. Geben Sie eine Passphrase ein. Wenn Sie eine neue SharePoint-Farm erstellen, wird die Passphrase immer dann verwendet, wenn Sie der SharePoint-Farm einen Server oder eine Anwendung hinzufügen. Wenn die Farm bereits vorhanden ist, geben Sie die Passphrase ein, die Ihnen ermöglicht, der Farm eine Serveranwendung hinzuzufügen.  
  
    4.  **PowerPivot-Server für Excel Services**: Geben Sie den Namen eines [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Servers im SharePoint-Modus ein. Bei einer Bereitstellung auf einem einzelnen Server entspricht dieser dem Datenbankserver. `[ServerName]\powerpivot`  
  
    5.  Klicken Sie im linken Fenster auf **Websitesammlung erstellen** . Notieren Sie sich die **Website-URL** , damit Sie sie später zur Hand haben. Wenn der SharePoint-Server noch nicht konfiguriert ist, verwendet der Konfigurations-Assistent für die URL der Webanwendung und Websitesammlung standardmäßig den Stamm von `http://[ServerName]`. Um die Standardeinstellungen zu ändern, überprüfen Sie die folgenden Seiten im linken Fenster: **Standardwebanwendung erstellen** und **Webanwendungslösung bereitstellen**  
  
5.  Überprüfen Sie optional die verbleibenden Eingabewerte, die zum Abschließen der jeweiligen Aktion verwendet werden. Klicken Sie im linken Fenster auf die einzelnen Aktionen, um die Details zur Aktion anzuzeigen und zu überprüfen. Weitere Informationen zu den einzelnen Informationen finden Sie im Abschnitt "Eingabewerte, die zum Konfigurieren des Servers in [konfigurieren oder reparieren PowerPivot für SharePoint 2010 &#40;Power Pivot-Konfigurationstools&#41;](../../configure-repair-powerpivot-sharepoint-2010.md) in diesem Thema verwendet werden.  
  
6.  Entfernen Sie optional alle Aktionen, die Sie zu dieser Zeit nicht verarbeiten wollen. Wenn Sie z. B. Secure Store Service später konfigurieren möchten, klicken Sie auf **Secure Store Service konfigurieren**, und deaktivieren Sie dann das Kontrollkästchen **Diese Aktion in Taskliste einschließen**.  
  
7.  Klicken Sie auf **Überprüfen** , um zu überprüfen, ob das Tool genügend Informationen hat, um die Aktionen in der Liste zu verarbeiten. Wenn Überprüfungsfehler auftreten, klicken Sie auf die Warnungen im linken Bereich, um Details zum Überprüfungsfehler anzuzeigen. Korrigieren Sie alle Überprüfungsfehler, und klicken Sie dann erneut auf **Überprüfen** .  
  
8.  Klicken Sie auf **Ausführen** , um alle Aktionen in der Aufgabenliste zu verarbeiten. Beachten Sie, dass **Ausführen** verfügbar wird, nachdem Sie die Aktionen überprüft haben. Wenn **Ausführen** nicht aktiviert ist, klicken Sie zuerst auf **Überprüfen** .  
  
 Weitere Informationen finden Sie unter [konfigurieren oder reparieren PowerPivot für SharePoint 2010 &#40;Power Pivot-Konfigurationstools&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)  
  
##  <a name="verify-powerpivot-configuration"></a><a name="bkmk_verify_powerpivot"></a>Überprüfen der Power Pivot-Konfiguration  
 **Dienste:**  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Dienste auf dem Server verwalten**.  
  
2.  Überprüfen Sie, ob **SQL Server Analysis Services** und **SQL Server PowerPivot System Service** gestartet wurden.  
  
 **Farmfunktion:**  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Farmfunktionen verwalten**.  
  
2.  Überprüfen Sie, ob **Funktion zur PowerPivot-Integration** auf **Aktiv**festgelegt ist.  
  
 **Websitesammlungsfunktion:**  
  
1.  Navigieren Sie zu der vom Konfigurationstool erstellten Website-URL.  
  
     Klicken Sie auf **Einstellungen**![SharePoint-Einstellungen](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint-Einstellungen")und dann auf **Website Einstellungen**.  
  
     Klicken Sie auf **Websitesammlungs-Features**.  
  
2.  Stellen Sie sicher, dass **Funktion zur PowerPivot-Integration für Websitesammlungen** auf **Aktiv**festgelegt ist.  
  
 **Power Pivot-Dienst Anwendung:**  
  
1.  Klicken Sie in der Zentraladministration unter **Anwendungsverwaltung**auf **Dienstanwendungen verwalten**.  
  
2.  Vergewissern Sie sich, dass der Status der Dienstanwendung **Gestartet**lautet. Der Standardname lautet **Power Pivot-Standard Dienst Anwendung**.  
  
     Klicken Sie auf den Namen der Dienstanwendung, um das PowerPivot-Management-Dashboard für die Dienstanwendung zu öffnen. Bei seiner ersten Verwendung dauert das Laden des Dashboards einige Minuten.  
  
 Weitere Informationen finden Sie unter [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).  
  
##  <a name="troubleshoot-issues"></a><a name="bkmk_troubleshoot_issues"></a>Beheben von Problemen  
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
  
 Weitere Informationen zu Problemen beim Durchsuchen der Datenaktualisierung finden Sie unter Problembehandlung bei der [Power Pivot-Datenaktualisierung](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) ( https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) .  
  
 Weitere Informationen zum Konfigurationstool finden Sie unter [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).  
  
  
