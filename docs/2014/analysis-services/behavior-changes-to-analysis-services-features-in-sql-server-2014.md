---
title: Verhaltensänderungen von Analysis Services-Funktionen in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 92ebd5cb-afb6-4b62-968f-39f5574a452b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0f7cc154a79a329bc18d02535e3f3332aa7e8b61
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52391783"
---
# <a name="behavior-changes-to-analysis-services-features-in-sql-server-2014"></a>Verändertes Verhalten von Analysis Services-Funktionen in SQL Server 2014
  In diesem Thema werden Änderungen im Verhalten von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] für mehrdimensionale, tabellarische, Datamining- und [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] -Bereitstellungen beschrieben. Verhaltensänderungen beeinflussen die Funktion und Interaktion von Funktionen in der aktuellen Version im Vergleich zu früheren Versionen von SQL Server.  
  
> [!NOTE]  
>  Eine bedeutende Änderung im Gegensatz dazu verhindert, dass ein in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] integriertes Datenmodell oder eine Anwendung ausgeführt wird. Weitere Informationen finden Sie unter [Breaking Changes to Analysis Services Features in SQL Server 2014](breaking-changes-to-analysis-services-features-in-sql-server-2014.md).  
  
 In diesem Thema:  
  
-   [Verändertes Programmverhalten in SQLServer 2014](#bkmk_sql2014)  
  
-   [Verändertes Programmverhalten in SQL Server 2012 SP1](#bkmk_sql2012sp1)  
  
-   [Verändertes Programmverhalten in SQLServer 2012](#bkmk_sql2012)  
  
##  <a name="bkmk_sql2014"></a> Verändertes Programmverhalten in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Es sind keine neuen Verhaltensänderungen für tabellarische, mehrdimensionale, Datamining- oder [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] -Funktionen für diese Version angekündigt.  Da jedoch  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] den Versionen [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] und [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] sehr ähnelt, werden Verhaltensänderungen aus den beiden vorherigen Versionen hier zur Vereinfachung angegeben, falls Sie ein Upgrade von [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]durchführen.  
  
##  <a name="bkmk_sql2012sp1"></a> Verändertes Programmverhalten in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]  
 In diesem Abschnitt werden Änderungen am Programmverhalten dokumentiert, die für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Funktionen in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]beschrieben wurden. Diese Änderungen gelten auch für [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
|Problem|Description|  
|-----------|-----------------|  
|Modelle in SQL Server 2008 R2 PowerPivot-Arbeitsmappen werden bei Verwendung in SQL Server 2012 SP1 PowerPivot für SharePoint 2013 nicht automatisch aktualisiert. Aus diesem Grund können in SQL Server 2008 R2 PowerPivot-Arbeitsmappen keine planmäßigen Datenaktualisierungen ausgeführt werden.|Arbeitsmappen der Version 2008 R2 werden zwar in [!INCLUDE[ssGeminiShortvnext](../includes/ssgeminishortvnext-md.md)]geöffnet, unterstützen aber keine planmäßigen Aktualisierungen. Wenn Sie den Aktualisierungsverlauf überprüfen, wird eine mit der folgenden vergleichbare Fehlermeldung angezeigt:<br /> "Die Arbeitsmappe enthält ein nicht unterstütztes PowerPivot-Datenmodell. Das PowerPivot-Modell in der Arbeitsmappe weist das Format von SQL Server 2008 R2 PowerPivot für Excel 2010 auf. Die folgenden PowerPivot-Modelle werden unterstützt: <br />SQL Server 2012 PowerPivot für Excel 2010<br />SQL Server 2012 PowerPivot für Excel 2013"<br /><br /> **Wie Sie eine Arbeitsmappe zu aktualisieren:** Die planmäßigen Aktualisierungen funktionieren erst, nachdem die Arbeitsmappe auf eine Arbeitsmappe der Version 2012 aktualisiert wurde. Um die Arbeitsmappe und das darin enthaltene Modell zu aktualisieren, führen Sie eines der folgenden Verfahren aus:<br /><br /> Laden Sie die Arbeitsmappe herunter, und öffnen Sie sie in einer Microsoft Excel 2010-Version, für die das SQL Server 2012 PowerPivot-Add-In für Excel installiert wurde. Speichern Sie dann die Arbeitsmappe, und veröffentlichen Sie sie auf dem SharePoint-Server erneut.<br /><br /> Laden Sie die Arbeitsmappe herunter, und öffnen Sie sie in Microsoft Excel 2013. Speichern Sie dann die Arbeitsmappe, und veröffentlichen Sie sie auf dem SharePoint-Server erneut.<br /><br /> <br /><br /> Weitere Informationen zu arbeitsmappenupgrades finden Sie unter [Aktualisieren von Arbeitsmappen und planmäßige Datenaktualisierungen &#40;SharePoint 2013&#41;](instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).|  
|Verändertes Programmverhalten in DAX [ALL Function](https://msdn.microsoft.com/library/ee634802(v=sql.120).aspx).|Wenn Sie vor [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]in Als Datumstabelle markieren eine [Date]-Spalte zur Verwendung mit der Zeitintelligenzfunktion angegeben haben und diese [Date]-Spalte als Argument an die ALL-Funktion übergeben wurde, wurde diese wiederum als Filter an eine CALCULATE-Funktion übergeben, und sämtliche Filter für alle Spalten in der Tabelle wurden unabhängig von etwaigen Slicern in der Datumsspalte ignoriert.<br /><br /> Beispiel:<br /><br /> `= CALCULATE (<expression>, ALL (DateTable[Date]))`<br /><br /> Vor [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]wurden alle Filter für sämtliche DateTable-Spalten unabhängig von der als Argument an ALL übergebenen [Date]-Spalte ignoriert.<br /><br /> In [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] und in PowerPivot in Excel 2013 werden Filter nur für die angegebene Spalte ignoriert, die als Argument an ALL übergeben wird.<br /><br /> Zur Umgehung des neuen Verhaltens, d. h, um alle Spalten als Filter für die gesamte Tabelle zu ignorieren, können Sie die [Date]-Spalte beispielsweise aus dem Argument ausschließen.<br /><br /> `=CALCULATE (<expression>, ALL(DateTable))`<br /><br /> Dadurch wird das gleiche Verhalten erzielt wie vor [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)].|  
  
##  <a name="bkmk_sql2012"></a> Verändertes Programmverhalten in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 In diesem Abschnitt werden Änderungen am Programmverhalten dokumentiert, die für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Funktionen in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]beschrieben wurden. Diese Änderungen gelten auch für [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
### <a name="analysis-services-multidimensional-mode"></a>Analysis Services, Mehrdimensionaler Modus  
  
#### <a name="nullprocessing-option-set-to-preserve-is-no-longer-supported-for-distinct-count-measures"></a>Die Festlegung der NullProcessing-Option auf „Preserve“ wird für Distinct Count Measures nicht mehr unterstützt.  
 Vor dem [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], war es möglich, legen Sie [NullProcessing-Element &#40;ASSL&#41; ](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl) zu `Preserve` für distinct Count Measures.  Leider führte diese Vorgehensweise häufig zu ungültigen Ergebnissen und manchmal sogar zum Absturz des Verarbeitungsauftrags. Aus diesem Grund wird diese Konfiguration in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]nicht mehr unterstützt. Versucht, ihn zu verwenden, verursacht den folgende Validierungsfehler auftritt: "Fehler im Metadaten-Manager. Preserve ' ist kein gültiger NullProcessing-Wert für die \<Measurename > distinct Count Measures. "  
  
#### <a name="cube-browser-in-management-studio-and-cube-designer-has-been-removed"></a>Cube-Browser in Management Studio und Cube-Designer wurde entfernt  
 Das Cube-Browser-Steuerelement, mit dem Sie Felder in eine PivotTable-Struktur in Management Studio oder im Cube-Designer ziehen und ablegen konnten, wurde aus dem Produkt entfernt. Das Steuerelement war eine OWC-Komponente (Office Web Control). OWC wurde in Office als veraltet eingestuft und ist nicht mehr verfügbar.  
  
### <a name="powerpivot-for-sharepoint"></a>PowerPivot für SharePoint  
  
#### <a name="higher-permission-requirements-for-using-a-powerpivot-workbook-as-an-external-data-source"></a>Höhere Berechtigungsanforderungen zum Verwenden einer PowerPivot-Arbeitsmappe als externe Datenquelle  
 In einer Excel-Arbeitsmappe können in derselben oder einer externen Arbeitsmappe eingebettete PowerPivot-Daten gerendert werden. In der Vorgängerversion waren die Berechtigungsanforderungen für eingebettete und externe PowerPivot-Daten gleich. Wenn Sie die Berechtigung **Nur anzeigen** für eine PowerPivot-Arbeitsmappe besaßen, konnten Sie sowohl für eingebettete Daten als auch für externe Verbindungen Vollzugriff auf alle PowerPivot-Daten in der Arbeitsmappe erhalten.  
  
 In dieser Version wurden die Berechtigungsanforderungen für Excel-Arbeitsmappen geändert, in denen PowerPivot-Daten aus einer externen Datei gerendert werden. In dieser Version benötigen Sie die Berechtigung **Lesen** (oder genauer gesagt die Berechtigung **Elemente öffnen** ), um in einer Clientanwendung eine Verbindung mit einer externen PowerPivot-Arbeitsmappe herzustellen. Die zusätzlichen Berechtigungen gewähren einem Benutzer Downloadrechte zum Anzeigen der in der Arbeitsmappe eingebetteten Quelldaten. Diese zusätzlichen Berechtigungen tragen der Tatsache Rechnung, dass Modelldaten vollständig für die Clientanwendung oder die verknüpfte Arbeitsmappe verfügbar sind, und gleichen die Berechtigungsanforderungen an das tatsächliche Datenverbindungsverhalten an.  
  
 Wenn Sie weiterhin eine PowerPivot-Arbeitsmappe als externe Datenquelle verwenden möchten, müssen Sie die SharePoint-Berechtigungen für Benutzer erhöhen, die eine Verbindung mit externen PowerPivot-Daten herstellen. Bis Sie die Berechtigungen ändern, erhalten Benutzer beim Zugreifen auf PowerPivot-Arbeitsmappen in einer Datenquellenverbindung folgende Fehlermeldung: "PowerPivot-Webdienst hat einen Fehler zurückgegeben (Zugriff verweigert. Das angeforderte Dokument ist nicht vorhanden oder Sie keine Berechtigung zum Öffnen der Datei.)"  
  
> [!WARNING]  
>  Die folgenden Schritte enthalten eine Anleitung zum Unterbrechen der Vererbung von Berechtigungen auf Bibliotheksebene und Erhöhen der Benutzerberechtigungen von **Nur anzeigen** auf **Lesen** für bestimmte Dokumente in dieser Bibliothek. Überprüfen Sie vor dem Fortfahren sorgfältig vorhandene Berechtigungen und Dokumente, und stellen Sie sicher, dass diese Schritte für Ihre Website geeignet sind.  
>   
>  Alternativ Sie können einen Ordner in der Bibliothek erstellen, alle betroffenen Dokumente in diesen Ordner verschieben und eindeutige Berechtigungen für den Ordner festlegen.  
  
> [!NOTE]  
>  Sind die Arbeitsmappen im PowerPivot-Katalog gespeichert, wird durch das Unterbrechen der Berechtigungsvererbung für eine Arbeitsmappe die Erstellung von Miniaturansichten für diese Arbeitsmappe gestört, falls sie für die Datenaktualisierung konfiguriert wurde. Um den gleichzeitigen Zugriff auf Arbeitsmappen und Vorschaubilder im Katalog zu ermöglichen, können Sie bestimmten Benutzern für alle Dokumente in der Bibliothek **Leseberechtigungen** auf Bibliotheksebene gewähren.  
  
 Sie müssen Websitebesitzer sein, um Berechtigungen zu ändern.  
  
 **So erhöhen Sie die Berechtigungen zum Lesen der Berechtigungsstufe für einzelne Arbeitsmappen**  
  
1.  Klicken Sie auf den Pfeil nach unten, um das Menü für ein einzelnes Dokument zu öffnen.  
  
2.  Klicken Sie auf **Berechtigungen verwalten**.  
  
3.  Standardmäßig erbt eine Bibliothek Berechtigungen. Um die Berechtigungen von einzelnen Arbeitsmappen in dieser Bibliothek zu ändern, klicken Sie auf **Berechtigungsvererbung beenden**.  
  
4.  Aktivieren Sie die Kontrollkästchen von Benutzern oder Gruppennamen, die zusätzliche Berechtigungen für PowerPivot-Arbeitsmappen benötigen. Zusätzliche Berechtigungen ermöglichen es diesen Benutzern, einen Link zu den eingebetteten PowerPivot-Daten zu erstellen und diese Daten als externe Datenquelle in anderen Dokumenten zu verwenden.  
  
5.  Klicken Sie auf **Benutzerberechtigungen bearbeiten**.  
  
6.  Wählen Sie **Leseberechtigungen** aus, und klicken Sie dann auf **OK**.  
  
#### <a name="powerpivot-gallery-new-rules-for-snapshot-generation-for-some-powerpivot-workbooks"></a>PowerPivot-Katalog: Neue Regeln für die Momentaufnahmegenerierung für einige PowerPivot-Arbeitsmappen  
 In dieser Version werden neue Anforderungen für die Generierung von Momentaufnahmen im PowerPivot-Katalog eingeführt. Dadurch wird eine mögliche Quelle für die Offenlegung von Informationen beseitigt, d. h. das Anzeigen von Momentaufnahmen von Daten aus einer Datenquelle, für die Sie keine Berechtigungen besitzen, wird verhindert. Diese Anforderungen gelten nur für PowerPivot-Arbeitsmappen, die jedes Mal beim Anzeigen der Arbeitsmappe eine Verbindung mit externen Datenquellen herstellen. Wenn Sie nur Arbeitsmappen mit eingebetteten PowerPivot-Daten verwenden, sehen Sie keine Änderung beim Generieren von Momentaufnahmen im PowerPivot-Katalog.  
  
 Für eine Arbeitsmappe, deren Daten jedes Mal beim Öffnen aktualisiert werden, gelten die folgenden Anforderungen für die Erstellung von Momentaufnahmen:  
  
-   PowerPivot-Arbeitsmappen, die von anderen Arbeitsmappen oder Berichten als externe Datenquellen verwendet werden, müssen sich in derselben Bibliothek befinden wie die Arbeitsmappen, die die Daten verarbeiten. Wenn beispielsweise die Datei sales-data.xlsx Daten für sales-report.xlsx bereitstellt, müssen sich beide Arbeitsmappen im Katalog befinden, damit Momentaufnahmen angezeigt werden können.  
  
-   Zusammen verwendete Arbeitsmappen müssen Berechtigungen von einem gemeinsamen übergeordneten Element, d. h. dem PowerPivot-Katalog, erben. In unserem Beispiel muss sowohl sales-data.xlsx als auch sales-report.xlsx Berechtigungen vom PowerPivot-Katalog erben.  
  
 Falls eine Arbeitsmappe eines der oben genannten Kriterien nicht erfüllt, wird das folgende gesperrte Symbol anstelle der erwarteten Miniaturansicht angezeigt:  
  
 ![GMNI_PowerPivotGalleryIcon_Locked](media/gmni-powerpivotgalleryicon-locked.gif "GMNI_PowerPivotGalleryIcon_Locked")  
  
#### <a name="new-default-setting-for-load-balancing-requests-changed-from-round-robin-to-health-based"></a>Die neue Standardeinstellung für Lastenausgleichanforderungen wurde von Roundrobin zu Zustandsbasiert geändert.  
 Eine PowerPivot-Dienstanwendung besitzt Standardeinstellungen, die festlegen, wie Anforderungen von PowerPivot-Daten auf mehreren PowerPivot für SharePoint-Servern in einer Farm verteilt werden. In der vorherigen Version lautete die Standardeinstellung **Roundrobin**. Dabei wurden Anforderungen sequenziell auf die verfügbaren Server verteilt. In dieser Version lautet der Standard **Zustandsbasiert.** Die PowerPivot-Dienstanwendung verwendet Serverzustandsstatistiken, z. B. verfügbarer Speicher oder CPU, um zu ermitteln, welche Serverinstanz die xt-Anforderung abruft.  
  
 Wurde der Server von der vorherigen Version aktualisiert, behält die PowerPivot-Dienstanwendung die vorherige Standardeinstellung (**Roundrobin**) bei. Zur Verwendung der Einstellung für die Zuordnungsmethode **Zustandsbasiert** müssen Sie die Konfigurationseinstellungen ändern. Weitere Informationen finden Sie unter [erstellen und konfigurieren Sie eine PowerPivot-Dienstanwendung in der Zentraladministration](power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Abwärtskompatibilität](../../2014/getting-started/backward-compatibility.md)   
 [Wichtige Änderungen von Analysis Services-Funktionen in SQLServer 2014](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)  
  
  
