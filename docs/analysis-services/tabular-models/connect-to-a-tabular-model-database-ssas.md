---
title: Herstellen einer Verbindung einer Analysis Services-Datenbank für tabellarische Modelle mit | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 239559dc7d5bfdabe3a3f9060bc92059982c8dae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62469479"
---
# <a name="connect-to-a-tabular-model-database"></a>Herstellen einer Verbindung mit einer Datenbank für tabellarische Modelle  
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Nachdem Sie ein tabellarisches Modell erstellt und auf einem Analysis Services-Tabellenmodus-Server bereitgestellt haben, müssen Sie Berechtigungen festlegen, die es für Clientanwendungen verfügbar machen. In diesem Artikel wird erläutert, wie Sie Berechtigungen und von Clientanwendungen eine Verbindung mit einer Datenbank.  
  
> [!NOTE]  
>  Remoteverbindungen mit Analysis Services sind standardmäßig erst dann verfügbar, wenn Sie die Firewall konfiguriert haben. Stellen Sie sicher, dass Sie den entsprechenden Port geöffnet haben, wenn Sie eine benannte oder eine Standardinstanz für Clientverbindungen konfigurieren. Weitere Informationen finden Sie unter [Configure the Windows Firewall to Allow Analysis Services Access](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
##  <a name="bkmk_userpermissions"></a> Benutzerberechtigungen für die Datenbank  
 Benutzer, die eine Verbindung mit Tabellendatenbanken herstellen, müssen die Mitgliedschaft in einer Datenbankrolle besitzen, die einen Lesezugriff festlegt.  
  
 Rollen, und gelegentlich auch die Rollenmitgliedschaft, werden definiert, wenn ein Modell in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt wird, oder über [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Falle von bereitgestellten Modellen. Weitere Informationen zum Erstellen von Rollen mithilfe des Rollen-Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], finden Sie unter [erstellen und Verwalten von Rollen](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md). Weitere Informationen zum Erstellen und Verwalten von Rollen für ein bereitgestelltes Modell finden Sie unter [Rollen tabellarischer Modelle](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md).  
  
> [!CAUTION]  
>  Wenn ein tabellarisches Modellprojekt, dessen Rollen mithilfe des Rollen-Managers in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] definiert wurden, erneut bereitgestellt wird, dann werden die in einem bereitgestellten tabellarischen Modell definierten Rollen überschrieben.  
  
##  <a name="bkmk_admin"></a> Administratorberechtigungen für den Server  
 Für Organisationen, die SharePoint zum Hosten von Excel-Arbeitsmappen oder Reporting Services-Berichten verwenden, ist eine zusätzliche Konfiguration erforderlich, um tabellarische Modelldaten für SharePoint-Benutzer verfügbar zu machen. Wenn Sie SharePoint nicht verwenden, überspringen Sie diesen Abschnitt.  
  
 Zum Anzeigen von Excel-Arbeitsmappen oder [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Berichten, die Tabellendaten enthalten, muss das zum Ausführen von Excel Services oder Reporting Services verwendete Konto über Administratorberechtigungen für die Analysis Services-Instanz verfügen. Administratorberechtigungen sind erforderlich, damit diesen Services von der Analysis Services-Instanz vertraut wird.  
  
#### <a name="grant-administrative-access-on-the-server"></a>Gewähren von Administratorzugriff auf den Server  
  
1.  Öffnen Sie in der Zentraladministration die Seite "Dienstkonten konfigurieren".  
  
2.  Wählen Sie den von Excel Services verwendeten Dienstanwendungspool aus. Dies kann **Dienstanwendungspool – Systemstandard für SharePoint-Webdienste** oder einen benutzerdefinierten Anwendungspool. Das von Excel Services verwendete verwaltete Konto wird auf der Seite angezeigt.  
  
     Bei SharePoint-Farmen, die Reporting Services im SharePoint-Modus umfassen, müssen Sie die Kontoinformationen für die Reporting Services-Dienstanwendung ebenfalls abrufen.  
  
     In den folgenden Schritten fügen Sie die entsprechenden Konten der Serverrolle in der Analysis Services-Instanz hinzu.  
  
3.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her. Klicken Sie mit der rechten Maustaste auf die Serverinstanz, und wählen Sie **Eigenschaften**aus. Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf **Rollen** , und wählen Sie anschließend **Neue Rolle**aus.  
  
4.  Klicken Sie auf der Eigenschaftenseite für Analysis Services auf **Sicherheit**.  
  
5.  Klicken Sie auf **Hinzufügen**, und geben Sie dann das von Excel Services verwendete Konto ein, gefolgt von dem von Reporting Services verwendeten Konto.  
  
##  <a name="bkmk_excelconn"></a> Herstellen einer Verbindung von Excel oder SharePoint aus  
 Clientbibliotheken, die Zugriff auf Analysis Services-Datenbanken bieten, können verwendet werden, um eine Verbindung mit auf einem Tabellenmodus-Server ausgeführten Modelldatenbanken herzustellen. Bibliotheken umfassen den OLE DB-Anbieter für Analysis Services, ADOMD.NET und AMO.  
  
 Excel verwendet den OLE DB-Anbieter. Wenn Sie entweder über MSOLAP.4 aus SQL Server 2008 R2 (Dateiname msolap100.dll, Version 10.50.1600.1) oder MSOLAP.5 (Dateiname msolap110.dll) verfügen, der mit der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Version von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für Excel installiert wird, besitzen Sie eine Version, die eine Verbindung mit tabellarischen Datenbanken herstellt.  
  
 Wählen Sie eine der folgenden Vorgehensweisen aus, um eine Verbindung mit Modelldatenbanken aus Excel herzustellen:  
  
-   Erstellen Sie mithilfe der im nächsten Abschnitt bereitgestellten Anweisungen eine Datenverbindung innerhalb von Excel.  
  
-   Erstellen Sie eine BI-Semantikmodell-Verbindungsdatei (BISM-Datei) in SharePoint, die die Umleitung zu einer Datenbank bereitstellt, die auf einem Analysis Services-Tabellenmodus-Server ausgeführt wird. Eine BI-Semantikmodell-Verbindungsdatei stellt einen Befehl per rechten Mausklick bereit, der Excel mithilfe der in der Verbindung angegebenen Modelldatenbank startet. Er startet auch [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] , wenn Reporting Services installiert ist. Weitere Informationen zum Erstellen und Verwenden von BI-Semantikmodell-Verbindungsdateien finden Sie unter [Erstellen einer BI-Semantikmodellverbindung mit einer tabellarischen Modelldatenbank](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).  
  
-   Erstellen Sie eine gemeinsame Datenquelle für Reporting Services, die auf eine Tabellendatenbank als Datenquelle verweist. Sie können die gemeinsame Datenquelle in SharePoint erstellen und sie zum Starten von [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]verwenden.  
  
#### <a name="connect-from-excel"></a>Herstellen einer Verbindung von Excel aus  
  
1.  Klicken Sie in Excel auf der Registerkarte **Daten** unter **Externe Daten abrufen**auf **Aus anderen Quellen**.  
  
2.  Wählen Sie **Aus Analysis Services**aus.  
  
3.  Geben Sie unter **Servername**den Namen der Analysis Services-Instanz an, die die Datenbank hostet. Der Servername ist häufig der Name des Computers, auf dem die Software ausgeführt wird. Wenn der Server als benannte Instanz installiert wurde, müssen Sie den Namen im folgenden Format angeben: \<Servername >\\< Instancename\>.  
  
     Die Serverinstanz muss für die eigenständige tabellarische Bereitstellung konfiguriert sein, und die Serverinstanz muss eine eingehende Regel aufweisen, die den Zugriff darauf zulässt. Weitere Informationen finden Sie unter [Bestimmen des Servermodus einer Analysis Services-Instanz](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md) und [Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
4.  Wählen Sie **Windows-Authentifizierung verwenden** bezüglich der Anmeldeinformationen aus, wenn Sie Leseberechtigungen für die Datenbank besitzen. Wählen Sie anderenfalls **Benutzername und Kennwort verwenden**aus, und geben Sie den Benutzernamen und das Kennwort eines Windows-Kontos ein, das über Datenbankberechtigungen verfügt. Klicken Sie auf **Weiter**.  
  
5.  Wählen Sie die Datenbank aus. Eine gültige Auswahl zeigt einen einzelnen **Modell** -Cube für die Datenbank an. Klicken Sie auf **Weiter** und anschließend auf **Fertig stellen**.  
  
 Nachdem die Verbindung hergestellt wurde, können Sie mithilfe der Daten eine PivotTable oder ein PivotChart erstellen. Weitere Informationen finden Sie unter [in Excel analysieren](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md).  
  
##  <a name="bkmk_sharepoint"></a> Herstellen einer Verbindung von SharePoint aus  
 Wenn Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint verwenden, können Sie eine BI-Semantikmodell-Verbindungsdatei in SharePoint erstellen, die die Umleitung zu einer Datenbank ermöglicht, die auf einem Analysis Services-Server im tabellarischen Modus ausgeführt wird. Eine BI-Semantikmodell-Verbindung stellt einen HTTP-Endpunkt für eine Datenbank bereit. Sie vereinfacht auch den Tabellenmodell-Zugriff für Wissensarbeiter, die routinemäßig Dokumente auf einer SharePoint-Website verwenden. Wissensarbeiter müssen nur den Speicherort der BI-Semantikmodell-Verbindungsdatei oder die URL kennen, um auf Tabellenmodell-Datenbanken zuzugreifen. Details zum Serverspeicherort oder Datenbanknamen werden in der BI-Semantikmodell-Verbindung gekapselt. Weitere Informationen zum Erstellen und Verwenden von BI-Semantikmodell-Verbindungsdateien finden Sie unter [PowerPivot-BI-Semantikmodell-Verbindung &#40;.bism&#41;](../../analysis-services/power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md) und [Erstellen einer BI-Semantikmodellverbindung mit einer tabellarischen Modelldatenbank](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).  
  
##  <a name="bkmk_Tshoot"></a> Beheben von Verbindungsproblemen  
 Dieser Abschnitt enthält Ursachen und Lösungsschritte für Probleme, die beim Herstellen einer Verbindung mit einer Tabellenmodell-Datenbank auftreten.  
  
 **Der Datenverbindungs-Assistent kann keine Liste von Datenbanken aus der angegebenen Datenquelle abrufen.**  
  
 Beim Importieren von Daten tritt dieser Microsoft Excel-Fehler auf, wenn Sie versuchen, den Assistenten zum Herstellen einer Verbindung zu einer tabellarischen Modelldatenbank auf einem Analysis Services-Remoteserver verwenden, und Sie verfügen nicht über ausreichende Berechtigungen. Um diesen Fehler zu beheben, müssen Sie über Benutzerzugriffsrechte für die Datenbank verfügen. Weitere Informationen finden Sie weiter oben in diesem Thema in den Anweisungen zum Gewähren von Benutzerzugriff auf Daten.  
  
 **Fehler beim Versuch, eine Verbindung mit der externen Datenquelle herzustellen. Die folgenden Verbindungen wurden nicht aktualisiert: \<Modellname >-Sandbox**  
  
 In SharePoint tritt dieser Microsoft Excel-Fehler auf, wenn Sie eine Dateninteraktion, z. B. das Filtern von Daten, in einer PivotTable durchführen, die Modelldaten verwendet. Der Fehler tritt auf, da Sie nicht über ausreichende Berechtigungen für den Analysis Services-Remoteserver verfügen. Um diesen Fehler zu beheben, müssen Sie über Benutzerzugriffsrechte für die Datenbank verfügen. Weitere Informationen finden Sie weiter oben in diesem Thema in den Anweisungen zum Gewähren von Benutzerzugriff auf Daten.  
  
 **Fehler beim Versuch, diesen Vorgang auszuführen. Laden Sie die Arbeitsmappe erneut, und wiederholen Sie dann, um diesen Vorgang erneut auszuführen.**  
  
 In SharePoint tritt dieser Microsoft Excel-Fehler auf, wenn Sie eine Dateninteraktion, z. B. das Filtern von Daten, in einer PivotTable durchführen, die Modelldaten verwendet. Der Fehler tritt auf, da Excel Services nicht von der Analysis Services-Instanz vertraut wird, in der die Modelldaten bereitgestellt werden. Um diesen Fehler zu beheben, gewähren Sie Excel Services Administratorberechtigung für die Analysis Services-Instanz. Weitere Informationen finden Sie weiter oben in diesem Thema in den Anweisungen zum Gewähren von Administratorberechtigungen. Wenn der Fehler weiterhin auftritt, verwenden Sie wieder den Excel Services-Anwendungspool.  
  
 **Während des Herstellens einer Verbindung mit der in der Arbeitsmappe verwendeten externen Datenquelle ist ein Fehler aufgetreten.**  
  
 In SharePoint tritt dieser Microsoft Excel-Fehler auf, wenn Sie eine Dateninteraktion, z. B. das Filtern von Daten, in einer PivotTable durchführen, die Modelldaten verwendet. Der Fehler tritt auf, da der Benutzer nicht über ausreichende SharePoint-Berechtigungen für die Arbeitsmappe verfügt. Der Benutzer muss mindestens über **Leseberechtigungen** verfügen. **Nur anzeigen** -Berechtigungen sind für den Datenzugriff nicht ausreichend.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellung von Tabellenmodelllösungen](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
  
