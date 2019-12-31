---
title: Installieren des Analysis Services OLE DB-Anbieter auf SharePoint-Servern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2c62daf9-1f2d-4508-a497-af62360ee859
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: f8dcec71f8b9c90df9f30aa5bfb972fef28fbcd7
ms.sourcegitcommit: 381595e990f2294dbf324ef31071e2dd2318b8dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "74200450"
---
# <a name="install-the-analysis-services-ole-db-provider-on-sharepoint-servers"></a>Installieren des OLE DB-Anbieters für Analysis Services auf SharePoint-Servern
  Der Microsoft OLE DB-Anbieter für Analysis Services (MSOLAP) ist eine Schnittstelle, die von Clientanwendungen für die Interaktion mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Daten verwendet wird. In einer SharePoint-Umgebung, die [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] einschließt, verarbeitet der Anbieter Verbindungsanforderungen für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Daten.  
  
 Der Datenanbieter ist im [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Installationspaket (spPowerPivot.msi) enthalten, muss jedoch ggf. manuell installiert werden. Für die manuelle Installation von Clientbibliotheken oder Datenanbietern auf einem SharePoint-Server können zwei Gründe vorliegen.  
  
-   **Aktivieren**Sie die Abwärtskompatibilität. 
  [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Arbeitsmappen geben die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Version vom OLE DB-Anbieter für Analysis Services in ihrer Verbindungszeichenfolge an. Daher muss diese Anbieterversion auf dem Computer vorhanden sein, damit die Anforderung erfolgreich verarbeitet wird.  
  
-   **Aktivieren Sie den Datenzugriff für eine dedizierte Instanz von Excel Services**. Wenn die SharePoint-Farm Excel Services auf einem Server einschließt, auf dem nicht zusätzlich auch [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] enthalten ist, installieren Sie die [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]-Version des Anbieters und andere Clientkonnektivitätskomponenten mithilfe des [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Installationspakets.  
  
    > [!NOTE]  
    >  Diese Szenarien schließen sich nicht gegenseitig aus. Wenn Sie mehrere Arbeitsmappenversionen auf einer Farm hosten, die Anwendungsserver enthält, auf denen Excel Services ohne eine [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Instanz ausgeführt wird, müssen Sie sowohl die ältere als auch die neuere Version des Datenanbieters auf jedem Computer mit Excel Services installieren.  
  
  
##  <a name="bkmk_vers"></a>Versionen des OLE DB Anbieters, der den Power Pivot-Datenzugriff unterstützt  
 Eine SharePoint-Farm könnte mehrere Versionen vom OLE DB-Anbieter für Analysis Services einschließen, einschließlich früherer Versionen, die keinen PowerPivot-Datenzugriff unterstützen.  
  
 Standardmäßig installiert SharePoint 2010 die [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Version des Anbieters. Obwohl sie als MSOLAP.4 (entspricht der für [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] verwendeten Versionsnummer) identifiziert wird, funktioniert diese Version nicht für den PowerPivot-Datenzugriff. Damit Verbindungen erfolgreich hergestellt werden, müssen Sie über die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Version oder die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version des Anbieters verfügen.  
  
 Eine im Anschluss an [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] herausgegebene Version des OLE DB-Anbieters bietet Unterstützung für Transporte und Verbindungen für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Datenstrukturen. 
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Arbeitsmappen verwenden neuere Versionen dieses Anbieters, um die Abfrageverarbeitung von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Servern in der Farm anzufordern. Eine aktualisierte Version können Sie von einer Seite SQL Server Feature Pack herunterladen und installieren.  
  
 In der folgenden Tabelle werden die gültigen Optionen beschrieben:  
  
|Produktversion|Dateiversion|Gültig für:|  
|---------------------|------------------|----------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|MSOLAP100.dll im Dateisystem<br /><br /> MSOLAP.4 in einer Excel-Verbindungszeichenfolge<br /><br /> 10.50.1600 oder höher in Dateiversionsdetails|Verwenden für Datenmodelle, die mit der [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Version von PowerPivot für Excel erstellt wurden.|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|MSOLAP110.dll im Dateisystem<br /><br /> MSOLAP.5 in einer Excel-Verbindungszeichenfolge<br /><br /> 11.0.0000 oder höher in Dateiversionsdetails|Verwenden für Datenmodelle, die mit der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]- oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für Excel erstellt wurden.|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|MSOLAP120.dll im Dateisystem<br /><br /> 12.0.20000 oder höher in Dateiversionsdetails|Verwenden für andere Datenmodelle als [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Modelle|  
  
  
##  <a name="bkmk_why"></a>Gründe für die Installation des OLE DB Anbieters  
 Es gibt zwei Szenarien, die erfordern, den OLE DB-Anbieter auf Servern in der Farm manuell zu installieren.  
  
 **Das häufigste Szenario** ist, wenn Sie ältere und neuere Versionen von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappen haben, die in Dokument Bibliotheken in der Farm gespeichert werden. Wenn Analysten in Ihrer Organisation die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Version von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für Excel verwenden und die Arbeitsmappen in einer [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Installation speichern, funktionieren die älteren Arbeitsmappen nicht. Die Verbindungs Zeichenfolge verweist auf eine ältere Version des Anbieters, die sich nicht auf dem Server befindet, es sei denn, Sie installieren Sie. Werden beide Versionen installiert, wird der Datenzugriff auf PowerPivot-Arbeitsmappen aktiviert, die in älteren und neueren Versionen von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für Excel erstellt wurden. Da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Setup nicht die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Version des Anbieters installiert, müssen Sie diese manuell installieren, wenn Sie Arbeitsmappen einer früheren Version verwenden.  
  
 **Das zweite Szenario** ist, wenn Sie über einen Server in einer SharePoint-Farm verfügen, auf dem Excel [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]Services ausgeführt werden, nicht jedoch. In diesem Fall muss der Anwendungsserver, der Excel Services ausführt, manuell für die Verwendung einer neueren Version des Anbieters aktualisiert werden. Dies ist für das Herstellen einer Verbindung mit einer PowerPivot für SharePoint-Instanz erforderlich. Wenn Excel Services eine frühere Version des Anbieters verwenden, schlägt die Verbindungsanforderung fehl. Beachten Sie, dass der Anbieter mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup bzw. mithilfe des [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Installationspaket (spPowerPivot.msi) installiert werden muss, damit alle erforderlichen Komponenten, die zur Unterstützung von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] erforderlich sind, installiert werden.  
  
  
##  <a name="bkmk_sql11"></a>Installieren des SQL Server 2012 OLE DB-Anbieters auf einem Excel Services-Server mithilfe von SQL Server Setup  
 Verwenden Sie die folgenden Anweisungen, um den OLE DB-Anbieter und andere Clientkonnektivitätskomponenten SharePoint-Servern hinzuzufügen, auf denen sie noch nicht installiert wurden, wie z. B. Anwendungsserver, die Excel Services ohne PowerPivot für SharePoint auf der gleichen Hardware ausführen.  
  
 Verwenden Sie diese Anweisungen, um den aktuellen Analysis Services OLE DB-Anbieter zu installieren und **Microsoft. AnalysisServices. XMLA. dll** der globalen Assembly hinzuzufügen.  
  
#### <a name="run-sql-server-setup-and-install-the-client-connectivity-tools"></a>Ausführen von SQL Server-Setup und Installieren der Clientkonnektivitätstools  
  
1.  Führen Sie SQL Server-Setup auf dem Anwendungsserver aus, der Excel Services hostet.  
  
2.  Wählen Sie auf der Seite Installation die **Option neu SQL Server eigenständige Installation aus, oder fügen Sie einer vorhandenen Installation Features hinzu**.  
  
3.  Wählen Sie auf der Seite Installationstyp die Option **neue Installation von SQL Server 2012 ausführen aus**.  
  
4.  Wählen Sie auf der Seite Setup Rolle die Option **SQL Server Featureinstallation**aus.  
  
5.  Klicken Sie auf der Seite **Funktionsauswahl** auf **Konnektivität der Client Tools**. Mit dieser Option wird **Microsoft. AnalysisServices. XMLA. dll** installiert.  
  
     Wählen Sie keine weiteren Funktionen aus.  
  
6.  Klicken Sie auf **weiter** , um den Assistenten abzuschließen, und klicken Sie dann auf **Installieren** , um das Setup auszuführen.  
  
7.  Wiederholen Sie die vorherigen Schritte, wenn Excel Services auch auf anderen Servern ausgeführt wird, ohne dass eine PowerPivot für SharePoint auf dem gleichen Server installiert ist.  
  
#### <a name="verify-msolap5-is-a-trusted-provider"></a>Überprüfen, ob MSOLAP.5 ein vertrauenswürdiger Anbieter ist  
  
1.  Klicken Sie in der Zentraladministration auf **Dienstanwendungen verwalten**und dann auf die Excel Services-Dienstanwendung.  
  
2.  Klicken Sie auf **Vertrauenswürdige Dienstanbieter**.  
  
3.  Überprüfen Sie, dass MSOLAP.5 in der Liste angezeigt wird. Je nach der Art der Konfiguration von PowerPivot für SharePoint wird MSOLAP.5 möglicherweise bereits vertraut. Wenn Sie das PowerPivot-Konfigurationstool verwendet haben, diese Aktion dann jedoch aus der Taskliste ausgeschlossen haben, wird MSOLAP.5 nicht von Excel Services vertraut und muss daher manuell hinzugefügt werden.  
  
4.  Wenn MSOLAP nicht aufgeführt ist, klicken Sie auf **Vertrauenswürdige Datenanbieter hinzufügen**.  
  
5.  Geben Sie unter Anbieter-ID `MSOLAP.5` ein.  
  
6.  Stellen Sie sicher, dass für den Anbietertyp OLE DB ausgewählt ist.  
  
7.  Geben Sie als Anbieterbeschreibung **Microsoft OLE DB-Anbieter für OLAP Services 11.0**ein.  
  
#### <a name="verify-installation"></a>Überprüfen der Installation  
  
1.  Wechseln Sie zu Programme\Microsoft Analysis Services\AS OLEDB\110.  
  
2.  Klicken Sie mit der rechten Maustaste auf „msolap110.dll“, und wählen Sie **Eigenschaften**.  
  
3.  Klicken Sie auf **Details**.  
  
4.  Zeigen Sie die Dateiversionsinformationen an. Die Version sollte 11,00 enthalten. \<BuildNumber->.  
  
5.  Im Ordner Windows\assembly muss Microsoft.AnalysisServices.Xmla.dll der Version 11.0.0.0 enthalten sein.  
  
  
##  <a name="bkmk_install2012_from_sppowerpivot_msi"></a>Verwenden Sie das PowerPivot für SharePoint Installationspaket (sppowerpivot. msi), um den SQL Server 2012 OLE DB-Anbieter zu installieren.  
 Installieren Sie [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] den OLE DB Anbieter auf dem-und dem Excel Services [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Server mithilfe des Installationspakets **(sppowerpivot. msi)**.  
  
#### <a name="download-the-msolap5-provider-from-the-includesssql11sp1includessssql11sp1-mdmd-feature-pack"></a>Laden Sie den MSOLAP.5-Anbieter aus dem [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] Feature Pack herunter.  
  
1.  Navigieren Sie zu [Microsoft® SQL Server® 2012 SP1 Feature Pack](https://www.microsoft.com/download/details.aspx?id=35580) .  
  
2.  Klicken Sie auf **Installationsanweisungen**.  
  
3.  Weitere Informationen finden Sie im Abschnitt "Microsoft Analysis Services OLE DB-Anbieter für Microsoft SQL Server 2012 SP1". Laden Sie die Datei herunter, und starten Sie die Installation.  
  
4.  Wählen Sie auf der Seite **Funktionsauswahl** **Analysis Services OLE DB-Anbieter für SQL Server aus**. Deaktivieren Sie die Auswahl der anderen Komponenten, und schließen Sie die Installation ab. Weitere Informationen zu sppowerpivot. msi finden Sie unter [installieren oder Deinstallieren des PowerPivot für SharePoint-Add-ins &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).  
  
5.  Registrieren Sie MSOLAP.5 als vertrauenswürdigen Anbieter bei SharePoint Excel Services. Weitere Informationen finden Sie unter [Hinzufügen von MSOLAP.5 als vertrauenswürdigen Datenanbieter in Excel Services](https://technet.microsoft.com/library/hh758436.aspx).  
  
  
##  <a name="bkmk_kj"></a>Installieren des SQL Server 2008 R2-OLE DB Anbieters zum Hosten von Arbeitsmappen früherer Versionen  
 Verwenden Sie die folgenden Anweisungen, um die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Version des MSOLAP.4-Anbieters zu installieren, und registrieren Sie die Datei "Microsoft.AnalysisServices.ChannelTransport.dll". Der ChannelTransport ist eine Unterkomponente vom OLE DB-Anbieter für Analysis Services. Die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Version des Anbieters liest die Registrierung, wenn ChannelTransport zum Herstellen einer Verbindung verwendet wird. Das Registrieren der Datei ist ein Installationsnachbereitungsschritt, der nur für Verbindungen erforderlich ist, die von einem [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Anbieter auf einem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Server verarbeitet werden.  
  
#### <a name="step-1-download-and-install-the-client-library"></a>Schritt 1: Herunterladen und Installieren der Clientbibliothek  
  
1.  Suchen Sie auf der [Seite "SQL Server 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=16978)" nach Microsoft Analysis Services OLE DB-Anbieter für Microsoft SQL Server 2008 R2.  
  
2.  Laden Sie das x64-Paket des `SQLServer2008_ASOLEDB10.msi`-Installationsprogramms herunter. Obwohl der Dateiname SQLServer2008 enthält, handelt es sich um die richtige Datei für die SQL Server 2008 R2-Version des Anbieters.  
  
3.  Führen Sie auf dem Computer, der eine Installation von [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] aufweist, das MSI-Element aus, um die Bibliothek zu installieren.  
  
4.  Wenn Sie über andere Server in der Farm verfügen, die nur Excel Services ausführt, und zwar ohne [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] auf dem gleichen Server, wiederholen Sie die vorherigen Schritte, um die 2008 R2-Version des Anbieters auf dem Computer mit Excel Services zu installieren.  
  
#### <a name="step-2-register-the-microsoftanalysisserviceschanneltransportdll-file"></a>Schritt 2: Registrieren der Datei "Microsoft.AnalysisServices.ChannelTransport.dll"  
  
1.  Verwenden Sie das Hilfsprogramm "regasm.exe", um die Datei zu registrieren. Wenn Sie "Regasm. exe" noch nicht ausgeführt haben, fügen Sie den über\\geordneten Ordner "C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319" der Systempfad-Variablen hinzu.  
  
2.  Öffnen Sie eine Eingabeaufforderung mit Administratorberechtigungen.  
  
3.  Wechseln Sie zum Ordner C:\Windows\assembly\GAC_MSIL\Microsoft.AnalysisServices.ChannelTransport\10.0.0.0__89845dcd8080cc91.  
  
4.  Geben Sie den folgenden Befehl ein: `regasm microsoft.analysisservices.channeltransport.dll`  
  
5.  Wiederholen Sie die vorherigen Schritte für die Computer, auf denen Sie die 2008 R2-Version des Anbieters manuell installiert haben.  
  
#### <a name="verify-installation"></a>Überprüfen der Installation  
  
1.  Sie sollten jetzt in der Lage sein, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Arbeitsmappen in Slices aufzuteilen oder zu filtern. Wenn ein Fehler auftritt, überprüfen Sie, ob Sie die 64-Bit-Version von "regasm.exe" zum Registrieren der Datei verwendet haben.  
  
2.  Darüber hinaus können Sie die Dateiversion überprüfen.  
  
     Wechseln Sie zur Adresse `C:\Program files\Microsoft Analysis Services\AS OLEDB\10`. Klicken Sie mit der rechten Maustaste auf **msolap100. dll** , und wählen Sie **Eigenschaften** Klicken Sie auf **Details**.  
  
     Zeigen Sie die Dateiversionsinformationen an. Die Version sollte 10,50 enthalten. \<BuildNumber->.  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
