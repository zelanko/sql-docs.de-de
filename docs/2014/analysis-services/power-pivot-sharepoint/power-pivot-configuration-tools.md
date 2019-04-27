---
title: PowerPivot-Konfigurationstools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: f934c51d-01fe-4e67-971d-cd87d7d7ee51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 133f5db597dfd56464678c52273e576e3493f172
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62749616"
---
# <a name="powerpivot-configuration-tools"></a>PowerPivot Configuration Tools
  Sie verwenden die PowerPivot-Konfigurationstools zum Konfigurieren, Reparieren oder Entfernen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .  
  
 Der Setup-Assistent für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installiert das [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Konfigurationstool für SharePoint 2010 sowie ein [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Konfigurationstool für SharePoint 2013. In diesem Thema wird auf die allgemeine Verwendung der beiden Tools und die Unterschiede eingegangen.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010  
  
 **In diesem Thema:**  
  
-   [Anforderungen für die Verwendung der Konfigurationstools](#bkmk_requirements)  
  
-   [Zwei Versionen des Konfigurationstools](#bkmk_twoversions)  
  
-   [Übersicht über die Verwendung eines PowerPivot-Konfigurationstools](#bkmk_overview)  
  
-   [Starten eines der PowerPivot-Konfigurationstools](#bmkm_start_tool)  
  
##  <a name="bkmk_requirements"></a> Anforderungen für die Verwendung der Konfigurationstools  
  
-   Sie müssen ein Farmadministrator sein.  
  
-   Sie müssen Serveradministrator für die Analysis Services-Instanz sein (nur SharePoint 2010).  
  
-   Sie müssen Db_owner für die Konfigurationsdatenbank der Farm sein.  
  
-   Für die Verwendung der Konfigurationstools bestehen keine TCP/IP-Portanforderungen. Deshalb besteht keine Notwendigkeit, die Firewall in Anpassung an die Konfigurationstools zu konfigurieren. Vom Konfigurationstool wird vorausgesetzt, dass die Webanwendungen und freigegebenen Dienste als Teil der SharePoint-Plattform verfügbar sind. Möglicherweise müssen Sie die Firewall für den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server konfigurieren. Weitere Informationen finden Sie unter [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
##  <a name="bkmk_twoversions"></a> Zwei Versionen des Konfigurationstools  
 Der Setup-Assistent für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installiert das PowerPivot-Konfigurationstool für SharePoint 2010 sowie ein PowerPivot-Konfigurationstool für SharePoint 2013.  
  
 Die Tools können nur mit einer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Instanz oder [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] -Instanz von [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]verwendet werden. Verwenden Sie sie nicht mit [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Installationen.  
  
|Name|Unterstützte SharePoint-Versionen|Konfigurationsdetails|  
|----------|-------------------------------------|----------------------------|  
|Konfiguration von PowerPivot für SharePoint 2013|SharePoint 2013|[Konfigurieren oder Reparieren von PowerPivot für SharePoint 2013 &#40;PowerPivot-Konfigurationstool&#41;](configure-or-repair-power-pivot-for-sharepoint-2013.md)|  
|PowerPivot-Konfigurationstool|SharePoint 2010 mit SharePoint 2010|[Konfigurieren oder Reparieren von PowerPivot für SharePoint 2010 &#40;PowerPivot-Konfigurationstool&#41;](../configure-repair-powerpivot-sharepoint-2010.md)|  
  
###  <a name="bkmk_sum_differences_betweentools"></a> Unterschiede zwischen den beiden Konfigurationstools  
 Die beiden Versionen des Konfigurationstools sind ähnlich, unterscheiden sich jedoch hinsichtlich der ausgeführten Konfigurationsschritte. Die Unterschiede resultieren aus den Änderungen zwischen SharePoint 2010 und SharePoint 2013 sowie den Architekturunterschieden zwischen der SQL Server 2012 SP1-Version von PowerPivot für SharePoint und den Vorgängerversionen von PowerPivot für SharePoint.  
  
 In der folgenden Tabelle sind die neuen und geänderten Funktionen im Tool für die **PowerPivot für SharePoint 2013-Konfiguration** beschrieben. Außerdem sind in der Tabelle die Funktionen des **PowerPivot-Konfigurationstools** beschrieben, die nicht im PowerPivot für SharePoint 2013-Konfigurationstool enthalten sind. Die Zeilen in der Tabelle weisen die gleiche Reihenfolge auf wie die Registerkarten in den Konfigurationstools.  
  
|Konfiguration von PowerPivot für SharePoint 2013|PowerPivot-Konfigurationstool|  
|--------------------------------------------------|-----------------------------------|  
|Die Hauptseite verfügt über eine neue Option für **PowerPivot-Server für Excel Services**. Die Option unterstützt die neue Architektur, in der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] außerhalb der SharePoint-Farm ausgeführt wird. Sie konfigurieren Excel Services für die Verwendung eines oder mehrerer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server, die im SharePoint-Modus ausgeführt werden.<br /><br /> ![PowerPivot-Server im neuen Konfigurationstool](../media/as-powerpivot-configtool-differences-new-mainpage.gif "PowerPivot-Server im neuen Konfigurationstool")||  
||Das Tool für die Version 2010 enthält die Seite **SQL Server Analysis Services (PowerPivot) auf dem lokalen Server registrieren** , um eine lokale Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]zu konfigurieren. Diese Seite ist im Tool für die Version 2013 nicht enthalten, da keine lokale Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]vorhanden ist.<br /><br /> ![ALS Dienstkonto im alten Konfigurationstool](../media/as-powerpivot-configtool-differences-old-register-as-localserver.gif "als Dienstkonto im alten Konfigurationstool")|  
||Die Seite **PowerPivot-Dienstanwendung erstellen** verfügt über die zusätzliche Option **Arbeitsmappen aktualisieren, um die Datenaktualisierung zuzulassen**. Diese Option steht im Tool für die Version 2013 nicht zur Verfügung.<br /><br /> ![Aktualisieren von Arbeitsmappen im alten Konfigurationstool](../media/as-powerpivot-configtool-differences-old-uprgadeworkbooks.gif "Aktualisieren von Arbeitsmappen im alten Konfigurationstool")|  
|Das Tool für die Version 2013 verfügt über die neue Seite **PowerPivot-Server konfigurieren**. Diese Seite unterstützt die neue Architektur von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , die außerhalb der SharePoint-Farm ausgeführt wird. Der Servername, der auf der Hauptseite im Textfeld **PowerPivot-Server für Excel Services**eingegeben wurde, wird standardmäßig auch unter **PowerPivot-Server konfigurieren**aufgeführt.<br /><br /> ![Registrieren von neuen Konfigurationstool für PowerPivot-Servern](../media/as-powerpivot-configtool-differences-new-powerpivot-servers.gif "registrieren PowerPivot-Server neue-Konfigurationstool")||  
|Das Tool für die Version 2013 verfügt die neue Seite **PowerPivot-Add-In als Tracker für die Verwendung von Excel Services registrieren**. Die PowerPivot-Verwendungsdaten werden von SharePoint 2010 Excel Services nicht nachverfolgt.||  
||Das Tool für die Version 2010 enthält die Seite **MSOLAP.5 als vertrauenswürdigen Anbieter hinzufügen** , um MSOLAP zu registrieren, damit PowerPivot-Modelle von Excel Services in SharePoint 2010 geladen werden können. Diese Seite ist im Tool für die Version 2013 nicht enthalten. SharePoint 2013 Excel Services verwendet nicht den MSOLAP-Anbieter, um Modelle zu laden.|  
  
##  <a name="bkmk_overview"></a> Übersicht über die Verwendung eines PowerPivot-Konfigurationstools  
 Wenn Sie eines der PowerPivot-Konfigurationstools starten, wertet das Tool eine vorhandene Installation aus, um zu ermitteln, welche Vorgänge anwendbar sind. Bei einer neuen Installation ist nur der Konfigurationstask verfügbar. Nach der Serverkonfiguration wird der Task zum Entfernen angezeigt. Wenn Sie mit einer [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Instanz begonnen haben, wird das Upgrade auch in der Liste der verfügbaren Tasks aktiviert.  
  
 Wenn Sie mit der Zentraladministration oder Windows PowerShell nicht vertraut sind, können Sie alternativ das Konfigurationstool ausführen, um eine [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Installation vorzunehmen.  
  
 Darüber hinaus kann das Tool erkennen, ob die Farm konfiguriert ist oder ob erforderliche Funktionen fehlen. Wenn die SharePoint-Programmdateien installiert sind, aber die Farm nicht konfiguriert ist, stellt das Tool Aktionen zum Konfigurieren der Farm sowie der [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Installation bereit.  
  
 Sie können die Registerkarte **Skript** überprüfen, um zu erfahren und zu verstehen, wie PowerPivot und SharePoint mithilfe von Windows PowerShell konfiguriert werden. Weitere Informationen finden Sie unter den folgenden Links:  
  
-   [PowerPivot-Konfiguration mit Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
-   [PowerShell-Referenz für PowerPivot für SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
> [!NOTE]
>  Das Tool konfiguriert nicht Reporting Services. Wenn Sie der SharePoint-Umgebung Reporting Services hinzufügen, müssen Sie Reporting Services separat installieren und konfigurieren. Weitere Informationen finden Sie unter den folgenden Links:  
> 
>  -   [Installieren von Reporting Services SharePoint Mode for SharePoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).  
> -   [Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
##  <a name="bmkm_start_tool"></a> Starten eines der PowerPivot-Konfigurationstools  
  
1.  Auf der **starten** Startbildschirm `powerpivot`  
  
     Auf der **starten** geben `powerpivot` oder auf die **starten** Menü klicken Sie auf **Programme**, klicken Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], klicken Sie auf **-Konfigurationstools** , und klicken Sie dann auf einen der folgenden:  
  
    -   **PowerPivot-Konfigurationstool**  
  
    -   **OR**  
  
    -   **Konfiguration von PowerPivot für SharePoint 2013**  
  
     ![zwei powerpivot-konfigurationstools](../media/as-powerpivot-configtools-bothicons.gif "two powerpivot configuration tools")  
  
     **Hinweis**: Die Tools sind nur verfügbar, wenn [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] auf dem lokalen Server installiert ist.  
  
2.  Beim Start überprüfen die Konfigurationstools den Status der Installation und stellen Aufgaben bereit, die für die jeweilige Installation gelten.  
  
3.  Abhängig vom aktuellen Status der Installation können eine oder mehrere der folgenden Aufgaben ausgeführt werden:  
  
    1.  Klicken Sie auf **PowerPivot für SharePoint konfigurieren oder reparieren** , um Tasks zur Installationsnachbereitung abzuschließen oder eine Installation zu reparieren.  
  
    2.  Klicken Sie auf **Funktionen, Dienste, Anwendungen und Lösungen entfernen** , um Funktionen und Lösungen von der Farm zu entfernen.  
  
    3.  Klicken Sie auf **Funktionen, Dienste, Anwendungen und Lösungen aktualisieren** , um Funktionen und Lösungen zu aktualisieren, die mit einer früheren Version von [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]installiert wurden.  
  
     In der Abbildung ist beispielsweise die Startseite des PowerPivot für SharePoint 2013-Konfigurationstools dargestellt.  
  
     ![PowerPivot für SharePoint 2013-Konfigurationstool](../media/ssas-powerpivot-configtool-4-sharepoint2013-choosemode.gif "PowerPivot für SharePoint 2013-Konfigurationstool")  
  
 Jeder Task besteht aus einzelnen Aktionen, die verschiedene Aspekte der Serverkonfiguration behandeln. Die Konfigurationsaufgabe schließt z. B. Aktionen zum Bereitstellen von Lösungen, Erstellen einer PowerPivot-Dienstanwendung, Aktivieren von Funktionen und Konfigurieren der Datenaktualisierung ein. Die Liste der Aktionen variiert je nach dem aktuellen Status der Installation. Wenn eine Aktion nicht benötigt wird, wird sie vom Tool aus der Taskliste ausgeschlossen.  
  
 Wenn Sie auf Ausführen klicken, verarbeitet das Tool alle Aktionen im Batchmodus. Obwohl jede Aktion in der Aufgabenliste als separates Element angezeigt wird, werden alle im Task enthaltenen Aktionen zusammen verarbeitet. Nur Aktionen, die ein positives Überprüfungsergebnis aufweisen, werden verarbeitet. Sie müssen einige der Eingabewerte möglicherweise hinzufügen oder ändern, damit ein positives Überprüfungsergebnis erzielt wird.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Upgrade PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) : Beschreibt, wie eine vorhandene Installation aktualisiert wird, die sich bereits in einer Farm befindet.  
  
 [Uninstall PowerPivot for SharePoint](../../sql-server/install/uninstall-power-pivot-for-sharepoint.md) : Beschreibt, wie PowerPivot für SharePoint-Dienste, -Lösungen und -Anwendungsseiten aus einer Farm entfernt werden.  
  
 [PowerPivot-Konfiguration mit Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
 [PowerPivot-Serververwaltung und -konfiguration in der Zentraladministration](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
