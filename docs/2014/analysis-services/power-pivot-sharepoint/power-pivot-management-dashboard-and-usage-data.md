---
title: PowerPivot-Management-Dashboard und Verwendungsdaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 541c8b1f-c6c2-423d-a97d-65c379967e0c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ece3d8a1e9a66ecc6ad05508c975e617c523a9c8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66071123"
---
# <a name="powerpivot-management-dashboard-and-usage-data"></a>PowerPivot-Management-Dashboard und Verwendungsdaten
  Das PowerPivot-Management-Dashboard ist eine Sammlung vordefinierter Berichte und Webparts in der SharePoint-Zentraladministration, die Sie bei der Verwaltung einer SQL Server PowerPivot für SharePoint-Bereitstellung unterstützen. Das Management-Dashboard bietet Informationen zum Serverstatus, zur Arbeitsmappenaktivität sowie zur Datenaktualisierung. Das Dashboard nutzt Daten aus der Sammlung von Verwendungsdaten in SharePoint.  
  
 [Erforderliche Komponenten](#prereq)  
  
 [Übersicht über die Abschnitte des Dashboards](#items)  
  
 [Öffnen des PowerPivot-Management-Dashboard](#open)  
  
 [Quelldaten in Dashboards](#sourcedata)  
  
 [Bearbeiten eines PowerPivot-Dashboards](#edit)  
  
 [Erstellen von benutzerdefinierten Berichten für PowerPivot-Management-Dashboard](#reports)  
  
##  <a name="prereq"></a> Erforderliche Komponenten  
 Sie müssen Dienstadministrator sein, um das PowerPivot-Management-Dashboard für eine von Ihnen verwaltete PowerPivot-Dienstanwendung zu öffnen.  
  
##  <a name="items"></a> Übersicht über die Abschnitte des Dashboards  
 Das PowerPivot-Management-Dashboard enthält Webparts und eingebettete Berichte, die einen Drilldown in bestimmte Informationskategorien ermöglichen. In der folgenden Liste werden die einzelnen Bestandteile des Dashboards beschrieben:  
  
|Dashboard|Description|  
|---------------|-----------------|  
|Infrastruktur - Serverintegrität|Zeigt Trends zur CPU-Verwendung, Arbeitsspeichernutzung sowie zu Abfrageantwortzeiten im zeitlichen Verlauf an, damit Sie beurteilen können, ob die maximale Kapazität der Systemressourcen bald erreicht ist oder ob diese unterausgelastet sind.|  
|Aktionen|Enthält Links zu anderen Seiten in der Zentraladministration, darunter die aktuelle Dienstanwendung, eine Liste der Dienstanwendungen sowie die Verwendungsprotokollierung.|  
|Arbeitsmappenaktivität - Diagramm|Enthält Angaben zur Häufigkeit des Datenzugriffs. Hier können Sie erfahren, wie viele Verbindungen mit PowerPivot-Datenquellen täglich oder wöchentlich hergestellt werden.|  
|Arbeitsmappenaktivität - Liste|Enthält Angaben zur Häufigkeit des Datenzugriffs. Hier können Sie erfahren, wie viele Verbindungen mit PowerPivot-Datenquellen täglich oder wöchentlich hergestellt werden.|  
|Datenaktualisierung - Letzte Aktivität|Enthält Angaben zum Status von Datenaktualisierungsaufträgen, einschließlich fehlgeschlagener Aufträge. Dieser Bericht enthält eine zusammengesetzte Ansicht der Datenaktualisierungsvorgänge auf Anwendungsebene. Administratoren sehen auf einen Blick die Anzahl von Datenaktualisierungsaufträgen, die für die gesamte PowerPivot-Dienstanwendung definiert wurden.|  
|Datenaktualisierung - Letzte Fehler|Listet die PowerPivot-Arbeitsmappen auf, deren Datenaktualisierung nicht erfolgreich abgeschlossen wurde.|  
|Berichte|Enthält Links zu Berichten, die Sie in Excel öffnen können.|  
  
##  <a name="open"></a> Öffnen des PowerPivot-Management-Dashboard  
 Das Dashboard zeigt Informationen für jeweils eine PowerPivot-Dienstanwendung an. Sie können das Management-Dashboard von zwei unterschiedlichen Orten aus öffnen.  
  
### <a name="open-the-dashboard-from-general-application-settings"></a>Öffnen des Dashboards über die allgemeinen Anwendungseinstellungen  
  
1.  Klicken Sie in der Zentraladministration in der Gruppe **Allgemeine Anwendungseinstellungen** auf **PowerPivot-Management-Dashboard**.  
  
2.  Wählen Sie auf der Hauptseite die PowerPivot-Dienstanwendung aus, für die Sie Betriebsdaten anzeigen möchten.  
  
### <a name="open-the-dashboard-from-a-powerpivot-service-application"></a>Öffnen des Dashboards aus einer PowerPivot-Dienstanwendung  
  
1.  Klicken Sie in der Zentraladministration unter **Anwendungsverwaltung**auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie auf den Namen der PowerPivot-Dienstanwendung. Das PowerPivot-Management-Dashboard zeigt operative Daten für die aktuelle Dienstanwendung an.  
  
### <a name="change-the-current-service-application"></a>Ändern Sie die aktuelle Dienstanwendung.  
 So ändern Sie die aktuelle PowerPivot-Dienstanwendung im Management-Dashboard:  
  
1.  Beachten Sie am oberen Rand der PowerPivot-Management-Dashboard, den Namen der aktuellen dienstanwendung, z. B. **PowerPivot-Standarddienstanwendung**.  
  
2.  Klicken Sie im Dashboard **Aktionen** auf **Dienstanwendungen auflisten**.  
  
3.  Klicken Sie auf den Namen der PowerPivot-Dienstanwendung, für die Management-Dashboard-Berichte angezeigt werden sollen.  
  
##  <a name="sourcedata"></a> Quelldaten in Dashboards  
 In Dashboards, Berichten und Webparts werden Daten aus einem internen Datenmodell angezeigt, das Daten aus den System- und PowerPivot-Anwendungsdatenbanken abruft. Das interne Datenmodell ist in einer PowerPivot-Arbeitsmappe eingebettet, die auf der Website der Zentraladministration gehostet wird. Das Datenmodell verfügt über eine feste Struktur. Obwohl Sie die PowerPivot-Arbeitsmappe als Datenquelle für neue Berichte verwenden können, darf die Struktur in keiner Weise geändert werden, die die vordefinierten Berichte beeinträchtigen würde, die die Struktur verwenden.  
  
 Im Folgenden finden Sie weitere Informationen dazu, wie Daten gesammelt werden:  
  
-   [Collections von PowerPivot-Verwendungsdaten](power-pivot-usage-data-collection.md)  
  
-   [Konfigurieren der Sammlung von Verwendungsdaten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
 Achten Sie beim Sammeln von Daten zum PowerPivot-Serversystem darauf, dass für jede PowerPivot-Dienstanwendung Ereignismeldungen, Datenaktualisierungsverläufe und sonstige Verwendungsverläufe aktiviert sind. Die während des normalen Serverbetriebs gesammelten Server- und Verwendungsdaten bilden die Quelldaten, die in das interne Datenmodell übertragen werden. **Hinweis**: Wenn Sie ereignismeldungen oder verwendungsverläufe deaktivieren, werden die zusammengesetzten Berichte unvollständige oder fehlerhafte Angaben.  
  
##  <a name="edit"></a> Bearbeiten eines PowerPivot-Dashboards  
 Wenn Sie erfahren in der Dashboardentwicklung oder -anpassung sind, können Sie das Dashboard bearbeiten, um neue Webparts aufzunehmen. Sie können auch die Webparteigenschaften bearbeiten, die im Dashboard enthalten sind.  
  
##  <a name="reports"></a> Erstellen von benutzerdefinierten Berichten für PowerPivot-Management-Dashboard  
 Für Berichtszwecke werden PowerPivot-Verwendungsdaten und -verlauf in einer internen PowerPivot-Arbeitsmappe aufbewahrt, die zusammen mit dem Dashboard erstellt und konfiguriert wird. Wenn die Standardberichte die Informationen nicht enthalten, die Sie benötigen, können Sie benutzerdefinierte Berichte in Excel auf Grundlage der Arbeitsmappe erstellen. Sowohl die Arbeitsmappe als auch benutzerdefinierte Berichte, die Sie erstellen, bleiben erhalten, wenn Sie die PowerPivot-Lösungsdateien später aktualisieren oder deinstallieren. Die Arbeitsmappe und die Berichte werden in der PowerPivot-Verwaltungsbibliothek innerhalb der Website der Zentraladministration gespeichert. Diese Bibliothek ist standardmäßig nicht sichtbar. Sie können sie jedoch unter Websiteaktionen mithilfe der Aktion Alle Websiteinhalte einblenden anzeigen.  
  
 Um Ihnen den Einstieg in die benutzerdefinierte Berichterstellung zu erleichtern, bietet das PowerPivot-Management-Dashboard eine ODC (Office Data Connection)-Datei, über die eine Verbindung mit der Quellarbeitsmappe hergestellt werden kann. Beispielsweise können Sie die ODC-Datei in Excel verwenden, um zusätzliche Berichte zu erstellen.  
  
> [!NOTE]  
>  Bearbeiten Sie die Datei, um die folgenden Fehler zu vermeiden, beim Versuch die ODC-Datei in Excel zu verwenden: "Fehler bei der Initialisierung der Datenquelle". Die automatisch generierte ODC-Datei enthält einen Parameter, der vom MSOLAP-OLE DB-Anbieter nicht unterstützt wird. Die folgenden Anweisungen stellen eine Problemumgehung zum Entfernen der Parameter bereit.  
  
 Sie müssen ein Farm- oder Dienstadministrator sein, um Berichte zu erstellen, die auf der PowerPivot-Arbeitsmappe der Zentraladministration basieren.  
  
1.  Öffnen Sie das PowerPivot-Management-Dashboard.  
  
2.  Führen Sie einen Bildlauf zum Abschnitt **Berichte** am unteren Rand der Seite durch.  
  
3.  Klicken Sie auf **PowerPivot-Verwaltungsdaten**.  
  
4.  Speichern Sie die ODC-Datei in einem lokalen Ordner.  
  
5.  Öffnen Sie die ODC-Datei in einem Text-Editor.  
  
6.  Führen Sie im `<odc:ConnectionString>`-Element einen Bildlauf zum Ende der Zeile durch, und entfernen Sie `Embedded Data=False` und danach `Edit Mode=0`. Wenn das letzte Zeichen in der Zeichenfolge ein Semikolon ist, entfernen Sie es ebenfalls.  
  
7.  Speichern Sie die Datei. Die übrigen Schritte richten sich nach der verwendeten PowerPivot- und Excel-Version.  
  
8.  1.  Starten von Excel 2013  
  
    2.  Klicken Sie auf dem **PowerPivot** -Menüband auf **Verwalten**.  
  
    3.  Klicken Sie auf **Externe Daten abrufen** und dann auf **Vorhandene Verbindungen**.  
  
    4.  Klicken Sie auf die ODC-Datei, sofern sie angezeigt wird. Wenn die ODC-Datei nicht sichtbar ist, klicken Sie auf **Suche fortsetzen** und geben dann im Dateipfad die ODC-Datei an.  
  
    5.  Klicken Sie auf **Öffnen**.  
  
    6.  Klicken Sie auf **Verbindung testen** , um zu überprüfen, ob die Verbindung ordnungsgemäß arbeitet.  
  
    7.  Geben Sie einen Namen für die Verbindung ein, und klicken Sie dann auf **Weiter**.  
  
    8.  Klicken Sie im MDX-Abfrage geben Sie auf **Entwurf** zum Öffnen des MDX-Abfrage-Designers, um die Daten zusammenzustellen, denen Sie zusammenarbeiten möchten **, wenn Sie die Fehlermeldung finden Sie unter** überprüfen Sie, ob "den Namen der Bearbeitungsmodus-Eigenschaft ist nicht richtig formatiert." Sie bearbeiten die. ODC-Datei.  
  
    9. Klicken Sie auf **OK** und dann auf **Fertig stellen**.  
  
    10. Erstellen Sie PivotTable- oder PivotChart-Berichte, um die Daten in Excel visuell darzustellen.  
  
9. 1.  Starten Sie Excel 2010.  
  
    2.  Klicken Sie auf dem PowerPivot-Menüband auf die **Option zum Starten des PowerPivot-Fensters**.  
  
    3.  Klicken Sie im Menüband **Entwurf**im PowerPivot-Fenster auf Vorhandene Verbindungen.  
  
    4.  Klicken Sie auf **Suche fortsetzen**.  
  
    5.  Geben Sie im Dateipfad die ODC-Datei an.  
  
    6.  Klicken Sie auf **Öffnen**. Der Tabellenimport-Assistent wird mithilfe der Verbindungszeichenfolge zur PowerPivot-Arbeitsmappe, die die Verwendungsdaten enthält, gestartet.  
  
    7.  Klicken Sie auf **Verbindung testen** , um zu überprüfen, ob Sie Zugriff haben.  
  
    8.  Geben Sie einen Anzeigenamen für die Verbindung ein, und klicken Sie dann auf **Weiter**.  
  
    9. Klicken Sie im Bereich für das Angeben einer MDX-Abfrage auf **Entwurf** , um die Daten zusammenzutragen, mit denen Sie arbeiten möchten, und erstellen Sie dann PivotTable- oder PivotChart-Berichte, um die Daten in Excel visuell darzustellen.  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Datenaktualisierung mit SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)   
 [Konfigurieren der Sammlung von Verwendungsdaten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
