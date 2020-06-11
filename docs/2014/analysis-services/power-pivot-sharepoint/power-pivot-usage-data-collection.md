---
title: Sammlung von Power Pivot-Verwendungs Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9057cb89-fb17-466e-a1ce-192c8ca20692
author: minewiskan
ms.author: owend
ms.openlocfilehash: c5d28ef26a24f65be180b73620cf3f665db24d3c
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547812"
---
# <a name="powerpivot-usage-data-collection"></a>Sammlung von PowerPivot-Verwendungsdaten
  Die Sammlung von Verwendungsdaten ist eine SharePoint-Funktion auf Farmebene. Dieses System wird durch PowerPivot für SharePoint verwendet und ergänzt, indem Berichte im PowerPivot-Management-Dashboard bereitgestellt werden, die die Verwendung von PowerPivot-Daten und -Diensten aufzeigen. Abhängig davon, wie SharePoint installiert wird, kann die Sammlung von Verwendungsdaten für die Farm deaktiviert sein. Ein Farmadministrator muss die Verwendungsprotokollierung aktivieren, damit operative Verwendungsdaten für die Darstellung im PowerPivot-Management-Dashboard generiert werden. Weitere Informationen zum Aktivieren und Konfigurieren der Sammlung von Verwendungs Daten für Power Pivot-Ereignisse finden Sie unter [Konfigurieren der Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).  
  
 Informationen zu den Verwendungsdaten im PowerPivot-Management-Dashboard finden Sie unter [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
 **In diesem Thema:**  
  
 [Sammlung von Verwendungs Daten und Berichts Architektur](#usagearch)  
  
 [Quellen von Verwendungs Daten](#sources)  
  
 [Dienste und Zeit Geber Aufträge](#servicesjobs)  
  
 [Berichte zu Verwendungsdaten](#reporting)  
  
##  <a name="usage-data-collection-and-reporting-architecture"></a><a name="usagearch"></a> Sammlung von Verwendungsdaten und Berichtsarchitektur  
 PowerPivot-Verwendungsdaten werden mit kombinierten Funktionen aus der SharePoint-Infrastruktur und den PowerPivot-Serverkomponenten gesammelt, gespeichert, und verwaltet. Die SharePoint-Infrastruktur umfasst einen zentralen Dienst für Verwendungsdaten und integrierte Zeitgeberaufträge. Durch PowerPivot für SharePoint wird die Vorhaltedauer der in der SharePoint-Zentraladministration angezeigten PowerPivot-Verwendungsdaten und -berichte verlängert.  
  
 Ereignisinformationen gehen auf dem Anwendungsserver oder Web-Front-End in das System für die Sammlung von Verwendungsdaten ein. Die Verwendungsdaten durchlaufen das System in Reaktion auf Zeitgeberaufträge, durch die Daten aus temporären Datendateien auf dem physischen Server in den persistenten Speicher auf einem Datenbankserver verschoben werden. Das folgende Diagramm veranschaulicht, durch welche Komponenten und Prozesse Verwendungsdaten innerhalb des Datensammlungs- und Berichtssystems verschoben werden.  
  
 **Hinweis:** Vergewissern Sie sich, dass die Sammlung von Verwendungsdaten aktiviert ist. Wechseln Sie dazu in der SharePoint-Zentraladministration zu **Überwachung** . Weitere Informationen finden Sie unter [Konfigurieren der Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).  
  
 ![Komponenten und Prozesse der Verwendungsdatensammlung](../media/gmni-usagedata.gif "Komponenten und Prozesse der Verwendungsdatensammlung")  
  
|Phase|Beschreibung|  
|-----------|-----------------|  
|1|Die Sammlung von Verwendungsdaten wird durch Ereignisse ausgelöst, die von PowerPivot-Komponenten und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenanbietern in SharePoint-Bereitstellungen generiert werden. Zu den konfigurierbaren Ereignissen, die aktiviert und deaktiviert werden können, gehören Verbindungsanforderungen, Anforderungen zum Laden und Entladen sowie Ereignisse zu Abfrageantwortzeiten, die vom PowerPivot-Dienst auf dem Anwendungsserver überwacht werden. Andere Ereignisse, die ausschließlich vom Server verwaltet werden und nicht deaktiviert werden können. Diese beinhalten Datenaktualisierungs- und Serverzustandsereignisse.<br /><br /> Zu Beginn werden Verwendungsdaten unter Verwendung der Datensammlungsfunktionen des SharePoint-Systems in lokalen Protokolldateien gesammelt und gespeichert. Die Dateien und ihr Speicherort sind Teil des Standardsystems zur Sammlung von Verwendungsdaten in SharePoint. Der Speicherort der Dateien ist auf allen Servern in der Farm identisch. Um den Speicherort des Protokollierungsverzeichnisses anzuzeigen oder zu ändern, wechseln Sie in der SharePoint-Zentraladministration zu **Überwachung** und klicken auf **Verwendungs- und Integritätsdatenerfassung konfigurieren**.|  
|2|Der Zeitgeberauftrag "Import der Microsoft SharePoint Foundation-Verwendungsdaten" verschiebt Verwendungsdaten in geplanten Intervallen (standardmäßig einmal pro Stunde) aus den lokalen Dateien in die Datenbank der PowerPivot-Dienstanwendung. Wenn mehrere PowerPivot-Dienstanwendungen in einer Farm vorhanden sind, weist jede eine eigene Datenbank auf. Ereignisse enthalten interne Informationen, durch die die PowerPivot-Dienstanwendung angegeben wird, von der das Ereignis ausgelöst wurde. Mit den Anwendungsbezeichnern wird sichergestellt, dass Verwendungsdaten an die Anwendung gebunden werden, von der sie erstellt wurden.|  
|3|Die Daten werden in eine interne Berichtsdatenbank kopiert, die über die Zentraladministration für das PowerPivot-Management-Dashboard verfügbar ist.|  
|4|Die Datenquelle ist eine PowerPivot-Arbeitsmappe, auf die Sie zum Erstellen benutzerdefinierter Berichte in Excel zugreifen können. Es gibt nur eine Quellarbeitsmappe. Alle lokalisierten Berichte basieren auf derselben Quellarbeitsmappe.|  
|5|Verwendungsdaten zu PowerPivot-Dienstanwendungen werden Administratoren, die die Serverleistung und -verfügbarkeit verwalten, in Berichtsform zur Verfügung gestellt. Für die von SharePoint unterstützten Sprachen werden lokalisierte Arbeitsmappeninstanzen erstellt.<br /><br /> Weitere Informationen finden Sie unter [Berichte zu Verwendungsdaten](#reporting) in diesem Thema.|  
  
##  <a name="sources-of-usage-data"></a><a name="sources"></a> Quellen von Verwendungsdaten  
 Wenn die Sammlung von Verwendungsdaten aktiviert ist, werden Daten für die folgenden Serverereignisse generiert.  
  
|Ereignis|BESCHREIBUNG|Konfigurierbar|  
|-----------|-----------------|------------------|  
|Verbindungen|Serververbindungen, die im Namen eines Benutzers hergestellt wurden, der PowerPivot-Daten in einer Excel-Arbeitsmappe abfragt. Verbindungsereignisse identifizieren den Benutzer, der eine Verbindung mit einer PowerPivot-Arbeitsmappe geöffnet hat. In Berichten werden diese Informationen verwendet, um die häufigsten Benutzer, die PowerPivot-Datenquellen, auf die von den gleichen Benutzern zugegriffen wird, sowie Verbindungstrends im Zeitverlauf zu identifizieren.|Sie können das Konfigurieren der [Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)aktivieren und deaktivieren.|  
|Abfrageantwortzeiten|Abfrageantwortstatistiken, in denen Abfragen auf Grundlage ihrer Ausführungsdauer kategorisiert werden. Abfrageantwortstatistiken zeigen anhand von Mustern auf, wie viel Zeit der Server zur Beantwortung von Abfrageanforderungen benötigt.|Sie können das Konfigurieren der [Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)aktivieren und deaktivieren.|  
|Ladevorgänge für Daten|[!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]-Ladevorgänge für Daten. Datenladeereignisse identifizieren, welche Datenquellen am häufigsten verwendet werden.|Sie können das Konfigurieren der [Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)aktivieren und deaktivieren.|  
|Entladevorgänge für Daten|Entladevorgänge für Daten von PowerPivot-Dienstanwendungen. Ein [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] entlädt inaktive PowerPivot-Datenquellen, wenn sie nicht verwendet werden, der Server nicht über genügend Arbeitsspeicher verfügt oder zusätzlichen Arbeitsspeicher zum Ausführen von Datenaktualisierungsaufträgen benötigt.|Sie können das Konfigurieren der [Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)aktivieren und deaktivieren.|  
|Serverzustand|Servervorgänge, die den anhand der CPU- und Arbeitsspeicherauslastung ermittelten Serverzustand angeben. Hierbei handelt es sich um Verlaufsdaten. Sie enthalten keine Echtzeitinformationen zur aktuellen Verarbeitungslast des Servers.|Nein. Für dieses Ereignis werden immer Verwendungsdaten gesammelt.|  
|Datenaktualisierung|Durch den PowerPivot-Dienst für geplante Datenaktualisierungen initiierte Datenaktualisierungsvorgänge. Der Verwendungsverlauf für Datenaktualisierungen wird auf Anwendungsebene für Betriebsberichte erfasst und auf der Seite Datenaktualisierung verwalten der jeweiligen Arbeitsmappe wiedergegeben.<br /><br /> **Hinweis:** Bei [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] - und SharePoint 2013-Bereitstellungen wird die Datenaktualisierung durch Excel Services und nicht durch den Analysis Services-Server verwaltet.|Nein. Verwendungsdaten für die Datenaktualisierung werden immer gesammelt, wenn Sie die Datenaktualisierung für die PowerPivot-Dienstanwendung aktivieren.|  
  
##  <a name="services-and-timer-jobs"></a><a name="servicesjobs"></a> Dienste und Zeitgeberaufträge  
 In der folgenden Tabelle werden die Dienste sowie Speicherorte für Datensammlungen im System für die Sammlung von Verwendungsdaten beschrieben. Anweisungen zum Überschreiben der Zeitpläne für Zeit Geber Aufträge, um eine Datenaktualisierung von Server Integrität und Verwendungs Daten in Berichten des Power Pivot-Management-Dashboards zu erzwingen, finden Sie unter [Power Pivot-Datenaktualisierung mit SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md). Sie können die Zeitgeberaufträge in der SharePoint-Zentraladministration einsehen. Wechseln Sie zu **Überwachung**, und klicken Sie auf **Auftragsstatus überprüfen**. Klicken Sie auf **Auftrags Definitionen überprüfen**.  
  
|Komponente|Standardzeitplan|Beschreibung|  
|---------------|----------------------|-----------------|  
|SharePoint-Zeitgeberdienst (SPTimerV4)||Dieser Windows-Dienst wird lokal auf jedem Mitgliedscomputer in der Farm ausgeführt und verarbeitet alle auf Farmebene definierten Zeitgeberaufträge.|  
|Microsoft SharePoint Foundation für den Import von Verwendungsdaten|In SharePoint 2010 alle 30 Minuten. In SharePoint 2013 alle 5 Minuten.|Dieser Zeitgeberauftrag wird global auf Farmebene konfiguriert. Er verschiebt Verwendungsdaten aus lokalen Verwendungsprotokolldateien in die zentrale Datenbank für Verwendungsdaten. Sie können diesen Zeitgeberauftrag manuell ausführen, um einen Datenimportvorgang zu erzwingen.|  
|Microsoft SharePoint Foundation-Zeitgeberauftrag für die Verarbeitung von Verwendungsdaten|Täglich um 3:00 VORMITTAGS|**( \* )** Beginnend mit SQL Server 2012 PowerPivot für SharePoint, wird dieser Zeit Plan für Upgrade-oder Migrationsszenarien unterstützt, in denen noch ältere Verwendungs Daten in den SharePoint-Verwendungs Datenbanken enthalten sind. Ab SQL Server 2012 PowerPivot für SharePoint wird die SharePoint-Verwendungsdatenbank weder für die Sammlung von PowerPivot-Verwendungsdaten noch für den Workflow des Management-Dashboards verwendet. Der Zeitgeberauftrag kann manuell ausgeführt werden, um verbliebene PowerPivot-bezogene Daten in der SharePoint-Verwendungsdatenbank in die Datenbanken der PowerPivot-Dienstanwendung zu verschieben.<br /><br /> Dieser Zeitgeberauftrag wird global auf Farmebene konfiguriert. Er überprüft die zentrale Datenbank für Verwendungsdaten auf abgelaufene Verwendungsdaten (d. h. auf Datensätze, die älter als 30 Tage sind). Für PowerPivot-Server in der Farm führt dieser Zeitgeberauftrag eine zusätzliche Überprüfung auf PowerPivot-Verwendungsdaten aus. Wenn PowerPivot-Verwendungsdaten erkannt werden, verschiebt der Zeitgeberauftrag die Daten in die Datenbank einer Dienstanwendung und verwendet dabei den Anwendungsbezeichner, um die richtige Datenbank zu identifizieren.<br /><br /> Sie können diesen Zeitgeberauftrag manuell ausführen, um eine Überprüfung auf abgelaufene Daten oder einen Import von PowerPivot-Verwendungsdaten in die Datenbank einer PowerPivot-Dienstanwendung zu erzwingen.|  
|Zeitgeberauftrag für die Verarbeitung des PowerPivot-Management-Dashboards|Täglich um 3:00 VORMITTAGS|Dieser Zeitgeberauftrag aktualisiert die interne PowerPivot-Arbeitsmappe, die Verwaltungsdaten für das PowerPivot-Management-Dashboard enthält. Er ruft aktualisierte Informationen ab, die von SharePoint verwaltet werden, einschließlich Servernamen, Benutzernamen, Anwendungsnamen und Dateinamen, die in Dashboardberichten oder Webparts angezeigt werden.|  
  
##  <a name="reporting-on-usage-data"></a><a name="reporting"></a>Berichterstellung zu Nutzungsdaten  
 Um Verwendungsdaten zu PowerPivot-Daten zu überprüfen, können Sie integrierte Berichte im PowerPivot-Management-Dashboard anzeigen. In den integrierten Berichten werden Verwendungsdaten konsolidiert, die aus Berichtsdatenstrukturen in der Datenbank der Dienstanwendung abgerufen werden. Da die zugrunde liegenden Berichtsdaten täglich aktualisiert werden, enthalten die integrierten Verwendungsberichte erst aktuelle Informationen, nachdem die Daten vom Microsoft SharePoint Foundation-Zeitgeberauftrag für die Verarbeitung von Verwendungsdaten in die Datenbank einer PowerPivot-Dienstanwendung kopiert wurden. Standardmäßig geschieht dies einmal am Tag.  
  
 Weitere Informationen zum Anzeigen von Berichten finden Sie unter [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Power Pivot-Management-Dashboard und Verwendungs Daten](power-pivot-management-dashboard-and-usage-data.md)   
 [Die Konfigurations Einstellungs Referenz &#40;PowerPivot für SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Konfigurieren der Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
