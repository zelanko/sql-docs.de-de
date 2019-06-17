---
title: Analysis Services-Entwicklerdokumentation | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 44be6e7ab0bb3598b2478f1a5f94e64fee48d05a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65449984"
---
# <a name="analysis-services-developer-documentation"></a>Entwicklerhandbuch (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

In Analysis Services fast alle Objekte und die Workload programmierbaren und häufig ist mehr als ein Ansatz zur Auswahl.  Unter anderem Schreiben von verwaltetem Code, Skripts oder mithilfe von offenen Standards wie XMLA und MSOLAP, wenn Anforderungen an die Lösung ausschließen, die mit .NET Framework.

## <a name="what-you-can-accomplish-in-code"></a>Was können Sie im Code erreichen.
Typische Programmierszenarien enthalten Server und Bereitstellung, Verwaltung, Modell und Datenbankerstellung und Datenzugriff über Ihre benutzerdefinierten Anwendungen und die Berichte, die Analysis Services-Daten verwenden. Alle diese Szenarien ist eine feste Architektur und Objekt Definition Hierarchie, mit gut verstandenen Vorgängen, die Datendefinition, Verarbeitungs- und abfragearbeitsauslastungen umfassen.

Obwohl Objekte und -Workloads programmierbaren sind, sind sie nicht erweiterbar. Insbesondere Cartridges für benutzerdefinierte Daten, die Daten aus einer nicht unterstützten Datenquellen abrufen, anpassen oder ersetzen die Formel oder Speicher-Engine-Verhalten kann nicht erstellt werden, noch können Sie neue Typen von Metadaten des Objekts auf einem Server, eine Datenbank oder ein Modell erstellen.

Weitere Details auf dem letzten Punkt zum Erstellen von neuen Objekttypen: zwar eine neue Art von Objekt kann nicht erstellt werden, können Sie berechnete Objekte, die von Ausdrücken oder Code erstellt wird, zur Laufzeit erstellen. Nicht alle in Ihrem Modell muss vordefiniert und eine vorhandene Datenstruktur zugeordnet werden. Darüber hinaus können Sie das Schema über Anmerkungen in AMO Übergabe von objektspezifischen Informationen an Ihre Client-Anwendung erweitern.

## <a name="choose-a-platform-or-approach-to-development"></a>Wählen Sie eine Plattform oder einen Ansatz für die Entwicklung
Analysis Services bietet viele Möglichkeiten, eine Lösung über Code anpassen, aber die meisten Entwickler verwenden, die verwalteten APIs oder das Skript.

- Verwaltete APIs enthalten [AMO und TOM](http://msdn.microsoft.com/library/mt436122.aspx) für die Datendefinition und administrative Tasks und [ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx) für die Unterstützung für Abfragen über den Clientcode. In SQL Server 2016 ist AMO aktualisiert, um die neuen tabellarischen Metadaten für Modelle erstellt oder ein Upgrade auf Kompatibilitätsgrad 1200 und höher verwenden.

- Skripts kann häufig die gleichen Ergebnisse wie eine Programmdatei mit möglicherweise weniger Aufwand erreichen.

  - Sie können PowerShell-Skript mithilfe von Analysis Services PowerShell-Komponenten, die AMO-Typen direkt aufrufen, schreiben. In PowerShell verwenden können Sie auch erstellen und Ausführen von ASSL/XMLA oder TMSL (im JSON-Format)-Skript.

  - ASSL und TMSL sind Skriptsprachen, die angeben, dass Objekte in verwendet ermitteln und -Vorgänge ausführen. Welche Art von Skript, die Sie verwenden, hängt von der zugrunde liegenden-Server, Datenbank oder Modell.

  - Tabellarische Modelle oder Datenbanken mit Kompatibilitätsgrad 1200 oder höher verwenden, der Tabular Model Scripting Language (TMSL), die im JSON-Format ist.

  - Verwenden Analysis Services Scripting Language (ASSL), ist die Analysis Services-Erweiterung von der offene Standard XMLA, mehrdimensionale und tabellarische Modelle mit Kompatibilitätsgrad 1050-1103.

  - Sie können ASSL oder TMSL-Skripts in Management Studio generieren. Sie können auch **Ansichtscode** in SQL Server Data Tools, um die Modelldefinition in ASSL oder TMSL anzuzeigen.

- Obwohl es möglich, eine Lösung basierend auf der offenen Standards von XMLA und MDX zu erstellen ist, ist es ziemlich selten dazu. Es gibt keine Dokumentation als XMLA und MDX-Funktionsreferenz um, und die meisten Community und support-Forum zu zeichnet aus Erfahrungen mit .NET oder systemeigenen (MSOLAP)-Technologien.

## <a name="programming-in-analysis-services"></a>In Analysis Services-Programmierung
[Data Mining-Programmierung](../analysis-services/data-mining/data-mining-programming.md) beschreibt die Herangehensweisen, die zum Erstellen von Projektmappen, die Datamining-Objekte enthalten.

[Mehrdimensionale Programmiermodell](../analysis-services/multidimensional-models/multidimensional-model-programming.md) beschreibt die Entwicklungsaufgaben und Herangehensweisen zum Integrieren von mehrdimensionalen modellobjekten in einer benutzerdefinierten Lösung.

[Programmieren von tabellarischen Modellen für Kompatibilitätsgrad 1200 und höher](../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)
**neu in SQL Server 2016**.  Fasst zusammen, die Schnittstellen und Skriptsprachen für Programmgesteuertes Arbeiten mit tabellarischen 1200 und höher Modelle verwendet.

[Programmieren von tabellarischen Modellen für Compatibility Levels 1050 bis 1103](../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md) in dieser Dokumentation richtet sich an Entwickler, die tabellarische Modelle mit älteren Kompatibilitätsgraden unterstützen. Es wird beschrieben, die CSDL-Erweiterungen, die ein tabellarisches Modell im XML-Syntax zu definieren. Darüber hinaus Informationen zur Syntax und Tabellenobjekts Modelldefinitionen gespeichert.

[Analysis Services Management Objects (AMO)](https://msdn.microsoft.com/library/mt436122.aspx) Referenzdokumentation für Entwickler für den verwalteten Anbieter, Analysis Services Management Objects (AMO), für die Datendefinition und -Verwaltung, einschließlich der Verarbeitung.

[ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx) Referenzdokumentation für Entwickler für den verwalteten Anbieter ADOMD.NET für Daten in den programmgesteuerten Zugriff als auch das abfragearbeitsauslastungen verwendet.

[Analysis Services-Schemarowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/analysis-services-schema-rowsets) beschreibt die Schemarowsets, die Informationen zu Serverstatus, Servervorgängen und Datenbankobjekten liefern.

[XML für die Analyse &#40;XMLA&#41; Verweis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) beschreibt XMLA-Konzepte, die Ihnen helfen zu verstehen, wie XMLA zu Ihrer benutzerdefinierten Projektmappe beitragen. Darüber hinaus wird der Grad der Kompatibilität mit der XMLA 1.1-Spezifikation beschrieben.

[Analysis Services Scripting Language &#40;ASSL für XMLA&#41; ](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) beschreibt die ASSL-Erweiterungen für XMLA. ASSL stellt eine Datendefinitions- und Datenbearbeitungssprache für mehrdimensionale Analysis Services-Modelle bereit und ist eine Ergänzung der XMLA-Spezifikation.

[Tabular Model Scripting Language &#40;TMSL&#41; Verweis](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference) TMSL ist eine JSON-Darstellung von tabellarischen Modellen mit Kompatibilitätsgrad 1200 und höher. Objektdefinitionen basieren auf tabellarische Metadaten von Konstrukten wie Tabelle, Spalte und Beziehung anstatt mehrdimensionale Metadaten, die möglicherweise nicht vertraut sind, wenn Sie noch nicht mit der datenmodellierung für Analysis Services im tabellarischen Modus sind.

[Referenz zu Analysis Services PowerShell](../analysis-services/powershell/analysis-services-powershell-reference.md) dokumentiert den Cmdlets für administrative Funktionen sowie die allgemeine **Invoke-ASCmd** -Cmdlet, das Skript bzw. die Abfrage als Eingabe akzeptiert.

## <a name="see-also"></a>Siehe auch
[Technische Referenz für den](../analysis-services/powershell/technical-reference-ssas.md)
[Abfrage- und Ausdruckssprachreferenz &#40;Analysis Services&#41;](http://msdn.microsoft.com/library/gg492188.aspx)
