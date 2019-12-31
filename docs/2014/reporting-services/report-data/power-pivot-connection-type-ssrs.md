---
title: Power Pivot-Verbindungstyp (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a104c3c7-f118-4d02-9a0f-6859f1469d11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e9b8fb98082fb3509acf50e6546673e86962893c
ms.sourcegitcommit: 381595e990f2294dbf324ef31071e2dd2318b8dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "74200416"
---
# <a name="powerpivot-connection-type-ssrs"></a>PowerPivot-Verbindungstyp (SSRS)
  Sie können Daten mithilfe der SQL Server Analysis Services-Datenverarbeitungserweiterung aus einer PowerPivot-Arbeitsmappe abrufen, die in einem SharePoint-PowerPivot-Katalog veröffentlicht wird.  
  
 Verwenden Sie die Informationen in diesem Thema, um eine Datenquelle zu erstellen. Schritt-für-Schritt-Anweisungen finden [Sie unter Hinzufügen und Überprüfen einer Datenverbindung oder einer Datenquelle &#40;Berichts-Generator und SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Die PowerPivot-Datenquelle muss in einem PowerPivot-Katalog auf einer SharePoint-Website veröffentlicht sein.  
  
 Zur Unterstützung von Verbindungen von Berichts-Generator mit einer PowerPivot-Arbeitsmappe muss SQL Server 2008 R2 ADOMD.NET auf der Arbeitsstation installiert sein. Diese Clientbibliothek wird mit PowerPivot for Excel installiert. Wenn Sie jedoch einen Computer verwenden, der nicht über diese Anwendung verfügt, müssen Sie ADOMD.NET von der Seite [SQL Server 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=16978)herunterladen und installieren.  
  
## <a name="data-source-type"></a>Datenquellentyp  
 Verwenden Sie den Berichtsdatenquellentyp **Microsoft SQL Server Analysis Services**.  
  
## <a name="connection-string"></a>Verbindungszeichenfolge  
 Die Verbindungs Zeichenfolge ist die URL zur Power Pivot-Arbeitsmappe, die auf SharePoint im Power Pivot-Katalog oder einer anderen http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsxBibliothek veröffentlicht wurde, z. b..  
  
## <a name="credentials"></a>Anmeldeinformationen  
 Geben Sie die Anmeldeinformationen an, die Sie benötigen, um auf die PowerPivot-Arbeitsmappe und die SharePoint-Website zuzugreifen, z. B. die Windows-Authentifizierung (Integrierte Sicherheit). Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) Zeichenfolgen in Reporting Services oder [Angeben von Anmelde Informationen in Berichts-Generator](../specify-credentials-in-report-builder.md).  
  
## <a name="queries"></a>Abfragen  
 Nachdem Sie eine Verbindung mit der PowerPivot-Datenquelle hergestellt haben, verwenden Sie die grafische MDX-Abfrage, um durch Durchsuchen und Auswählen aus den zugrunde liegenden Datenstrukturen eine Abfrage zu erstellen. Nach dem Erstellen einer Abfrage können Sie die Abfrage so ausführen, dass die Beispieldaten im Ergebnisbereich angezeigt werden.  
  
 Mit dem Abfrage-Designer wird die Abfrage analysiert, um die Datasetfelder zu bestimmen. Sie können die Datasetfeldauflistung im Bereich **Berichtsdaten** auch manuell bearbeiten. Weitere Informationen finden Sie unter [Hinzufügen, Bearbeiten und Aktualisieren von Feldern im Berichtsdatenbereich &#40;Berichts-Generator und SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).  
  
## <a name="filters"></a>Filter  
 Geben Sie im Bereich "Filter" Dimensionen und Elemente an, die ausgefiltert oder in die Abfrageergebnisse eingeschlossen werden sollen.  
  
## <a name="parameters"></a>Parameter  
 Aktivieren Sie im Bereich "Filter" die Option **Parameter** für einen Filter, um automatisch einen Berichtsparameter mit verfügbaren Werten zu erstellen, die der Filterauswahl entsprechen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie den Berichts-Generator aus der PowerPivot-Arbeitsmappe in einem PowerPivot-Katalog öffnen, werden PivotTables, PivotCharts, Slicer und andere Layout- und analytische Funktionen aus der PowerPivot-Arbeitsmappe im Bericht nicht neu erstellt. Stattdessen enthält der leere Bericht eine vorkonfigurierte Datenquelle, die auf die Daten in der PowerPivot-Arbeitsmappe verweist. Berichte auf Grundlage einer PowerPivot-Arbeitsmappe zu entwerfen kann abhängig von der Anzahl von Slicern, Filtern und Tabellen oder Diagrammen, die Sie wieder im Bericht erstellen möchten, arbeitsintensiv und zeitaufwändig sein. Ein besserer Ansatz ist, die Präsentation der Daten zu planen, die Sie vom PowerPivot-Entwurf unabhängig in einem Bericht möchten.  
  
 Die Daten in einer PowerPivot-Arbeitsmappe sind stark komprimiert; aus der PowerPivot-Arbeitsmappe für einen Bericht abgerufene Daten sind nicht komprimiert. Geben Sie im Abfrage-Designer Filter und Parameter an, um die Daten auf die für den Bericht erforderliche Menge zu begrenzen.  
  
 Im Gegensatz zu einer Verbindung mit einem Analysis Services-Cube hat ein PowerPivot-Modell keine Hierarchien. Um ähnliche Funktionalität wie die von verwandten Slicern in der Arbeitsmappe bereitzustellen, müssen Sie kaskadierende Parameter im Bericht erstellen. Weitere Informationen finden Sie unter [Hinzufügen von kaskadierenden Parametern zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](../report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)erstellen.  
  
 In einigen Fällen müssen Sie möglicherweise Ausdrücke an die zugrunde liegenden Datenwerte aus dem PowerPivot-Modell anpassen. Sie müssen möglicherweise Ausdrücke ändern, um Daten in den richtigen Datentyp zu konvertieren oder eine Aggregatfunktion hinzuzufügen oder zu entfernen. Verwenden Sie zum Konvertieren eines Datentyps aus einer Zeichenfolge in eine ganze Zahl beispielsweise `=CInt`. Überprüfen Sie vor der Veröffentlichung des Berichts stets, dass der Bericht die erwarteten Werte aus den Daten im PowerPivot-Modell anzeigt.  
  
 Vorschaubilder eines Berichts in einem PowerPivot-Katalog werden nur generiert, wenn die folgenden Bedingungen erfüllt sind:  
  
-   Der Bericht und die PowerPivot-Arbeitsmappe, die die Daten bereitstellt, müssen im selben PowerPivot-Katalog gespeichert sein.  
  
-   Der Bericht enthält nur PowerPivot-Daten aus einer PowerPivot-Datenquelle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services die Benutzeroberfläche des MDX-Abfrage-Designers &#40;Berichts-Generator&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
