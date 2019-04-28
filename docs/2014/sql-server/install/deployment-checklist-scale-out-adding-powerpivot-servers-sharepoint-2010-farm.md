---
title: 'Bereitstellungsprüfliste: Horizontale Skalierung durch Hinzufügen von PowerPivot-Server zu einer SharePoint 2010-Farm | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 2dbddcc7-427a-4537-a8e2-56d99b9d967d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7bef5104038dad251927c6afff613f248f4a6a47
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63025701"
---
# <a name="deployment-checklist-scale-out-by-adding-powerpivot-servers-to-a-sharepoint-2010-farm"></a>Bereitstellungsprüfliste: Horizontale Skalierung durch Hinzufügen von PowerPivot-Server zu einer SharePoint 2010-farm
  Wenn Sie viele Anforderungen für die PowerPivot-Abfrageverarbeitung in einer SharePoint-Farm erwarten, können Sie eine zusätzliche PowerPivot for SharePoint-Instanz hinzufügen, um die Unterstützung zusätzlicher Abfrage- und Datenverarbeitung nahtlos zu ermöglichen.  
  
 Nachdem Sie eine neue Instanz installiert haben, verfügen Sie über zusätzliche Kapazitäten, PowerPivot-Daten abzufragen oder PowerPivot-Datenaktualisierungsaufträge zu verarbeiten. Optional haben Sie die Möglichkeit, jeden Server so zu konfigurieren, dass er einen bestimmten Anforderungstyp bearbeitet: Abfrage oder Datenaktualisierung.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 SharePoint Server 2010 ist installiert und wird konfiguriert.  
  
 SharePoint Server 2010 SP1 wird angewendet, und die Farm wird aktualisiert.  
  
 Die in der Farm vorhandene PowerPivot für SharePoint-Instanz ist [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (entweder eine Neuinstallation oder eine Aktualisierung von SQL Server 2008 R2).  
  
 Der Computer, auf dem Sie den neuen [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot für SharePoint-Server installieren, wird der Farm hinzugefügt. Der Computer und die anderen Server in der Farm müssen sich in derselben Domäne befinden.  
  
 Überprüfen Sie die folgenden weiteren Themen, um System- und Versionsanforderungen zu verstehen:  
  
-   [Leitfaden zum Verwenden von SQL Server BI-Features in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
> [!NOTE]  
>  In einer Multiserverfarm müssen alle PowerPivot für SharePoint-Instanzen dieselbe Version aufweisen. Wenn Sie Service Packs oder Updates auf andere PowerPivot-Server angewendet haben, die bereits in der Farm vorhanden sind, muss die neue, von Ihnen hinzugefügte Instanz auf dieselbe Version der bereits in der Farm vorhandenen Instanz aktualisiert werden. Die neue Instanz steht erst zur Verfügung, wenn die Updates vorgenommen worden sind.  
  
## <a name="steps"></a>Schritte  
 Verwenden Sie diese Prüfliste, um einer SharePoint-Farm zusätzliche PowerPivot-Server hinzuzufügen. Diese Anweisungen gehen davon aus, dass bereits ein PowerPivot für SharePoint-Server in der Farm vorhanden ist und dass Sie einen zweiten Server für die zusätzliche Datenverarbeitung hinzufügen möchten. Mit Ausnahme der Unterschiede in den Installationsanforderungen, in der Konfiguration nach der Installation und in der Überprüfung, sind die Schritte zum Bereitstellen einer Lösung für horizontales Skalieren identisch mit dem Hinzufügen eines einzelnen PowerPivot-Servers zu einer bereits vorhandenen Farm.  
  
|Schritt|Link|  
|----------|----------|  
|Bestimmen des Dienstkontos der Analysis Services-Instanz, die bereits in der Farm vorhanden ist|Jede zusätzlich installierte Instanz, muss unter dem gleichen Konto wie die erste Instanz ausgeführt werden. Verwenden Sie einen der beiden Ansätze, um das Dienstkonto zu bestimmen:<br /><br /> Klicken Sie in der Zentraladministration im Abschnitt Sicherheit auf **Konfigurieren von Dienstkonten**. Wählen Sie **Windows-Dienst - SQL Server Analysis Services**. Nachdem Sie den Dienst ausgewählt haben, wird der Dienstkontoname auf der Seite angezeigt.<br /><br /> Öffnen Sie auf einem Server, die bereits eine PowerPivot-Dienstinstallation die **Services** Konsolenanwendung in der Verwaltung. Doppelklicken Sie auf **SQL Server Analysis Services**. Klicken Sie auf die **anmelden** Registerkarte, um das Dienstkonto anzuzeigen.<br />**\*\* Wichtige \* \***  nur verwenden Sie Zentraladministration, um Dienstkonten zu ändern. Wenn Sie ein anderes Tool oder einen anderen Ansatz verwenden, werden die Berechtigungen nicht ordnungsgemäß in der Farm aktualisiert.|  
|Ausführen von Setup, um eine zweite Instanz von PowerPivot für SharePoint zu installieren|[Installieren von PowerPivot für SharePoint 2010](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)<br /><br /> Wählen Sie einen Anwendungsserver, der der Farm hinzugefügt wird, jedoch über keine vorhandene PowerPivot-Instanz auf dem Server verfügt.<br /><br /> Wenn Sie während des Setups aufgefordert werden, ein Dienstkonto anzugeben, geben Sie das Konto vom vorherigen Schritt ein. Alle Instanzen des Analysis Services-Diensts müssen unter dem gleichen Domänenkonto ausgeführt werden. Diese Anforderung aktiviert die Verwendung der verwalteten Konten-Funktion in SharePoint, mit der Sie das Kennwort für alle Dienstinstanzen des gleichen Typs an einer Stelle aktualisieren können.|  
|Konfigurieren der zweiten Instanz|Sie können beide Ansätze verwenden, die Instanz konfigurieren: [PowerPivot-Konfigurationstools](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md) oder [PowerPivot-Konfiguration, die mithilfe von Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)<br /><br /> Wenn Sie eine zweite Instanz konfigurieren, müssen Sie nur die lokalen Dienste bereitstellen. Alle anderen Konfigurationstasks (z. B. Dienstanwendungen erstellen oder Datenaktualisierung konfigurieren) werden während der Erstkonfiguration ausgeführt und durch nachfolgende, von Ihnen installierte Instanzen verwendet.|  
|Installationsnachbereitung|Keine weiteren Schritte sind ausdrücklich erforderlich. Sie müssen keine Dienstanwendungen erstellen, Funktionen aktivieren, Lösungen bereitstellen oder die Identität von Dienstanwendungen ändern. Vorhandene Webanwendungen und Dienstanwendungen ermitteln und verwenden die neue Serversoftware automatisch.<br /><br /> Wenn Sie optional einen zweiten Server installieren, damit Abfragen und Datenaktualisierungen von verschiedenen Servern vorgenommen werden, können Sie jetzt Serverinstanzeigenschaften konfigurieren, um die Art der Anforderungen festzulegen, die von jedem Server bearbeitet werden. Weitere Informationen finden Sie unter [dedizierten Datenaktualisierung konfigurieren oder Verarbeitung Query-Only &#40;PowerPivot für SharePoint&#41;](../../analysis-services/configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md).|  
|Überprüfen der Installation der zweiten Instanz|Anhand der folgenden Schritte können Sie die PowerPivot-Abfrageverarbeitungen auf dem soeben installierten Server überprüfen.<br /><br /> (1) öffnen Sie die Dienste verwalten, auf der Serverseite zu bestätigen, dass der Server und seine Dienste angezeigt werden, in der zentralen Verwaltung.<br />-In-Server klicken Sie auf den Pfeil nach unten, klicken Sie auf Server ändern, und wählen Sie dann auf den Server mit dem neuen PowerPivot für SharePoint-Installation.<br />-Stellen Sie sicher, dass SQL Server Analysis Services und SQL Server PowerPivot-Systemdienst gestartet wurden.<br /><br /> 2) beenden Sie in der Zentraladministration andere PowerPivot für SharePoint-Server, damit der soeben installierte Server der einzige verfügbare ist. Weitere Informationen finden Sie unter [starten oder Beenden eines PowerPivot für SharePoint-Server](../../analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server.md).<br /><br /> (3) klicken Sie auf eine PowerPivot-Arbeitsmappe, um sie aus der Bibliothek zu öffnen.<br /><br /> (4) klicken Sie auf einen Slicer oder Pivotieren Sie die Daten, um eine Abfrage einzuleiten. Der Server lädt PowerPivot-Daten im Hintergrund. Im nächsten Schritt stellen Sie eine Verbindung mit dem Server her, um zu überprüfen, ob die Daten geladen und zwischengespeichert wurden.<br /><br /> (5) starten Sie SQL Server Management Studio aus der Programmgruppe Microsoft SQL Server, im Startmenü. Wenn dieses Tool nicht auf dem Server installiert ist, können Sie mit dem letzten Schritt fortfahren, um das Vorhandensein zwischengespeicherter Dateien zu bestätigen.<br /><br /> 6) Wählen Sie im Server-Typ **Analysis Services**.<br /><br /> 7) Servernamen ein, geben Sie unter  **\<Servername > \powerpivot**, wobei  **\<Servername >** ist der Name des Computers, der die neue PowerPivot für SharePoint installiert wurde.<br /><br /> 8) klicken Sie auf **verbinden**.<br /><br /> 9) im Objekt-Explorer, klicken Sie auf **Datenbanken** zum Anzeigen der Liste der PowerPivot-Datendateien, die geladen werden.<br /><br /> 10) überprüfen Sie den folgenden Ordner, um festzustellen, ob Dateien zwischengespeichert werden, auf das Dateisystem des Computers, auf dem Datenträger. Das Vorhandensein zwischengespeicherter Dateien ist eine weitere Bestätigung, dass die Bereitstellung betriebsbereit ist. Um den Dateicache anzuzeigen, wechseln Sie zum Ordner \Programme\Microsoft SQL Server\MSAS11.POWERPIVOT\OLAP\Backup.<br /><br /> 11) starten Sie, die Sie zuvor beendet Dienste neu.|  
  
## <a name="see-also"></a>Siehe auch  
 [Anfängliche Konfiguration &#40;PowerPivot für SharePoint&#41;](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [PowerPivot-Serververwaltung und -konfiguration in der Zentraladministration](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
