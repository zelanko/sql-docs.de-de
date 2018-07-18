---
title: Fehlerbehandlung in Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data conversion errors [Integration Services]
- errors [Integration Services], data flow components
- lookups [Integration Services]
- errors [Integration Services]
- errors [Integration Services], data flow outputs
- error outputs [Integration Services]
- data flow [Integration Services], errors
- expressions [Integration Services], errors
ms.assetid: c61667b4-25cb-4d45-a52f-a733e32863f4
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ecae86e05bc67275d21d0811d3b1abd642a7e62c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201620"
---
# <a name="error-handling-in-data"></a>Fehlerbehandlung in Daten
  Wenn eine Datenflusskomponente eine Transformation auf Spaltendaten anwendet, Daten aus Quellen extrahiert oder Daten in Ziele lädt, können Fehler auftreten. Fehler treten häufig aufgrund unerwarteter Datenwerte auf. Beispielsweise tritt bei einer Datenkonvertierung ein Fehler auf, weil eine Spalte eine Zeichenfolge anstelle einer Zahl enthält. Beim Einfügen in eine Datenbankspalte kann ein Fehler auftreten, weil die Daten einen date-Datentyp und die Spalte einen numeric-Datentyp aufweist. Ein Ausdruck kann nicht ausgewertet werden, weil ein Spaltenwert Null ist, wodurch sich eine ungültige mathematische Operation ergibt.  
  
 Fehler können in der Regel einer der folgenden Kategorien zugeordnet werden:  
  
-   Datenkonvertierungsfehler, die auftreten, wenn eine Konvertierung zum Verlust signifikanter Ziffern, zum Verlust insignifikanter Ziffern und zum Abschneiden von Zeichenfolgen führt. Datenkonvertierungsfehler treten außerdem auf, wenn die angeforderte Konvertierung nicht unterstützt wird.  
  
-   Fehler bei der Ausdrucksauswertung. Sie treten auf, wenn Ausdrücke, die zur Laufzeit ausgewertet werden, ungültige Vorgänge ausführen oder aufgrund fehlender oder falscher Datenwerte syntaktisch falsch sind.  
  
-   Suchfehler, die auftreten, wenn ein Suchvorgang keine Übereinstimmung in der Nachschlagetabelle findet.  
  
 Viele Datenflusskomponenten unterstützen Fehlerausgaben, mit denen Sie steuern können, wie die Komponente Fehler auf Zeilenebene in ein- und ausgehenden Daten behandelt. Sie geben das Verhalten der Komponente an, wenn Daten abgeschnitten werden oder ein Fehler auftritt, indem Sie Optionen für einzelne Spalten in der Eingabe oder Ausgabe festlegen. Beispielsweise können Sie angeben, dass bei der Komponente ein Fehler auftritt, wenn die Daten für den Kundennamen abgeschnitten werden, dass aber Fehler in einer anderen Spalte, die weniger wichtige Daten enthält, ignoriert werden.  
  
 Die Fehlerausgabe kann mit der Eingabe einer anderen Transformation verbunden werden oder in ein anderes Ziel als die Nichtfehlerausgabe geladen werden. Beispielsweise kann die Fehlerausgabe mit einer Transformation für abgeleitete Spalten verbunden werden, die eine Zeichenfolge für eine leere Spalte bereitstellt.  
  
 Im folgenden Diagramm wird ein einfacher Datenfluss mit einer Fehlerausgabe dargestellt.  
  
 ![Datenfluss mit Fehlerausgabe](../media/mw-dts-11.gif "Datenfluss mit Fehlerausgabe")  
  
 Neben den Datenspalten enthält die Fehlerausgabe die Spalten **ErrorCode** und **ErrorColumn** . Die **ErrorCode** -Spalte gibt den Fehler an, und die **ErrorColumn** -Spalte enthält den Herkunftsbezeichner der Fehlerspalte. Zum Anzeigen der Metadaten dieser Spalten klicken Sie auf den Pfad, der die Fehlerausgabe mit der nächsten Komponente im Datenfluss verbindet. Unter einigen Umständen wird der Wert der **ErrorColumn** -Spalte auf 0 festgelegt. Dies ist der Fall, wenn sich die Fehlerbedingung nicht auf eine einzelne Spalte, sondern auf die gesamte Zeile auswirkt. Beispielsweise tritt dies ein, wenn bei einer Suche in der Transformation für die Suche ein Fehler auftritt.  
  
 Weitere Informationen finden Sie unter [Datenfluss](data-flow.md) und [Integration Services-Pfade](integration-services-paths.md).  
  
 Eine Liste der Fehler, Warnungen und anderen Meldungen in Integration Services finden Sie unter [Fehler- und Meldungsreferenz von Integration Services](../integration-services-error-and-message-reference.md).  
  
## <a name="error-and-truncation-options"></a>Fehler- und Abschneideoptionen  
 Fehler können zwei Kategorien zugeordnet werden: Fehler oder Abschneiden von Daten. Ein Fehler ist ein Hinweis auf ein eindeutiges Problem, und es wird ein NULL-Ergebnis generiert. Hierzu zählen Fehler bei der Datenkonvertierung oder bei der Ausdrucksauswertung. Beispielsweise wird ein Fehler verursacht, wenn eine Zeichenfolge, die Buchstaben enthält, in eine Zahl konvertiert wird. Datenkonvertierungen, Auswertungen von Ausdrücken sowie Zuweisungen von Ausdrucksergebnissen zu Variablen, Eigenschaften und Datenspalten erzeugen aufgrund von unzulässigen Umwandlungen und inkompatiblen Datentypen möglicherweise einen Fehler. Weitere Informationen finden Sie unter [Cast &#40;SSIS-Ausdruck&#41;](../expressions/cast-ssis-expression.md), [Integration Services-Datentypen in Ausdrücken](../expressions/integration-services-data-types-in-expressions.md) und [Integration Services-Datentypen](integration-services-data-types.md).  
  
 Das Abschneiden von Daten ist nicht so schwerwiegend wie ein Fehler. Beim Abschneiden werden Ergebnisse generiert, die verwendbar oder sogar wünschenswert sind. Sie können das Abschneiden von Daten als Fehler oder als zulässige Bedingungen behandeln. Wenn Sie z. B. eine Zeichenfolge mit 15 Zeichen in eine Spalte einfügen, die nur eine Breite von einem Zeichen aufweist, können Sie festlegen, dass die Zeichenfolge abgeschnitten wird.  
  
 Sie können konfigurieren, wie Quellen, Transformationen und Ziele Fehler und das Abschneiden von Daten behandeln. In der folgenden Tabelle werden diese Optionen beschrieben.  
  
|Option|Description|  
|------------|-----------------|  
|Fehler bei Komponente|Bei einem Fehler oder beim Abschneiden von Daten wird der Datenflusstask nicht ausgeführt. Dies ist die Standardoption für einen Fehler und das Abschneiden von Daten.|  
|Fehler ignorieren|Der Fehler oder das Abschneiden von Daten wird ignoriert, und die Datenzeile wird an die Ausgabe der Transformation oder Quelle weitergeleitet.|  
|Zeile umleiten|Der Fehler oder das Abschneiden der Datenzeile wird an die Fehlerausgabe der Quelle, der Transformation oder des Zieles umgeleitet.|  
  
## <a name="adding-the-error-description"></a>Hinzufügen der Fehlerbeschreibung  
 Eine Fehlerausgabe stellt standardmäßig den numerischen Fehlercode bereit und enthält in der Regel den Bezeichner der Spalte, in dem der Fehler aufgetreten ist. Sie können die Skriptkomponente verwenden, um die Fehlerbeschreibung in einer zusätzlichen Spalte einzuschließen, indem Sie für den Aufruf der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>-Schnittstelle eine einzelne Zeile des Skripts verwenden.  
  
 Die Skriptkomponente kann dem Fehlersegment des Datenflusses hinzugefügt werden, und zwar an eine beliebige Stelle unterhalb der Datenflusskomponenten, deren Fehler Sie erfassen möchten. In der Regel wird die Skriptkomponente jedoch eingefügt, kurz bevor die Fehlerzeilen in ein Ziel geschrieben werden. Auf diese Weise sucht das Skript nur nach Beschreibungen für geschriebene Fehlerzeilen. Beispielsweise korrigiert das Fehlersegment des Datenflusses u. U. einige Fehler und schreibt diese Zeilen nicht in ein Fehlerziel. Weitere Informationen finden Sie unter [Erweitern einer Fehlerausgabe mit der Skriptkomponente](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md).  
  
### <a name="to-configure-an-error-output"></a>So konfigurieren Sie eine Fehlerausgabe  
  
-   [Konfigurieren einer Fehlerausgabe in einer Datenflusskomponente](../configure-an-error-output-in-a-data-flow-component.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datenfluss](data-flow.md)   
 [Transformieren von Daten mit Transformationen](transformations/transform-data-with-transformations.md)   
 [Verbinden von Komponenten mit Pfaden](../connect-components-with-paths.md)   
 [Datenflusstask](../control-flow/data-flow-task.md)   
 [Datenfluss](data-flow.md)  
  
  
