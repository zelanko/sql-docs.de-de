---
title: Übersetzungen (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence Development Studio, translations [Analysis Services]
- translations [Analysis Services], about translations
- object translations [Analysis Services]
- language identifiers [Analysis Services]
- attribute translations [Analysis Services]
- translations [Analysis Services]
ms.assetid: 018471e0-3c82-49ec-aa16-467fb58a6d5f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e97c9ba15aab664e9f0c77f9eb84152f75c3e3d7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66065878"
---
# <a name="translations-analysis-services"></a>Übersetzungen (Analysis Services)
  **[!INCLUDE[applies](../includes/applies-md.md)]** Nur mehrdimensional  
  
 In einem mehrdimensionalen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenmodell können Sie mehrere Übersetzungen einer Beschriftung einbetten, um gebietsschemaspezifische Zeichenfolgen basierend auf der LCID bereitzustellen. Übersetzungen können für den Datenbanknamen, Cubeobjekte und Datenbankdimensionsobjekte hinzugefügt werden.  
  
 Durch Definieren einer Übersetzung werden Metadaten und die übersetzte Beschriftung innerhalb des Modells erstellt, um jedoch lokalisierte Zeichenfolgen in einer Clientanwendung zu rendern, müssen Sie entweder die `Language`-Eigenschaft für das Objekt festlegen oder einen `Locale Identifier`-Parameter in der Verbindungszeichenfolge übergeben (z. B. durch Festlegen von `LocaleIdentifier=1036` für die Rückgabe von französischen Zeichenfolgen). Planen Sie die Verwendung von `Locale Identifier`, wenn Sie mehrere, gleichzeitige Übersetzungen des gleichen Objekts in verschiedenen Sprachen unterstützen möchten. Das Festlegen der `Language`-Eigenschaft funktioniert, hat aber Auswirkungen auf Verarbeitung und Abfragen, die möglicherweise unerwartete Ergebnisse liefern. Das Festlegen von `Locale Identifier` ist die bessere Wahl, da es nur verwendet wird, um die übersetzten Zeichenfolgen zurückzugeben.  
  
 Eine Übersetzung besteht aus einem Gebietsschemabezeichner (LCID), einer übersetzten Beschriftung für das Objekt (z. B. Dimensions- oder Attributname) und optional einer Bindung an eine Spalte, die Datenwerte in der Zielsprache enthält. Sie können mehrere Übersetzungen haben, jedoch nur jeweils eine für eine bestimmte Verbindung verwenden. Theoretisch können Sie beliebig viele Übersetzungen im Modell einbetten. Jede Übersetzung erhöht jedoch die Komplexität beim Testen, und alle Übersetzungen müssen dieselbe Sortierung verwenden. Beim Entwerfen Ihrer Lösung sollten Sie diese natürlichen Einschränkungen bedenken.  
  
> [!TIP]  
>  Sie können Clientanwendungen wie Excel, Management Studio und [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] verwenden, um übersetzte Zeichenfolgen zurückzugeben. Weitere Informationen finden Sie unter [Tipps und Best Practices für die Globalisierung &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md) .  
  
## <a name="setting-up-a-model-to-support-translated-members"></a>Einrichten eines Modells zur Unterstützung übersetzter Elemente  
 Ein in einer mehrsprachigen Lösung verwendetes Datenmodell benötigt mehr als übersetzte Beschriftungen (Feldnamen und Beschreibungen). Es muss auch Datenwerte bereitstellen, die in verschiedenen Sprachskripts formuliert sind. Für eine mehrsprachige Lösung müssen einzelne Attribute vorhanden sein, die an Spalten in einer externen Datenbank gebunden sind, die die Daten zurückgeben.  
  
 Die Adventure Works-Beispieldatenbanken (sowohl die mehrdimensionale als auch das relationale Datawarehouse) veranschaulichen die Übersetzungsfunktion. Das Beispielmodell enthält übersetzte Beschriftungen und Beschreibungen. Das relationale Data Warehouse-Beispiel enthält Spalten mit übersetzten Werten, die lokalisierte Attributelemente im Modell bereitstellen.  
  
 So zeigen Sie die im Modell verfügbaren übersetzten Datenwerte an:  
  
1.  Öffnen Sie das mehrdimensionale Adventure Works-Modell im Designer.  
  
2.  Öffnen Sie in Projektmappen-Explorer Datenquellen Sichten, und doppelklicken Sie auf Adventure\<Works DW-Version>. DSV.  
  
3.  Suchen Sie nach dimDate, dimProduct, dimProductCategory oder dimProductSubcateogry. Alle diese Dimensionen enthalten Attribute für übersetzte Elemente für Monat, Tag der Woche, Produktname, Kategoriename usw.  
  
4.  Klicken Sie mit der rechten Maustaste auf ein beliebiges Feld, und wählen Sie **Daten durchsuchen**aus. Für jedes Element werden Übersetzungen in Englisch, Spanisch und Französisch angezeigt.  
  
 Formate für Datum, Uhrzeit und Währung werden nicht durch Übersetzungen implementiert. Um kulturspezifische Formate basierend auf dem Gebietsschema des Clients dynamisch bereitzustellen, verwenden Sie den Währungsumrechnungs-Assistenten und die `FormatString`-Eigenschaft. Weitere Einzelheiten finden Sie unter [Währungsumrechnungen &#40;Analysis Services&#41;](currency-conversions-analysis-services.md) und [FormatString-Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/formatstring-element-assl).  
  
 [Lesson 9: Defining Perspectives and Translations](lesson-9-defining-perspectives-and-translations.md) im Analysis Services-Lernprogramm führt Sie durch die Schritte zum Erstellen und Testen von Übersetzungen.  
  
## <a name="defining-translations"></a>Definieren von Übersetzungen  
 Durch Definieren einer Übersetzung wird ein `Translation`-Objekt als untergeordnetes Element des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank-, -Dimensions- oder -Cubeobjekts erstellt. Öffnen Sie mit [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] die Projektmappe, und definieren Sie Übersetzungen.  
  
### <a name="add-translations-to-a-cube"></a>Hinzufügen von Übersetzungen zu einem Cube  
 Sie können Übersetzungen zu Cubes, Measuregruppen, Measures, Cubedimensionen, Perspektiven, KPIs, Aktionen, benannten Mengen und berechneten Elementen hinzufügen.  
  
1.  Doppelklicken Sie im Projektmappen-Explorer auf einen Cubenamen, um den Cube-Designer zu öffnen.  
  
2.  Klicken Sie auf die Registerkarte **translations** . Alle Objekte, die Übersetzungen unterstützen, werden auf dieser Seite aufgeführt.  
  
3.  Geben Sie für jedes Objekt die Zielsprache (wird intern in eine LCID aufgelöst), die übersetzte Beschriftung und die übersetzte Beschreibung an. Die Sprachenliste ist überall in Analysis Services konsistent, egal, ob Sie die Serversprache in Management Studio festlegen oder die Übersetzungsüberschreibung zu einem einzelnen Attribut hinzufügen.  
  
     Denken Sie daran, dass Sie die Sortierung nicht ändern können. Ein Cube verwendet im Wesentlichen eine Sortierung, selbst wenn Sie mehrere Sprachen durch übersetzte Beschriftungen unterstützen (es gibt eine Ausnahme für Dimensionsattribute, die weiter unten erläutert wird). Wenn die Sprachen nicht ordnungsgemäß unter der freigegebenen Sortierung sortiert werden, müssen Sie Kopien des Cubes erstellen, um den Sortierungsanforderungen gerecht zu werden.  
  
4.  Erstellen Sie das Projekt, und stellen Sie es bereit.  
  
5.  Stellen Sie mithilfe einer Clientanwendung wie Excel eine Verbindung mit der Datenbank her, und ändern Sie dabei die Verbindungszeichenfolge so, dass sie den Gebietsschemabezeichner verwendet. Weitere Informationen finden Sie unter [Tipps und Best Practices für die Globalisierung &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md) .  
  
### <a name="add-translations-to-a-dimension-and-attributes"></a>Hinzufügen von Übersetzungen zu einer Dimension und Attributen  
 Sie können Übersetzungen zu Datenbankdimensionen, Attributen, Hierarchien und Ebenen innerhalb einer Hierarchie hinzufügen.  
  
 Übersetzte Beschriftungen werden mithilfe Ihrer Tastatur oder durch Kopieren und Einfügen manuell zum Modell hinzugefügt, bei Dimensionsattributelementen können Sie die übersetzten Werte jedoch aus einer externen Datenbank abrufen. Insbesondere kann die `CaptionColumn`-Eigenschaft eines Attributs an eine Spalte in einer Datenquellensicht gebunden werden.  
  
 Auf Attributebene können Sie Sortierungseinstellungen überschreiben, z. B. können Sie die Unterscheidung nach Breite anpassen oder für ein bestimmtes Attribut eine binäre Sortierung verwenden. In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]wird die Sortierung dort zur Verfügung gestellt, wo Datenbindungen definiert sind. Da Sie eine Dimensionsattributübersetzung an eine andere Quellspalte in der Datenquellensicht binden, ist eine Sortierungseinstellung verfügbar, sodass Sie die Sortierung der Quellspalte angeben können. Weitere Informationen zur Spaltensortierung in der relationalen Datenbank finden Sie unter [Set or Change the Column Collation](../relational-databases/collations/set-or-change-the-column-collation.md) .  
  
1.  Doppelklicken Sie im Projektmappen-Explorer auf den Dimensionsnamen, um den Dimensions-Designer zu öffnen.  
  
2.  Klicken Sie auf die Registerkarte **translations** . Alle Dimensions Objekte, die Übersetzungen unterstützen, werden auf dieser Seite aufgeführt.  
  
     Geben Sie für jedes Objekt die Zielsprache (wird in eine LCID aufgelöst), die übersetzte Beschriftung und die übersetzte Beschreibung an. Die Sprachenliste ist überall in Analysis Services konsistent, egal, ob Sie die Serversprache in Management Studio festlegen oder die Übersetzungsüberschreibung zu einem einzelnen Attribut hinzufügen.  
  
3.  Um ein Attribut an eine Spalte binden, müssen Sie folgende übersetzte Werte angeben:  
  
    1.  Fügen Sie im Dimensions-Designer unter **Übersetzungen**eine neue Übersetzung hinzu. Wählen Sie die Sprache aus. Auf der Seite wird eine neue Spalte für die übersetzten Werte angezeigt.  
  
    2.  Platzieren Sie den Cursor in einer leeren Zelle neben einem der Attribute. Das Attribut darf nicht der Schlüssel sein, aber alle anderen Attribute sind zulässige Optionen. Eine kleine Schaltfläche mit einem Punkt darin sollte angezeigt werden. Klicken Sie auf die Schaltfläche, um das Dialogfeld **Attributdatenübersetzung**zu öffnen.  
  
    3.  Geben Sie eine Übersetzung für die Beschriftung ein. Diese wird als Datenbeschriftung in der Zielsprache verwendet, z. B. als Feldname in einer PivotTable-Feldliste.  
  
    4.  Wählen Sie die Quellspalte aus, die die übersetzten Werte der Attributelemente bereitstellt. Nur bereits vorhandene Spalten in der an die Dimension gebundene Tabelle oder Abfrage sind verfügbar. Wenn die Spalte nicht vorhanden ist, müssen Sie die Datenquellensicht, die Dimension und den Cube zur Auswahl der Spalte ändern.  
  
    5.  Wählen Sie ggf. die Sortierung und die Sortierreihenfolge.  
  
4.  Erstellen Sie das Projekt, und stellen Sie es bereit.  
  
5.  Stellen Sie mithilfe einer Clientanwendung wie Excel eine Verbindung mit der Datenbank her, und ändern Sie dabei die Verbindungszeichenfolge so, dass sie den Gebietsschemabezeichner verwendet. Weitere Informationen finden Sie unter [Tipps und Best Practices für die Globalisierung &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md) .  
  
### <a name="add-a-translation-of-the-database-name"></a>Hinzufügen einer Übersetzung des Datenbanknamens  
 Auf Datenbankebene können Sie Übersetzungen für den Datenbanknamen und die Beschreibung hinzufügen. Der übersetzte Datenbankname ist möglicherweise bei Clientverbindungen sichtbar, die die LCID der Sprache angeben, das hängt jedoch vom Tool ab. Bei Anzeige der Datenbank in Management Studio beispielsweise wird der übersetzte Name nicht angezeigt, selbst wenn Sie den Gebietsschemabezeichner für die Verbindung angeben. Die von Management Studio für die Herstellung einer Verbindung mit Analysis Services verwendete API liest die `Language`-Eigenschaft nicht.  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektnamenamen, und wählen Sie **Datenbank bearbeiten** aus, um den Datenbank-Designer zu öffnen.  
  
2.  Geben Sie unter „Übersetzungen“ die Zielsprache (wird in eine LCID aufgelöst), die übersetzte Beschriftung und die übersetzte Beschreibung an. Die Sprachenliste ist überall in Analysis Services konsistent, egal, ob Sie die Serversprache in Management Studio festlegen oder die Übersetzungsüberschreibung zu einem einzelnen Attribut hinzufügen.  
  
3.  Legen Sie auf der Eigenschaftenseite der Datenbank für `Language` die gleiche LCID fest, die Sie für die Übersetzung angegeben haben. Legen Sie gegebenenfalls auch die `Collation`-Eigenschaft fest, wenn der Standardwert nicht mehr sinnvoll ist.  
  
4.  Erstellen Sie die Datenbank, und stellen Sie sie bereit.  
  
## <a name="resolving-translations"></a>Auflösung von Übersetzungen  
 Wenn eine Clientanwendung einen Gebietsschemabezeichner anfordert, versucht die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz, Daten und Metadaten für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekte in die nächste übereinstimmende LCID aufzulösen. Wenn die Clientanwendung keine Standardsprache und auch nicht den neutralen Gebietsschemabezeichner (0) oder den standardmäßigen Prozesssprachbezeichner (1024) vorgibt, dann verwendet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Standardsprache für die Instanz, um Daten und Metadaten für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekte zurückzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Globalisierungs Szenarien für Analysis Services-multidimensionalen](globalization-scenarios-for-analysis-services-multiidimensional.md)   
 [Sprachen und Sortierungen &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md)   
 [Festlegen oder Ändern der Spalten Sortierung](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Tipps und Best Practices für die Globalisierung &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md)  
  
  
