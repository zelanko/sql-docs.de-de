---
title: Rendern von HTML (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cf559b0a-499a-4d74-b520-b382b87e0b17
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 2776ccbb78346ad6243e5b6a4ed1e7c5827d31bf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157831"
---
# <a name="rendering-to-html-report-builder-and-ssrs"></a>Rendern in das HTML-Format (Berichts-Generator und SSRS)
  Die HTML-Renderingerweiterung rendert einen Bericht im HTML-Format. Die Renderingerweiterung kann außerdem vollständige HTML-Seiten oder HTML-Fragmente zum Einbetten in andere HTML-Seiten erstellen. HTML wird stets mit UTF-8-Codierung erstellt.  
  
 Die HTML-Renderingerweiterung ist die Standardrenderingerweiterung für Berichte, die mit einem Browser angezeigt werden (auch bei der Ausführung im Berichts-Manager).  
  
 Die HTML-Renderingerweiterung ist die Standardrenderingerweiterung für Berichte, die mit einem Browser angezeigt werden (auch bei der Ausführung im Berichts-Manager). Die HTML-Renderingerweiterung kann HTML als Fragment oder als vollständiges HTML-Dokument rendern. Falls HTML ein Fragment ist die `HEAD`, `HTML`, und `BODY` -Tag des HTML-Dokuments entfernt. Nur der Inhalt des `BODY`-Tags wird gerendert. Dies ist hilfreich beim Einbetten des HTML-Codes in den von einer anderen Anwendung erstellten HTML-Code.  
  
 In einigen Szenarien können mit Berichtsparametern Script-Injection-Angriffe gestartet werden, wenn Berichte in HTML gerendert werden. Weitere Informationen zum Sichern von Berichten finden Sie unter [Sichere Berichte und Ressourcen](../security/secure-reports-and-resources.md).  
  
 Weitere Informationen zu Browsern finden Sie unter [Planung für Reporting Services und Power View-Browserunterstützung &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="RenderingMHTML"></a> Rendern in das MHTML-Format  
 Die HTML-Renderingerweiterung kann Berichte im MHTML-Format (MIME Encapsulation of Aggregate HTML Documents) rendern. MHTML erweitert HTML, um codierte Objekte in das HTML-Dokument einzubetten, z. B. Bilder. Mit der MHTML-Renderingerweiterung können Sie Ressourcen wie Bilder, Dokumente oder andere Binärdateien als MIME-Strukturen (Multipurpose Internet Mail Extensions) in den Berichts-HTML-Code in einer einzelnen Datei einbetten. Daneben sind MHTML-Berichte zur Einbettung in E-Mail-Nachrichten geeignet, da alle Ressourcen in den Bericht eingeschlossen sind. Zwar rendert eigentlich die HTML-Renderingerweiterung MHTML, aber diese Funktion kann auch als MHTML-Renderingerweiterung bezeichnet werden.  
  
 ![Pfeilsymbol mit dem Link „Zurück zum Anfang“](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol mit dem Link „Zurück zum Anfang“") [Zurück zum Anfang](#BackToTop)  
  
##  <a name="BrowserSupport"></a> Browserunterstützung  
 Diese Renderingerweiterung unterstützt die folgenden Browserversionen:  
  
-   Internet Explorer 5.5 und höher  
  
-   Firefox 1.5 und höher  
  
-   Safari 3.0 und höher  
  
 Aufgrund von browserübergreifenden Überlegungen kann der gerenderte Bericht je nach Browser leicht unterschiedlich ausfallen. So enthält z. B. das Textfeld die Eigenschaft „WritingMode“. Diese Eigenschaft wird in Firefox nicht unterstützt.  
  
 ![Pfeilsymbol mit dem Link „Zurück zum Anfang“](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol mit dem Link „Zurück zum Anfang“") [Zurück zum Anfang](#BackToTop)  
  
##  <a name="HTMLSpecificRenderingRules"></a> HTML-spezifische Renderingregeln  
 Die folgenden HTML-spezifischen Regeln werden beim Rendern angewendet:  
  
-   Der Renderer erstellt eine HTML-Tabellenstruktur mit allen Elementen in jeder `ReportItems`-Auflistung, falls mehr als eine vorhanden ist.  
  
-   Jedes Element innerhalb der Tabellenstruktur nimmt eine einzelne Zelle ein.  
  
-   Leere Zellen werden so weit wie möglich reduziert, um die Größe der HTML-Datei zu reduzieren.  
  
-   Eine Reihe leerer Zellen wird dem oberen Rand und eine weitere Spalte dem linken Rand hinzugefügt, um die Geschwindigkeit, mit der Browser die Tabelle rendern können, zu erhöhen.  
  
-   Tabellenzeilen oder -spalten, die keine Elemente, sondern nur Lücken zwischen Elementen enthalten, erhalten eine feste Breite und Höhe.  
  
-   Allen anderen Zeilen und Spalten können abhängig von der Größe der einzelnen Berichtselemente zunehmen.  
  
-   Alle Koordinaten und Berichtselementgrößen werden in Millimeter konvertiert. Alle anderen Größen, einschließlich der Stileigenschaften, behalten ihre ursprünglichen Einheiten bei. Größen- und Positionsunterschiede, die kleiner als 0,2 mm sind, werden als 0 mm behandelt.  
  
 ![Pfeilsymbol mit dem Link „Zurück zum Anfang“](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol mit dem Link „Zurück zum Anfang“") [Zurück zum Anfang](#BackToTop)  
  
##  <a name="Interactivity"></a> Interaktivität  
 Einige interaktive Elemente werden in HTML unterstützt. Im Folgenden werden spezifische Funktionsweisen beschrieben.  
  
### <a name="show-and-hide"></a>Einblenden und Ausblenden  
 Ein Berichtselement, das ein- und ausgeblendet werden kann, wird mit einem Bild zum Umschalten (+/-) gerendert. Auf dieses Element kann geklickt werden. Wenn auf das Element geklickt wird, erfolgt ein Rückruf an den Server, um die Ausgabe mit dem geänderten aktuellen Ansichtsstatus erneut zu rendern.  
  
### <a name="document-map"></a>Dokumentstruktur  
 Dokumentstrukturbezeichnungen werden gerendert und sind navigierbar. Verwenden Sie dazu die Dokumentstruktur im Steuerelement für den Viewer. Für ausgelassene Datenbereichskopfzeilen werden Bezeichnungen auf der ersten untergeordneten Zelle gerendert. Wenn keine untergeordnete Zelle vorhanden ist, wird die Bezeichnung auf dem untergeordneten Element gerendert, das ihm vorausgeht.  
  
### <a name="bookmarks"></a>Lesezeichen  
 Lesezeichenlinks werden gerendert und als Links angezeigt. Lesezeichenziele werden gerendert. Die Navigation zu diesen Zielen erfolgt durch Klicken auf die Lesezeichenlinks. Beim Klicken auf einen Lesezeichenlink springt der Bericht zum ersten Auftreten der Ziellesezeichenbezeichnung, sofern möglich. Im Browser wird ein Bildlauf durchgeführt, sodass sich der Lesezeichenlink oben im Fenster befindet. HTML-Anchortags (\<a>) werden verwendet, um Lesezeichenziele zu markieren.  
  
### <a name="interactive-sorting"></a>Interaktives Sortieren  
 Bei einem Textfeld mit benutzerdefinierter Sortierung rendert die HTML-Renderingerweiterung die Sortiersymbole im Textfeld rechts vom Inhalt. Wenn ein Bericht ein Textfeld mit benutzerdefinierter Sortierung enthält, wird JavaScript gerendert, was zu einem Postback zum Server führt, wenn das Sortiersymbol angeklickt wird.  
  
### <a name="hyperlinks-and-drillthrough"></a>Links und Drillthroughlinks  
 Hyperlinks und Drillthroughlinks werden in Berichtselementen als Hyperlinks gerendert. Dabei wird das HTML-Anchortag (\<a>) um das Element verwendet, für das sie definiert sind.  
  
### <a name="search"></a>Suchen  
 Die Suchfunktion ermöglicht es Benutzern, nach einer Textzeichenfolge innerhalb des Berichts zu suchen.  
  
 Zusätzliche Suchfunktionen werden vom ReportViewer Web Forms-Steuerelement bereitgestellt.  
  
 ![Pfeilsymbol mit dem Link „Zurück zum Anfang“](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol mit dem Link „Zurück zum Anfang“") [Zurück zum Anfang](#BackToTop)  
  
##  <a name="DeviceInfo"></a> Geräteinformationseinstellungen  
 Sie können einige Standardeinstellungen für diesen Renderer ändern, einschließlich des Modus für das Rendern. Ändern Sie dazu die Geräteinformationseinstellungen. Weitere Informationen finden Sie unter [HTML Device Information Settings](../html-device-information-settings.md).  
  
 ![Pfeilsymbol mit dem Link „Zurück zum Anfang“](../../2014-toc/media/uparrow16x16.gif "Pfeilsymbol mit dem Link „Zurück zum Anfang“") [Zurück zum Anfang](#BackToTop)  
  
## <a name="see-also"></a>Siehe auch  
 [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Renderingverhalten (Berichts-Generator und SSRS)](../report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen &#40;Berichts-Generator und SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md)   
 [Rendern von Berichtselementen (Berichts-Generator und SSRS)](../report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
