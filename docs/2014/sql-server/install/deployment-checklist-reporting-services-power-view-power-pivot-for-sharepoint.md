---
title: 'Bereitstellungsprüfliste: Reporting Services, Power View und PowerPivot für SharePoint | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 9a2575c8-06fc-4ef4-9f24-c19e52b1bbcf
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b2c6e28a8c328bd1e38cee2f4cad74802a981aa9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095640"
---
# <a name="deployment-checklist-reporting-services-power-view-and-powerpivot-for-sharepoint"></a>Bereitstellungsprüfliste: Reporting Services, Power View und PowerPivot für SharePoint
  Verwenden Sie die folgende Checkliste, um diese BI-Funktionen in der gleichen SharePoint-Farm zu installieren: PowerPivot für SharePoint, Berichts-Generator und [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. Diese Prüfliste empfiehlt zwar eine bestimmte Installationsreihenfolge, Sie können diese Funktionen jedoch praktisch in beliebiger Reihenfolge installieren. Die Prüfliste geht davon aus, dass die folgenden Produkte oder Funktionen installiert sind:  
  
1.  SharePoint Server 2010 mit Service Pack 1 (SP1)  
  
2.  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Datenbank-Engine  
  
3.  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Reporting Services und Reporting Services-Add-In  
  
4.  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot für SharePoint  
  
 Nachdem Sie diese Funktionen installiert haben, können Sie folgende Aufgaben ausführen.  
  
-   Sie können auf die PowerPivot-Arbeitsmappen zugreifen, die Sie in PowerPivot für Excel aus SharePoint-Websites erstellt haben.  
  
-   Sie können interaktive [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]-Berichte auf Grundlage von PowerPivot-Arbeitsmappen in SharePoint erstellen.  
  
-   Sie können Berichts-Generator-Berichte erstellen, wenn Sie den Berichts-Generator in SharePoint starten.  
  
> [!NOTE]  
>  PowerPivot für SharePoint erfordert, dass Sie SharePoint 2010 Service Pack 1 (SP1) auf der SharePoint-Farm installieren. Wenn Sie die Software zu Auswertungszwecken installieren, sollten Sie ggf. mit einem bereinigten Server beginnen, um den mit dem Upgrade einer Farm verbundenen Aufwand zu vermeiden. Das Upgrade einer Farm hat gravierende Auswirkungen auf die SharePoint-Vorgänge und erfordert in der Regel eine sorgfältige Planung. Um PowerPivot für SharePoint so schnell wie möglich zu installieren, gehen Sie wie folgt vor: Installieren Sie SharePoint 2010, installieren Sie SharePoint 2010 SP1, und konfigurieren Sie die Farm in einem späteren Schritt. Ein Upgrade wird vermieden, da die Farm noch nicht konfiguriert wird, wenn Sie SharePoint 2010 SP1 installieren.  
>   
>  In dieser Prüfliste wird davon ausgegangen, dass die Farm während der Konfiguration von PowerPivot für SharePoint mit dem PowerPivot-Konfigurationstool konfiguriert wird. Alternativ können Sie den SharePoint-Produktkonfigurations-Assistenten verwenden. Mit beiden Vorgehensweisen erhalten Sie eine funktionstüchtige Farm, die PowerPivot für SharePoint unterstützt.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Sie müssen lokaler Administrator sein, um SQL Server-Setup auszuführen.  
  
 SharePoint Server 2010 Enterprise Edition ist für PowerPivot für SharePoint erforderlich. Sie können auch die Evaluation Enterprise Edition verwenden.  
  
 SharePoint Server 2010 SP1 muss installiert sein. Ist dies nicht der Fall, können Sie die Farm nicht konfigurieren, um [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Funktionen zu verwenden.  
  
 Der Computer muss einer Domäne hinzugefügt werden.  
  
 Sie müssen mindestens ein Domänenbenutzerkonto besitzen, um die Dienste bereitzustellen. Sie benötigen Domänenbenutzerkonten bei den folgenden Diensten: SharePoint-Webdienste und administratordienste, Reporting Services, Analysis Services, Excel Services, Secure Store Services und PowerPivot-Systemdienst. Domänenkonten sind für die verwaltete Konto-Funktion in SharePoint erforderlich. Die Datenbank-Engine kann mit einem virtuellen Konto bereitgestellt werden, aber alle anderen Dienste sollten als Domänenbenutzer ausgeführt werden.  
  
 Der Name der PowerPivot-Instanz muss vorhanden sein. Es darf keine benannte PowerPivot-Instanz auf dem Computer vorhanden sein, auf dem Sie PowerPivot für SharePoint installieren.  
  
 Wenn Sie PowerPivot für SharePoint auf einer vorhandenen Farm installieren, benötigen Sie mindestens eine SharePoint-Webanwendung, die für die Authentifizierung im klassischen Modus konfiguriert ist. Der PowerPivot-Datenzugriff wird nur unterstützt, wenn die Webanwendung die Authentifizierung im klassischen Modus unterstützt. Weitere Informationen zu Anforderungen für den klassischen Modus, finden Sie unter [PowerPivot-Authentifizierung und Autorisierung](../../analysis-services/power-pivot-sharepoint/power-pivot-authentication-and-authorization.md).  
  
 Überprüfen Sie die folgenden weiteren Themen, um System- und Versionsanforderungen zu verstehen:  
  
-   [Leitfaden zum Verwenden von SQL Server BI-Features in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
## <a name="steps"></a>Schritte  
 Die folgenden Schritte gehen davon aus, dass ein Administrator den Server installiert und konfiguriert. Der Setup-Benutzer in SharePoint ist zugleich Farmadministrator und oft der primäre Websiteadministrator für die Standardwebsitesammlung. Wenn Sie die folgenden Schritte unter mehreren Personen aufteilen, sind u. U. zusätzliche Berechtigungen erforderlich, um die folgenden Schritte ausführen zu können.  
  
|Schritt|Link|  
|----------|----------|  
|Führen Sie das Vorbereitungstool für SharePoint 2010-Produkte aus.|Sie müssen über die Installationsmedien für SharePoint 2010 verfügen. Das Vorbereitungstool heißt "PrerequisiteInstaller.exe" auf dem Installationsmedium.|  
|Installieren Sie SharePoint Server 2010 Enterprise Edition oder die Testversion hiervon.|Sie können bei der Installation von SharePoint auswählen, dass Sie die Farm später nach Abschluss des Setups durch Ausführen des Konfigurations-Assistenten für SharePoint 2010-Produkte konfigurieren möchten. Zum Konfigurieren der Farm warten, können Sie mit einem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Datenbank-Engine-Instanz, die in einem späteren Schritt als Datenbankserver der Farm installiert ist. Sie konfigurieren die Farm mithilfe des PowerPivot-Konfigurationstools. Dieses schließt Aktionen zum Bereitstellen der Farm ein, wenn die Farm noch nicht konfiguriert wurde.|  
|Installieren Sie SharePoint Server 2010 SP1.|Herunterladen von SP1 von [ https://support.microsoft.com/kb/2460045 ](https://go.microsoft.com/fwlink/p/?linkID=219697).|  
|Führen Sie das Setup von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] aus, um die Datenbank-Engine und PowerPivot für SharePoint zu installieren.|[Installieren von PowerPivot für SharePoint 2010](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)<br /><br /> In Schritt 1 wird die Vorgehensweise bei der Installation von PowerPivot für SharePoint beschrieben Achten Sie darauf, dass Sie in diesem Schritt auf der Seite für die Setuprolle das Kontrollkästchen aktivieren, durch das die Datenbank-Engine der Rolle hinzugefügt wird. Auf diese Weise, fügt der Datenbank-Engine zu Ihrer Installation, damit Sie sie als Datenbankserver der Farm verwenden können, wenn Sie die Farm im nächsten Schritt konfigurieren. Wenn die Farm bereits konfiguriert ist, können Sie diesen Schritt jedoch überspringen.<br /><br /> In Schritt 2 werden Sie aufgefordert, den Server zu konfigurieren. Wählen Sie für diesen Schritt das PowerPivot-Konfigurationstool aus. Es sind verschiedene Ansätze verfügbar, die Verwendung des Konfigurationstools ist für eine eigenständige Installation jedoch die effizienteste Methode.<br /><br /> Wenn SharePoint 2010 installiert, aber nicht konfiguriert wird, werden durch dieses Tool Aktionen ausgewählt, die die Farm, eine Standardwebanwendung und eine Stammwebsitesammlung erstellen. Stellen Sie sicher, diese Optionen aktiviert ist, damit die Farm erstellt wird. Wenn Sie die Farm bereits konfiguriert haben, lässt das Tool diese Aktionen aus und bietet nur die für die Konfiguration von PowerPivot für SharePoint erforderlichen Aktionen an.<br /><br /> In Schritt 3 werden Sie angewiesen, die SQL Server 2008 R2-Version des OLE DB-Anbieters von Analysis Services zu installieren. Dieser Schritt ist wichtig, damit auch Versionen einer Arbeitsmappe unterstützt werden, die die mit der SQL Server 2008 R2-Version von PowerPivot für Excel erstellt wurden.|  
|Überprüfen Sie, ob die Farm betriebsbereit ist.|Starten Sie zuerst die Zentraladministration, und vergewissern Sie sich, dass diese verfügbar ist. Öffnen Sie als Nächstes die Teamwebsite durch Eingabe http://localhost.  Es sollte eine SharePoint-Teamwebsite angezeigt werden.|  
|Überprüfen Sie, ob PowerPivot für SharePoint betriebsbereit ist.|[Überprüfen der PowerPivot für SharePoint-Installation](../../analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation.md)<br /><br /> In dieser Task wird der PowerPivot-Datenzugriff mithilfe einer Beispielarbeitsmappe geprüft, die Sie hochladen.|  
|Führen Sie das Setup von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] aus, um Reporting Services und das Reporting Services-Add-In zu installieren und zu konfigurieren.|[Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)<br /><br /> Sie können bei der Installation von Reporting Services optional der Funktionsstruktur des Setups eine zusätzliche Analysis Services-Instanz hinzufügen, wenn Sie eine zweite Ressource zum Hosten von Tabellendaten benötigen. Die zusätzliche Analysis Services-Instanz wird verwendet, um tabellarische Modelldatenbanken zu hosten, die Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellen. Tabellendatenbanken sind eine gültige Datenquelle für [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]-Berichte.<br /><br /> [Installieren von Analysis Services im Tabellenmodus](../../analysis-services/instances/install-windows/install-analysis-services.md)|  
|Überprüfen Sie, ob der Reporting Services betriebsbereit ist.|[Verify a Reporting Services Installation (Überprüfen einer Installation von Reporting Services)](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)|  
|(Websiteadministratoren) Konfigurieren Sie SharePoint-Berechtigungen.|Um SharePoint-Bibliotheken Elemente hinzuzufügen bzw. um diese zu bearbeiten oder zu löschen, sind Teilnahmeberechtigungen erforderlich. Für einen schreibgeschützten Zugriff auf Berichte und PowerPivot-Arbeitsmappen mit eingebetteten Daten reichen Anzeigeberechtigungen.<br /><br /> PowerPivot-Arbeitsmappen, auf die als externe Datenquellen zugegriffen wird (wobei die Arbeitsmappen-URL eine Verbindungszeichenfolge in einer anderen Arbeitsmappe oder einem anderen Bericht ist), erfordern Leseberechtigungen, die über Anzeigeberechtigungen hinausgehen.<br /><br /> Leseberechtigungen waren auch für BI-Semantikmodellverbindungen erforderlich. Sie müssen ggf. neue Berechtigungsstufen oder SharePoint-Gruppen erstellen, um die erforderlichen Berechtigungen zu erteilen.|  
|(Websiteadministratoren) Erweitern von Dokumentbibliotheken|Erweitern Sie die Dokumentbibliotheken um BI-Inhaltstypen: BI-Semantikmodell, Reporting Services freigegebene Datenquellen, Berichts-Generator-Berichte:<br /><br /> 1) <br />                    **Aktivieren der inhaltstypverwaltung**. Klicken Sie auf freigegebene Dokumente oder einer anderen Dokumentbibliothek auf der Registerkarte ' Bibliothek ' auf **Bibliothekseinstellungen**. Klicken Sie unter Allgemeine Einstellungen auf **Erweiterte Einstellungen**. Wählen Sie unter Inhaltstypen **Ja** ermöglichen die Verwaltung von Inhaltstypen aus, und klicken Sie dann auf **OK**.<br /><br /> 2) <br />                    **Wählen Sie die BI-Inhaltstypen**. Klicken Sie auf der Registerkarte ' Bibliothek ' auf **Bibliothekseinstellungen**. Klicken Sie unter Inhaltstypen auf **aus vorhandenen Websiteinhaltstypen hinzufügen**. Aus der Business Intelligence-Inhaltstypgruppe hinzufügen **BI Semantikmodell-Verbindungsdatei** und **Berichtsdatenquelle**. Optional können Sie auch andere Reporting Services-Inhaltstypen, z. B. Berichtsmodell, hinzufügen, um zusätzliche Szenarien für das Erstellen von Berichten zu aktivieren.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Hinzufügen einer BI Semantic Model Verbindungs-Inhaltstyps zu einer Bibliothek &#40;PowerPivot für SharePoint&#41; ](../../analysis-services/power-pivot-sharepoint/add-bi-semantic-model-connection-content-type-to-library.md) und [hinzufügen Berichtsserver-Inhaltstypen zu einer Bibliothek &#40;Reporting Services im Integrierter SharePoint-Modus&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).|  
|(Websiteadministratoren) Erstellen von Datenverbindungsdateien, die zum Starten von [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] verwendet werden.|Sie müssen als Datenquelle für [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] eine BI-Semantikmodellverbindung (.bism) oder eine gemeinsam genutzte Reporting Services-Datenquelle (.rsds) erstellen. Nachdem Sie eine Datenverbindungsdatei erstellt haben, können Sie [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] mit der Datenverbindung als Datenquelle starten.<br /><br /> [Herstellen einer BI-Semantikmodellverbindung mit einer Power Pivot-Arbeitsmappe](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)<br /><br /> [Erstellen einer BI-Semantikmodellverbindung mit einer tabellarischen Modelldatenbank](../../relational-databases/databases/model-database.md)<br /><br /> Hinweis: [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] ist verfügbar, da Sie die [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Version von Reporting Services installiert und den Server als freigegebenen Dienst konfiguriert haben. Wenn Sie Reporting Services installiert und für die SQL Server 2008-Integrationsstufe konfiguriert haben, ist [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] nicht verfügbar.|  
  
## <a name="see-also"></a>Siehe auch  
 [Von den SQL Server 2012-Editionen unterstützte Funktionen](https://go.microsoft.com/fwlink/?linkid=232473)  
  
  
