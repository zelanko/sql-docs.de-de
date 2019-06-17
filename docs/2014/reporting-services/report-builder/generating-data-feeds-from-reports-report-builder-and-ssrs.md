---
title: Generieren von Datenfeeds aus Berichten (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4e00789f-6967-42e5-b2b4-03181fdb1e2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d7afc644d96c895164aa954cc4813762cc4ef32d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66107839"
---
# <a name="generating-data-feeds-from-reports-report-builder-and-ssrs"></a>Generieren von Datenfeeds aus Berichten (Berichts-Generator und SSRS)
  Die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Atom-Renderingerweiterung generiert ein Atom-Dienstdokument, in dem die aus einem Bericht und aus den Datenbereichen in einem Bericht verfügbaren Datenfeeds aufgeführt sind. Mit dieser Erweiterung generieren Sie Atom-kompatible Datenfeeds, die von Anwendungen gelesen bzw. zwischen Anwendungen ausgetauscht werden können, die aus Berichten generierte Datenfeeds nutzen können. Sie können z. B. die Atom-Renderingerweiterung zum Generierten von Datenfeeds verwenden, die dann im [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Client verwendet werden können.  
  
 Im Atom-Dienstdokument ist mindestens ein Datenfeed für jeden Datenbereich in einem Bericht aufgeführt. Abhängig vom Typ des Datenbereichs und den darin angezeigten Daten könnte [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] mehrere Datenfeeds aus einem Datenbereich generieren. Eine Matrix oder ein Diagramm kann beispielsweise mehrere Datenfeeds bereitstellen. Wenn die Atom-Renderingerweiterung das Atom-Dienstdokument erstellt, wird für jeden Datenfeed ein eindeutiger Bezeichner erstellt. Sie verwenden den Bezeichner in der URL, um auf den Inhalt des Datenfeeds zuzugreifen.  
  
 Die Atom-Renderingerweiterung generiert Daten für einen Datenfeed auf ähnliche Weise, wie die CSV-(Comma-Separated Value-)Renderingerweiterung Daten in eine CSV-Datei rendert. Wie eine CSV-Datei entspricht ein Datenfeed einer vereinfachten Darstellung der Berichtsdaten. Beispiel: In einer Tabelle mit einer Zeilengruppe, in der die Verkäufe innerhalb einer Gruppe addiert werden, wird die Summe in jeder Datenzeile wiederholt, und es gibt keine separate Zeile, die nur die Summe enthält.  
  
 Atom-Dienstdokumente und -Datenfeeds können mit dem Berichts-Manager, Berichtsserver oder einer mit [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]integrierten SharePoint-Website generiert werden.  
  
 Atom bezieht sich auf zwei verwandte Standards. Das Atom-Dienstdokument entspricht der RFC 5023 APP-(Atom Publishing Protocol-)Spezifikation und die Datenfeeds der RFC 4287 ASF-Protokollspezifikation für das Atom-Veröffentlichungsformat.  
  
 Die folgenden Abschnitte enthalten zusätzliche Informationen zur Verwendung der Atom-Renderingerweiterung:  
  
 [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="ReportDataAsDataFeeds"></a> Berichte als Datenfeeds  
 Sie können einen Produktionsbericht als Datenfeed exportieren oder einen Bericht erstellen, dessen Hauptzweck in der Bereitstellung in Daten in Form von Datenfeeds für Anwendungen besteht. Durch die Verwendung von Berichten als Datenfeed haben Sie eine zusätzliche Möglichkeit, Daten für Anwendungen bereitzustellen, auf die nicht problemlos über Clientdatenanbieter zugegriffen werden kann, oder wenn Sie es vorziehen, die Komplexität der Datenquelle zu verbergen und die Datennutzung zu vereinfachen. Ein weiterer Vorteil der Verwendung von Berichtsdaten als Datenfeed besteht darin, dass Sie Funktionen von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] wie den Berichts-Manager, Sicherheits- und Planungsfunktionen sowie Berichtsmomentaufnahmen zur Verwaltung der Berichte verwenden können, die Datenfeeds bereitstellen.  
  
 Um die Atom-Renderingerweiterung optimal nutzen zu können, sollten Sie verstehen, wie der Bericht in Datenfeeds gerendert wird. Bei Verwendung vorhandener Berichte ist es hilfreich, im Voraus zu wissen, welche Datenfeeds aus den Berichten generiert werden. Wenn Sie Berichte speziell zur Verwendung als Datenfeeds erstellen, haben Sie die Möglichkeit, die enthaltenen Daten und das Berichtslayout genau auf eine optimale Nutzung des Datenfeeds abzustimmen, was einen erheblichen Vorteil bietet.  
  
 Weitere Informationen finden Sie unter [Generieren von Datenfeeds aus Berichten &#40;Berichts-Generator und SSRS&#41;](generate-data-feeds-from-a-report-report-builder-and-ssrs.md).  
  

  
##  <a name="AtomServiceDocument"></a> Atom-Dienstdokument (ATOMSVC-Datei)  
 In einem Atom-Dienstdokument ist eine Verbindung mit mindestens einem Datenfeed angegeben. Bei der Verbindung handelt es sich mindestens um eine einfache URL für den Datendienst, der den Feed erzeugt.  
  
 Wenn Sie Berichtsdaten mit der Atom-Renderingerweiterung rendern, sind im Atom-Dienstdokument die für einen Bericht verfügbaren Datenfeeds aufgeführt. Im Dokument ist mindestens ein Datenfeed für jeden Datenbereich im Bericht enthalten. Tabellen und Messgeräte generieren jeweils nur einen Datenfeed, während Matrizen, Listen und Diagramme je nach den darin angezeigten Daten mehrere Datenfeeds generieren könnten.  
  
 Das folgende Diagramm zeigt einen Bericht, in dem zwei Tabellen und ein Diagramm verwendet werden.  
  
 ![RS_Atom_TableAndChartDataFeeds](../media/rs-atom-tableandchartdatafeeds.gif "RS_Atom_TableAndChartDataFeeds")  
  
 Das aus diesem Bericht generierte Atom-Dienstdokument enthält drei Datenfeeds: einen für jede Tabelle und einen für das Diagramm.  
  
 Die Matrixdatenbereiche könnten abhängig von der Struktur der Matrix mehr als einen Datenfeed aufweisen. Das folgende Diagramm zeigt einen Bericht mit einer Matrix, die zwei Datenfeeds generiert.  
  
 ![RS_Atom_PeerDynamicColumns](../media/rs-atom-peerdynamiccolumns.gif "RS_Atom_PeerDynamicColumns")  
  
 Das aus diesem Bericht generierte Atom-Dienstdokument enthält zwei Datenfeeds: einen für jede der dynamischen Peerspalten: „Territory“ und „Year“. Das folgende Diagramm veranschaulicht den Inhalt der einzelnen Datenfeeds.  
  
 ![RS_Atom_PeerDynamicDataFeeds](../media/rs-atom-peerdynamicdatafeeds.gif "RS_Atom_PeerDynamicDataFeeds")  
  

  
##  <a name="DataFeeds"></a> Datenfeeds  
 Bei einem Datenfeed handelt es sich um eine XML-Datei mit einem konsistenten Tabellenformat, das sich nie ändert, und veränderbaren Daten, die mit jeder Berichtsausführung variieren können. Die von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] generierten Datenfeeds verfügen über das gleiche Format wie die von ADO.NET Data Services generierten Feeds.  
  
 Ein Datenfeed enthält zwei Abschnitte: Header und Daten. Die Atom-Spezifikation definiert die Elemente in den beiden Abschnitten. Der Header enthält Informationen wie das für die Datenfeeds zu verwendende Zeichencodierungsschema.  
  
### <a name="header-section"></a>Headerabschnitt  
 Im folgenden XML-Code wird der Headerabschnitt eines Datenfeeds veranschaulicht.  
  
 `<?xml version="1.0" encoding="utf-8" standalone="yes"?><feed xmlns:d="https://schemas.microsoft.com/ado/2007/08/dataservices" xmlns:m="https://schemas.microsoft.com/ado/2007/08/dataservices/metadata" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<title type="text"></title>`  
  
 `<id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166321</id>`  
  
 `<updated>2009-05-08T23:09:58Z</updated>`  
  
### <a name="data-section"></a>Datenabschnitt  
 Der Datenabschnitt der Datenfeeds enthält ein <`entry`>-Element für jede Zeile im vereinfachten von der Atom-Renderingerweiterung generierten Rowset.  
  
 Das folgende Diagramm zeigt einen Bericht, der Gruppen und Gesamtsummen verwendet.  
  
 ![RS_Atom_ProductSalesSummaryCircledValues](../media/rs-atom-productsalessummarycircledvalues.gif "RS_Atom_ProductSalesSummaryCircledValues")  
  
 Das folgende XML zeigt ein <`entry`>-Element aus diesem Bericht in einem Datenfeed. Beachten Sie, dass die <`entry`>-Element enthält, die Gesamtsummen der Verkäufe und Bestellungen der Gruppe sowie die Gesamtsummen der Verkäufe und Bestellungen aller Gruppen. Die <`entry`>-Element enthält alle Werte im Bericht.  
  
 `<entry><id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166322</id><title type="text"></title><updated>2009-05-08T23:09:58Z</updated><author /><content type="application/xml"><m:properties>`  
  
 `<d:ProductCategory_Value>Accessories</d:ProductCategory_Value>`  
  
 `<d:OrderYear_Value m:type="Edm.Int32">2001</d:OrderYear_Value>`  
  
 `<d:SumLineTotal_Value m:type="Edm.Decimal">20235.364608</d:SumLineTotal_Value>`  
  
 `<d:SumOrderQty_Value m:type="Edm.Int32">1003</d:SumOrderQty_Value>`  
  
 `<d:SumLineTotal_Total_2_1 m:type="Edm.Decimal">1272072.883926</d:SumLineTotal_Total_2_1>`  
  
 `<d:SumOrderQty_Total_2_1 m:type="Edm.Double">61932</d:SumOrderQty_Total_2_1>`  
  
 `<d:SumLineTotal_Total_2_2 m:type="Edm.Decimal">109846381.399888</d:SumLineTotal_Total_2_2>`  
  
 `<d:SumOrderQty_Total_2_2 m:type="Edm.Double">274914</d:SumOrderQty_Total_2_2></m:properties></content>`  
  
 `</entry>`  
  
### <a name="working-with-data-feeds"></a>Arbeiten mit Datenfeeds  
 Alle vom Bericht generierten Datenfeeds enthalten die Berichtselemente, die zum Bereich des übergeordneten Elements des Datenbereichs gehören, aus dem die Datenfeeds generiert werden. integrierten SharePoint-Website generiert werden. Angenommen, ein Bericht enthält mehrere Tabellen und ein Diagramm. Textfelder im Hauptteil des Berichts enthalten beschreibenden Text zu jedem Datenbereich. Jeder Eintrag in jedem vom Bericht generierten Datenfeed enthält den Wert des Textfelds. Lautete der Text z. B. "Diagramm zur Anzeige der durchschnittlichen Umsätze nach Vertriebsgebiet und Monat", wäre dieser Text in jeder Zeile aller drei Datenfeeds enthalten.  
  
 Wenn das Berichtslayout hierarchische Datenbeziehungen, z. B. geschachtelte Datenbereiche, umfasst, sind diese Beziehungen Teil des vereinfachten Rowsets der Berichtsdaten.  
  
 Die Datenzeilen für geschachtelte Datenbereiche sind in der Regel breit, insbesondere, wenn die geschachtelten Tabellen und die Matrizen Gruppen und Gesamtsummen beinhalten. Es ist u. U. hilfreich, den Bericht in einen Datenfeed zu exportieren und diesen anzuzeigen, um sicherzustellen, dass die generierten Daten Ihren Erwartungen entsprechen.  
  
 Wenn die Atom-Renderingerweiterung das Atom-Dienstdokument erstellt, wird für den Datenfeed ein eindeutiger Bezeichner erstellt. Sie verwenden den Bezeichner in der URL, um den Inhalt des Datenfeeds anzuzeigen. Oben gezeigte Beispiel Atom-dienstdokument enthält die URL <http://ServerName/ReportServer?%2fProduct+Sales+Summary&rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=xAx0x1>". In der URL ist der Bericht (Product Sales Summary), das Atom-Renderingformat (ATOM) und der Name des Datenfeeds (xAx0x1) angegeben.  
  
 Die Namen der Berichtselemente entsprechen den in der Berichtsdefinitionssprache (Report Definition Language, RDL) verwendeten Standardnamen, die häufig weder intuitiv noch einfach zu erinnern sind. Der Standardname der ersten in einen Bericht eingefügten Matrix lautet beispielsweise "Tablix 1". Die Datenfeeds verwenden diese Namen.  
  
 Sie können mithilfe der DataElementName-Eigenschaft des Datenbereichs Anzeigenamen bereitstellen, um die Arbeit mit Datenfeeds zu vereinfachen. Wenn Sie einen Wert für DataElementName angeben der Datenfeed Unterelement <`d`> wird mit ist es den Standard-datenbereichsnamen. Z. B., wenn der Standardname einer Datenbereiche Tablix1 und DataElementName SalesByTerritoryYear festgelegt wurde und dann die <`d`> in den Daten Feed SalesByTerritoryYear verwendet. Wenn der Datenbereich, wie der oben beschriebene Matrixbericht, zwei Datenfeeds aufweist, lauten die in den Datenfeeds verwendeten Namen SalesByTerritoryYear _Territory und SalesByTerritoryYear _Year.  
  
 Wenn Sie die im Bericht und die im Datenfeed angezeigten Daten vergleichen, werden Sie möglicherweise einige Unterschiede feststellen. In Berichten werden häufig formatierte numerische und Datums-/Uhrzeitangaben angezeigt, wohingegen der Datenfeed unformatierte Daten enthält.  
  
 Ein Datenfeed wird mit der Dateinamenerweiterung .atom gespeichert. Sie können einen Text- oder XML-Editor (z. B. Editor oder XML-Editor) verwenden, um die Dateistruktur und den Inhalt anzuzeigen.  
  

  
##  <a name="FlatteningReportData"></a> Vereinfachen von Berichtsdaten  
 Der Atom-Renderer stellt Berichtsdaten als vereinfachte Rowsets in einem XML-Format bereit. Die Regeln zum Vereinfachen von Datentabellen sind bis auf einige Ausnahmen mit denen des CSV-Renderers identisch:  
  
-   Elemente im Bereich werden bis auf Detailebene vereinfacht. Die Textfelder auf oberster Ebene werden im Gegensatz zum CSV-Renderer in jedem in den Datenfeed geschriebenen Eintrag angezeigt.  
  
-   Berichtsparameterwerte werden in jeder Ausgabezeile gerendert.  
  
 Hierarchische und gruppierte Daten müssen vereinfacht werden, damit sie im Atom-kompatiblen Format dargestellt werden können. Die Renderingerweiterung vereinfacht den Bericht zu einer Baumstruktur, die die geschachtelten Gruppen innerhalb des Datenbereichs darstellt. So vereinfachen Sie den Bericht:  
  
-   Eine Zeilenhierarchie wird vor einer Spaltenhierarchie vereinfacht.  
  
-   Elemente der Zeilenhierarchie werden vor Elementen der Spaltenhierarchie in den Datenfeed gerendert.  
  
-   Spalten werden wie folgt sortiert: Textfelder im Hauptteil von links nach rechts und von oben nach unten, gefolgt von Datenbereichen von links nach rechts und von oben nach unten.  
  
-   Innerhalb eines Datenbereichs werden die Spalten wie folgt sortiert: Eckelemente, Zeilenhierarchieelemente, Spaltenhierarchieelemente und Zellen  
  
-   Peerdatenbereiche sind Datenbereiche oder dynamische Gruppen, die einen allgemeinen Datenbereich oder einen dynamischen Vorgänger gemeinsam nutzen. Peerdaten werden durch Verzweigen der vereinfachten Struktur identifiziert.  
  
 Weitere Informationen finden Sie unter [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  

  
##  <a name="AtomRendering"></a> Atom-Renderingregeln  
 Beim Rendern eines Datenfeeds ignoriert die Atom-Renderingerweiterung die folgenden Informationen:  
  
-   Formatierung und Layout  
  
-   Seitenkopf  
  
-   Seitenfuß  
  
-   Benutzerdefinierte Berichtselemente  
  
-   Rechtecke  
  
-   Linien  
  
-   Bilder  
  
-   Automatische Teilergebnisse  
  
 Die verbleibenden Berichtselemente werden von oben nach unten und dann von links nach rechts sortiert. Anschließend wird jedes Element in eine Spalte gerendert. Enthält der Bericht geschachtelte Datenelemente, wie Listen oder Tabellen, werden die übergeordneten Elemente in jeder Zeile wiederholt.  
  
 In der folgenden Tabelle wird die Darstellung von Berichtselementen beim Rendern angegeben:  
  
|Element|Renderingverhalten|  
|----------|------------------------|  
|Tabelle|Das Rendering erfolgt durch Erweitern der Tabelle und Erstellen einer Zeile und Spalte für jede Zeile und Spalte auf der untersten Detailebene. Teilergebniszeilen und -spalten weisen keine Zeilen- und Spaltenüberschriften auf. Drillthroughberichte werden nicht unterstützt.|  
|Matrix|Das Rendering erfolgt durch Erweitern der Matrix und Erstellen einer Zeile und Spalte für jede Zeile und Spalte auf der untersten Detailebene. Teilergebniszeilen und -spalten weisen keine Zeilen- und Spaltenüberschriften auf.|  
|Liste|Für jede Detailzeile oder Instanz in der Liste wird ein Datensatz gerendert.|  
|Unterbericht|Das übergeordnete Element wird für jede Instanz des Inhalts wiederholt.|  
|Diagramm|Es wird ein Datensatz mit allen Diagrammbezeichnungen für jeden Diagrammwert gerendert. Bezeichnungen aus Reihen und Kategorien in Hierarchien werden vereinfacht und in die Zeile für einen Diagrammwert eingeschlossen.|  
|Datenbalken|Wird wie ein Diagramm gerendert. Ein Datenbalken enthält normalerweise keine Hierarchien oder Bezeichnungen.|  
|Sparkline|Wird wie ein Diagramm gerendert. Eine Sparkline enthält normalerweise keine Hierarchien oder Bezeichnungen.|  
|Messgerät|Wird als einzelner Datensatz mit dem Minimal- und Maximalwert der linearen Skala, dem Start- und Endwert des Bereichs und dem Wert des Zeigers gerendert.|  
|Indikator|Es wird als einzelnes Element mit dem Namen des aktiven Zustands, den verfügbaren Zuständen und dem Datenwert als Attribute gerendert.|  
|Karte|Generiert einen Datenfeed für jeden Kartendatenbereich. Wenn mehrere Kartenebenen den gleichen Datenbereich verwenden, sind diese alle im Datenfeed enthalten. Der Datenfeed umfasst einen Datensatz mit den Bezeichnungen und Werten der einzelnen Kartenelemente der Kartenebene.|  
  

  
##  <a name="DeviceInfo"></a> Geräteinformationseinstellungen  
 Sie können einige Standardeinstellungen für diesen Renderer ändern, einschließlich des zu verwendenden Codierungsschemas. Weitere Informationen finden Sie unter [ATOM Device Information Settings](../atom-device-information-settings.md).  
  

  
## <a name="see-also"></a>Siehe auch  
 [Exportieren als CSV-Datei &#40;Berichts-Generator und SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md)   
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](export-reports-report-builder-and-ssrs.md)  
  
  
