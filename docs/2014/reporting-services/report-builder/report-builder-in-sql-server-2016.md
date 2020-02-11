---
title: Berichts-Generator in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10428"
helpviewer_keywords:
- overview of Report Builder
- getting started
ms.assetid: 55bf4f9c-d037-412f-ae57-3fc39ce32fa5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f03f0f4c210408324ee4a2cae255ba805e0377a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107710"
---
# <a name="report-builder-in-sql-server-2014"></a>Berichts-Generator in SQL Server 2014
  Berichts-Generator ist eine Berichterstellungsumgebung für Geschäftsbenutzer, die lieber in der vertrauten [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office-Umgebung arbeiten. Beim Entwurf eines Berichts geben Sie an, wo die Daten abgerufen werden sollen, welche Daten abgerufen werden sollen und wie die Daten angezeigt werden sollen. Bei der Ausführung des Berichts übernimmt der Berichtsprozessor alle angegebenen Informationen, ruft die Daten ab und kombiniert sie mit dem Berichtslayout, um den Bericht zu generieren. Sie können Berichte im Berichts-Generator in der Vorschau anzeigen oder auf einem Berichtsserver oder einem Berichtsserver im integrierten SharePoint-Modus veröffentlichen, damit auch andere Benutzer den Bericht ausführen können.  
  
 Der Bericht in dieser Abbildung enthält eine Matrix mit Zeilen- und Spaltengruppen, Sparklines, Indikatoren und einem Zusammenfassungskreisdiagramm in der Eckzelle sowie eine Karte mit zwei Sätzen geografischer Daten, die durch Farbe und Kreisgröße dargestellt werden.  
  
 ![rs_GettingStartedReport](../media/rs-gettingstartedreport.gif "rs_GettingStartedReport")  
  
##  <a name="JumpStartReptCreation"></a>Erstellung eines Jump-Start-Berichts  
  
-   **Starten Sie den Bericht mit Berichts teilen, die** von einem anderen Benutzer in Ihrem Team erstellt wurden. Berichtsteile sind Berichtselemente, die separat auf einem Berichtsserver oder einer in einen Berichtsserver integrierten SharePoint-Website veröffentlicht wurden. Sie können in anderen Berichten wiederverwendet werden. Berichtselemente wie Tabellen, Matrizen, Diagramme und Bilder können als Berichtsteile veröffentlicht werden.  
  
-   **Beginnen Sie mit einem freigegebenen DataSet** , das von einer anderen Person in Ihrem Team erstellt wurde. Freigegebene Datasets sind auf einer freigegebenen Datenquelle basierende Abfragen, die auf einem Berichtsserver oder einer in einen Berichtsserver integrierten SharePoint-Website gespeichert werden.  
  
-   **Beginnen Sie mit dem Tabellen-, Matrix-oder Diagramm-Assistenten**. Wählen Sie eine Datenquellenverbindung aus, verschieben Sie Felder per Drag &amp; Drop, um eine Datasetabfrage zu erstellen, wählen Sie das Layout und Format aus, und passen Sie den Bericht an.  
  
-   **Beginnen Sie mit dem Karten-Assistenten** , um Berichte zu erstellen, die aggregierte Daten vor einem geografischen oder geometrischen Hintergrund anzeigen. Kartendaten können räumliche Daten aus einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage oder einer ESRI-Shape-Datei (Environmental Systems Research Institute, Inc.) sein. Sie können auch einen [!INCLUDE[msCoName](../../../includes/msconame-md.md)] -Bing Map-Kachelhintergrund hinzufügen.  
  

  
##  <a name="DesignRept"></a>Entwerfen des Berichts  
  
-   **Erstellen Sie Berichte mit Tabellen-, Matrix-, Diagramm- und Freiformberichtslayouts.** Erstellen Sie Tabellenberichte für spaltenbasierte Daten, Matrixberichte für zusammengefasste Daten (wie Kreuztabellenberichten oder PivotTable-Berichten), Diagrammberichte für grafische Daten und Freiformberichte für alle anderen Daten. In Berichte können andere Berichte und Diagramme sowie Listen, Grafiken und Steuerelemente für dynamische webbasierte Anwendungen eingebettet werden.  
  
-   **Melden Sie aus einer Vielzahl von Datenquellen.** Erstellen Sie Berichte mit Daten aus beliebigen Datenquellen Typen, die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]über einen von verwalteten Datenanbieter, OLE DB-Anbieter oder eine ODBC-Datenquelle verfügen. Sie können Berichte erstellen, die relationale und mehrdimensionale Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken, Oracle-Hyperion- sowie anderen Datenbanken enthalten. Sie können eine XML-Datenverarbeitungserweiterung verwenden, um Daten von jeder XML-Datenquelle abzurufen. Mit Tabellenwertfunktionen können Sie benutzerdefinierte Datenquellen entwerfen.  
  
-   **Ändern vorhandener Berichte.** Mithilfe Berichts-Generator können Sie Berichte anpassen und aktualisieren, die in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Berichts-Designer erstellt wurden.  
  
-   **Ändern Sie die Daten** durch Filtern, gruppieren und Sortieren von Daten oder durch Hinzufügen von Formeln oder Ausdrücken.  
  
-   **Fügen Sie Diagramme, Messgeräte, Sparklines und Indikatoren hinzu** , um Daten in einem visuellen Format zusammenzufassen und große Mengen aggregierter Informationen auf einen Blick darzustellen.  
  
-   **Fügen Sie interaktive Features** wie z. b. Dokument Zuordnungen, Schaltflächen zum anzeigen/ausblenden und Drillthrough-Links zu unter Berichten und Drillthrough-Berichten hinzu. Verwenden Sie Parameter und Filter, um Daten für benutzerdefinierte Sichten zu filtern.  
  
-   Sie können Bilder und andere Ressourcen **einbetten oder darauf verweisen** , einschließlich externer Inhalte.  
  

  
##  <a name="ManageRpt"></a>Verwalten des Berichts  
  
-   **Speichern Sie die Definition des Berichts** auf Ihrem Computer oder auf dem Berichts Server, wo Sie ihn verwalten und für andere Benutzer freigeben können.  
  
-   **Wählen Sie ein Präsentationsformat** aus, wenn Sie den Bericht öffnen, oder nachdem Sie den Bericht geöffnet haben. Sie können weborientierte, seitenorientierte und Desktopanwendungsformate auswählen. Zu den Formaten gehören HTML, MHTML, PDF, XML, CSV, TIFF, Word und Excel.  
  
-   **Richten Sie Abonnements ein.** Nachdem Sie den Bericht auf dem Berichtsserver oder einem Berichtsserver im integrierten SharePoint-Modus veröffentlicht haben, können Sie ihn so konfigurieren, dass er zu einer bestimmten Zeit ausgeführt wird. Sie können auch einen Berichtsverlauf erstellen und E-Mail-Abonnements einrichten.  
  
-   **Generieren Sie Datenfeeds** aus dem Bericht, indem Sie die Reporting Services Atom-Renderingerweiterung verwenden.  
  
> [!NOTE]  
>  Veröffentlichte Berichte werden auf einem Berichtsserver oder einem Berichtsserver im integrierten SharePoint-Modus von einem Berichtsserveradministrator verwaltet. Berichtsserveradministratoren können die Sicherheit definieren, Eigenschaften festlegen und Vorgänge planen, wie Berichtsverlauf und E-Mail-Übermittlung von Berichten. Sie können freigegebene Zeitpläne und freigegebene Datenquellen erstellen und zur allgemeinen Verwendung zur Verfügung stellen. Administratoren verwalten auch alle Berichtsserverordner. Welche Verwaltungsaufgaben ausgeführt werden können, hängt von den Berechtigungen des Benutzers ab.  
  

  
##  <a name="InThisSection"></a> In diesem Abschnitt  
 [Neues im Berichts-Generator für SQL Server 2014](../what-s-new-in-report-builder-for-sql-server-2014.md)  
 Beschreibt die neuen Funktionen in dieser Version des Berichts-Generators, einschließlich Karten.  
  
 [Tutorial: Erstellen eines Quick-Diagramm Berichts offline](tutorial-create-a-quick-chart-report-offline-report-builder.md)  
 Enthält eine Einführung in Berichts-Generator und die verfügbaren Assistenten, damit Sie Berichte erstellen können. Das Lernprogramm enthält eine Reihe von Daten, mit denen Sie arbeiten können, ohne eine Verbindung mit einer Datenquelle herstellen zu müssen.  
  
 [Planen eines Berichts &#40;Berichts-Generator&#41;](../report-design/planning-a-report-report-builder.md)  
 Enthält Informationen zu den Punkten, die Sie vor dem Erstellen des Berichts beachten sollten.  
  
 [Konzepte der Berichterstellung &#40;Berichts-Generator und SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)  
 Enthält Definitionen der Schlüsselkonzepte, die in der Dokumentation zum Berichts-Generator verwendet werden.  
  
 [Berichtsentwurfsansicht &#40;Berichts-Generator&#41;](report-design-view-report-builder.md)  
 Erläutert die unterschiedlichen Bereiche und Abschnitte der Berichtsentwurfsansicht.  
  
 [Entwurfs Ansicht für freigegebene Datasets &#40;Berichts-Generator&#41;](shared-dataset-design-view-report-builder.md)  
 Erläutert die unterschiedliche Bereiche und Abschnitte der Entwurfsansicht für freigegebene Datasets.  
  
 [Tastenkombinationen &#40;Berichts-Generator&#41;](keyboard-shortcuts-report-builder.md)  
 Bietet einen Überblick über die verfügbaren Tastenkombinationen für die Navigation und das Entwerfen von Berichten im Berichts-Generator.  
  
 [Starten Sie Berichts-Generator &#40;Berichts-Generator&#41;](start-report-builder.md)  
 Erläutert, wie die beiden Versionen von Berichts-Generator gestartet werden: eigenständige Version und [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]-Version.  
  
  
