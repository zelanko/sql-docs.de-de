---
title: Ausdruck (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10040"
- sql12.rtp.rptdesigner.expression.f1
helpviewer_keywords:
- Expression dialog box [Reporting Services]
ms.assetid: e6c74ccb-4594-4d4f-b958-618d710e34eb
caps.latest.revision: 63
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 747943591907b1025250e3554270e9dda14d3e51
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325640"
---
# <a name="expression-dialog-box"></a>Ausdruck (Dialogfeld)
  Verwenden der **Ausdruck** Dialogfeld schreiben [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] -Ausdrücke für berichtselementeigenschaften-Elementeigenschaften. Mit Ausdrücken können Sie zahlreiche Eigenschaften wie Farbe, Schriftart und Rahmen festlegen. Zur Laufzeit werden die Ausdrücke vom Berichtsprozessor ausgewertet, und das Ergebnis wird durch den Wert der Eigenschaft ersetzt.  
  
 Ein Ausdruck kann einfach oder komplex sein. Sie können einfache Ausdrücke direkt in einem Textfeld auf der Entwurfsoberfläche oder in einem Dialogfeld eingeben. Verwenden Sie zum Erstellen komplexer Ausdrücke das **Ausdruck** Dialogfeld. Sie können jeweils einen Ausdruck erstellen. Weitere Informationen finden Sie unter [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md).  
  
 Zum Öffnen des Dialogfelds **Ausdruck** klicken Sie in Dialogfeldern auf die Ausdrucksschaltfläche (**fx**), oder wählen Sie die Option **Ausdruck** über das Kontextmenü oder die Dropdownlisten im Bereich „Eigenschaften“ aus. Weitere Informationen finden Sie unter [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](report-design/expression-uses-in-reports-report-builder-and-ssrs.md).  
  
 Das Dialogfeld **Ausdruck** enthält ein Codefenster, eine Kategoriestruktur, Kategorieelemente, einen Beschreibungsbereich sowie einen Beispielbereich.  
  
 Das Dialogfeld **Ausdruck** ist kontextbezogen. Die Kategorieelemente und Beschreibungen verändern sich je nach verwendeter Ausdruckskategorie. Es unterstützt IntelliSense, Anweisungsvervollständigungen, Funktionsaufrufbeispiele sowie Syntaxfarben zur schnelleren Erkennung von Syntaxfehlern.  
  
## <a name="expression-constructs"></a>Ausdruckskonstrukte  
 Ausdrücke beginnen mit einem Gleichheitszeichen (=) und können Konstanten, Literale, Operatoren und Verweise auf integrierte Felder, Auflistungen und Funktionen, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Laufzeitbibliotheksfunktionen, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-CLR-Klassen (Common Language Runtime) sowie benutzerdefinierte Funktionen enthalten. Die folgende Liste beschreibt die Kategorien und Werte, die Sie einem Ausdruck hinzufügen können.  
  
 **Ausdruck festlegen für:***\<PropertyName >*   
 Der Name der Eigenschaft, für die Sie einen Ausdruck definieren. Sie können diese Einstellung auch im Eigenschaftenfenster nach dem Namen vornehmen.  
  
 **Konstanten**  
 Stellt für Eigenschaften, die auf Konstanten basieren, eine Liste vordefinierter gültiger Werte für diese Eigenschaft bereit. Beispielsweise zeigt eine Eigenschaft auf Grundlage der Farbe gültige Farbnamen an. Für eine Eigenschaft, die einen booleschen Datentyp darstellt, lauten die Werte `True` und `False`.  
  
 Nicht alle Elemente, die Ausdrücke unterstützen, können auf eine Konstante festgelegt werden. Wenn eine Eigenschaft nicht auf einen konstanten Wert festgelegt werden kann, ist dies in der Beschreibung angegeben.  
  
 **Integrierte Felder**  
 Bietet eine Liste der in der globalen Auflistung enthaltenen Elemente, die Sie in einem Ausdruck verwenden können. Einige Auflistungen werden nur unterstützt, nachdem der Bericht auf dem Server veröffentlicht wurde. Weitere Informationen finden Sie unter [Integrierte globale Werte und Benutzerverweise &#40;Berichts-Generator und SSRS&#41;](report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md).  
  
 **Parameter**  
 Bietet eine Liste von Berichtsparametern.  
  
 **Felder (**  *\<Ausgewähltes Dataset >* **)**  
 Zeigt die Liste von Feldern für das in der Datasets-Kategorie ausgewählte Dataset an. Doppelklicken Sie auf ein Feld, um es in das Feld **Ausdruck** zu kopieren.  
  
 **Datasets**  
 Bietet eine Liste der verfügbaren Datasets und zeigt die Felder an, die Mitglied des Datasets sind.  
  
 **Variablen**  
 Zeigt eine Liste von Berichtsvariablen an. Weitere Informationen finden Sie unter [Verweise auf Berichts- und Gruppenvariablenauflistungen &#40;Berichts-Generator und SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md).  
  
 **Operatoren**  
 Zeigt die Operatoren an, die Sie in einer Berechnung oder bei einer Zeichenfolgebearbeitung verwenden können. Weitere Informationen finden Sie unter [Operatoren in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](report-design/operators-in-expressions-report-builder-and-ssrs.md).  
  
 **Allgemeine Funktionen**  
 Zeigt allgemeine, nach Typ gruppierte Funktionen an. Wenn Sie im Bereich Element eine Funktion auswählen, werden eine Beschreibung und ein Beispiel angezeigt.  
  
 Zu den häufig verwendeten Funktionen gehören integrierte Berichts- und Aggregationsfunktionen, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Laufzeitbibliotheksfunktionen und [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Common Language Runtime (CLR)-Klassen im <xref:System.Math>- und <xref:System.Convert>-Namespace. Sie können auch Verweise auf CLR-Klassen und externe Assemblys hinzufügen, die nicht in der Kategorieliste angezeigt werden. Weitere Informationen finden Sie unter [Benutzerdefinierter Code und Assemblyverweise in Ausdrücken in Berichts-Designer &#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
## <a name="options"></a>Tastatur  
 Codefenster  
 Im oben angezeigten Codefenster können Sie einen Ausdruck eingeben. Wenn Sie das Dialogfeld **Ausdruck** öffnen, enthält das Codefenster den Ausdruck. Sie können den Ausdruck ersetzen oder bearbeiten. Sie können Funktionsaufrufe, Operatoren, Konstanten, Felder, Parameter, Elemente aus den globalen Auflistungen sowie Verweise auf benutzerdefinierten Code hinzufügen. Das Codefenster zeigt Ihre Änderungen sofort an.  
  
 Ein geschwungener roter Unterstrich signalisiert einen Syntaxfehler. Zeigen Sie auf den unterstrichenen Text, um die Fehlermeldung einzublenden.  
  
 Wenn Sie Begriffe aus globalen Auflistungen, gefolgt von einem Interpunktionstrennzeichen, eingeben, wird eine Dropdownliste mit verfügbaren Mitgliedern oder Eigenschaften angezeigt. Geben Sie über die Dropdownliste die ersten Zeichen ein, gefolgt von einem Tabulator, um die Auswahl automatisch auszufüllen.  
  
 Wenn Sie einen Funktionsnamen, gefolgt von einer linken Klammer, eingeben, wird eine QuickInfo mit Informationen zu den Parametern und Rückgabewerten der Funktion angezeigt.  
  
 **Kategorie**  
 Zeigt Kategorien von Ausdrücken an. Durch Auswahl einer Kategorie wird ein Kontext für die Erstellung eines Ausdrucks bereitgestellt und die Liste der gültigen Werte im Bereich Element geändert. Z. B. für einen Ausdruck für einen Textfeldwert erweitern Sie allgemeine Funktionen, und wählen Sie Aggregatfunktionen anzuzeigende `Avg`, `Count`, und andere Funktionen in der **Element** Bereich.  
  
 **Element**  
 Zeigt die Liste der gültigen Felder für die ausgewählte Kategorie an. Doppelklicken Sie auf ein Element, um den Ausdruckstext für dieses Element an der Einfügemarke im Codefenster hinzuzufügen.  
  
 **Werte**  
 Abhängig von der ausgewählten Kategorie und dem Element enthält der dritte Bereich eine Beschreibung, einen Beispielausdruck oder eine Liste gültiger Werte. Ziehen Sie am Rand des Dialogfelds, um den Beispielbereich zu erweitern.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Formatieren von Zahlen und Datumsangaben &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Parameters Collection References (Report Builder and SSRS) (Verweise auf Parameterauflistungen (Berichts-Generator und SSRS))](report-design/built-in-collections-parameters-collection-references-report-builder.md)   
 [Beispiele für Gruppierungsausdrücke (Berichts-Generator und SSRS)](report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [Beispiele für Filtergleichungen &#40;Berichts-Generator und SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Integrierte Auflistungen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](report-design/built-in-collections-in-expressions-report-builder.md)   
 [Hinzufügen eines Ausdrucks &#40;Berichts-Generator und SSRS&#41;](report-design/add-an-expression-report-builder-and-ssrs.md)  
  
  
