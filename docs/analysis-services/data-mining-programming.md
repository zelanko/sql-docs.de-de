---
title: Datamining-Programmierungsverfahren | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1be416528bc923e757afb9a8f3e556790941bf11
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34019957"
---
# <a name="data-mining-programming"></a>Data Mining-Programmierung
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Wenn die integrierten Tools und Viewer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Ihren Anforderungen nicht entsprechen, können Sie die Effektivität von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] durch Codieren eigener Erweiterungen erhöhen. Dabei haben Sie zwei Möglichkeiten:  
  
-   **XMLA**  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt XML for Analysis (XMLA) als Protokoll für die Kommunikation mit Clientanwendungen. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt zusätzliche Befehle, die die XML for Analysis-Spezifikation erweitern.  
  
     Weil in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] für die Datendefinition, Datenbearbeitung und Datenkontrolle XMLA verwendet, können Sie Miningstrukturen und Miningmodelle mithilfe der in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] bereitgestellten visuellen Tools erstellen und anschließend die erstellten Data Mining-Objekte mithilfe der Data Mining Extensions (DMX)- und Analysis Services Scripting Language (ASSL)-Skripts erweitern.  
  
     Sie können Data Mining-Objekte vollständig in XMLA-Skripts erstellen und ändern und aus Ihren eigenen Anwendungen programmgesteuert Vorhersageabfragen für die Modelle ausführen.  
  
-   **Analysis Management Objects (AMO)**  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt außerdem ein vollständiges Framework bereit, das Data Mining-Drittanbietern die Integration der Data Mining-Objekte in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ermöglicht.  
  
     Sie können Miningstrukturen und Miningmodelle mithilfe von AMO erstellen. Siehe die folgenden Beispiele in CodePlex:  
  
    -   AMO-Browser  
  
         Stellt eine Verbindung mit der angegebenen SSAS-Instanz her und listet alle Serverobjekte und deren Eigenschaften auf, einschließlich Miningstruktur und Miningmodelle.  
  
    -   AMO Simple Sample  
  
         Im AS Simple Sample werden folgende Verfahren behandelt: programmgesteuerter Zugriff auf die meisten Hauptobjekte, Durchsuchen von Metadaten und Zugriff auf Werte in Objekten.  
  
         Das Beispiel veranschaulicht auch, wie Sie eine Data Mining-Struktur und ein Data Mining-Modell erstellen und verarbeiten und wie ein vorhandenes Data Mining-Modell durchsucht wird.  
  
-   **DMX**  
  
     DMX kann verwendet werden, um Befehlsanweisungen, Vorhersageabfragen und Metadatenabfragen zu kapseln und Ergebnisse im Tabellenformat zurückzugeben, vorausgesetzt, Sie haben eine Verbindung mit einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server hergestellt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [OLE DB für Datamining](../analysis-services/data-mining-programming-ole-db.md)  
 Beschreibt Erweiterungen der Spezifikation zur Unterstützung von Data Mining und mehrdimensionalen Daten: neue Schemarowsets und -spalten, Data Mining Extensions (DMX)-Sprache zum Erstellen und Verwalten von Miningstrukturen.  
  
## <a name="related-reference"></a>Verwandter Verweis  
 [Entwickeln mit ADOMD.NET](../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
 Bietet eine Einführung in ADOMD.NET-Client- und Server-Programmierobjekte.  
  
 [Entwickeln mit Analysis Management Objects & #40; AMO & #41;](../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
 Stellt die AMO-Programmierbibliothek vor.  
  
 [Entwickeln mit Analysis Services Scripting Language & #40; ASSL & #41;](../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 Gibt eine Einführung in XML for Analysis (XMLA) und die zugehörigen Erweiterungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwicklerhandbuch (Analysis Services)](../analysis-services/analysis-services-developer-documentation.md)   
 [Datamining-Erweiterungen & #40; DMX & #41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)  
  
  
