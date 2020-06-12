---
title: Data Mining-Programmierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd4bd48b5914d5fda89f94c0a959e670ffec3321
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528676"
---
# <a name="data-mining-programming"></a>Data Mining-Programmierung
  Wenn die integrierten Tools und Viewer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Ihren Anforderungen nicht entsprechen, können Sie die Effektivität von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] durch Codieren eigener Erweiterungen erhöhen. Dabei haben Sie zwei Möglichkeiten:  
  
-   **XMLA**  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]unterstützt XML for Analysis (XMLA) als Protokoll für die Kommunikation mit Client Anwendungen. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt zusätzliche Befehle, die die XML for Analysis-Spezifikation erweitern.  
  
     Weil in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für die Datendefinition, Datenbearbeitung und Datenkontrolle XMLA verwendet, können Sie Miningstrukturen und Miningmodelle mithilfe der in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] bereitgestellten visuellen Tools erstellen und anschließend die erstellten Data Mining-Objekte mithilfe der Data Mining Extensions (DMX)- und Analysis Services Scripting Language (ASSL)-Skripts erweitern.  
  
     Sie können Data Mining-Objekte vollständig in XMLA-Skripts erstellen und ändern und aus Ihren eigenen Anwendungen programmgesteuert Vorhersageabfragen für die Modelle ausführen.  
  
-   **Analysis Management Objects (AMO)**  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stellt außerdem ein vollständiges Framework bereit, das Data Mining-Drittanbietern die Integration der Data Mining-Objekte in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ermöglicht.  
  
     Sie können Miningstrukturen und Miningmodelle mithilfe von AMO erstellen. Siehe die folgenden Beispiele in CodePlex:  
  
    -   AMO-Browser  
  
         Stellt eine Verbindung mit der angegebenen SSAS-Instanz her und listet alle Serverobjekte und deren Eigenschaften auf, einschließlich Miningstruktur und Miningmodelle.  
  
    -   AMO Simple Sample  
  
         Im AS Simple Sample werden folgende Verfahren behandelt: programmgesteuerter Zugriff auf die meisten Hauptobjekte, Durchsuchen von Metadaten und Zugriff auf Werte in Objekten.  
  
         Das Beispiel veranschaulicht auch, wie Sie eine Data Mining-Struktur und ein Data Mining-Modell erstellen und verarbeiten und wie ein vorhandenes Data Mining-Modell durchsucht wird.  
  
-   **DMX**  
  
     DMX kann verwendet werden, um Befehlsanweisungen, Vorhersageabfragen und Metadatenabfragen zu kapseln und Ergebnisse im Tabellenformat zurückzugeben, vorausgesetzt, Sie haben eine Verbindung mit einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Server hergestellt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [OLE DB für Data Mining](../../../2014/analysis-services/dev-guide/ole-db-for-data-mining.md)  
 Beschreibt Erweiterungen der Spezifikation zur Unterstützung von Data Mining und mehrdimensionalen Daten: neue Schemarowsets und -spalten, Data Mining Extensions (DMX)-Sprache zum Erstellen und Verwalten von Miningstrukturen.  
  
## <a name="related-reference"></a>Verwandter Verweis  
 [Entwickeln mit ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
 Bietet eine Einführung in ADOMD.NET-Client- und Server-Programmierobjekte.  
  
 [Entwickeln mit Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
 Stellt die AMO-Programmierbibliothek vor.  
  
 [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 Gibt eine Einführung in XML for Analysis (XMLA) und die zugehörigen Erweiterungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwicklerhandbuch &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Referenz](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
