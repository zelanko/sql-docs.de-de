---
title: Unterstützung für Übersetzungen in Analysis Services | Microsoft-Dokumentation
ms.date: 01/09/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd727b56649ce9ffc237575b0311db256ec9b2fc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207419"
---
# <a name="translation-support-in-analysis-services"></a>Unterstützung für Übersetzungen in Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenmodelle, Sie können mehrere Übersetzungen einer Beschriftung oder Beschreibung zu kulturspezifische Zeichenfolgen basierend auf den Gebietsschemabezeichner (LCID) einbetten. Bei mehrdimensionalen Modellen können Übersetzungen für den Datenbanknamen, Cubeobjekte und Datenbankdimensionsobjekte hinzugefügt werden. Bei tabellarischen Modellen können Beschriftungen und Beschreibungen der Tabellen und Spalten übersetzt werden.  
  
 Durch Definieren einer Übersetzung werden die Metadaten und die übersetzte Beschriftung innerhalb des Modells erstellt. Um lokalisierte Zeichenfolgen in einer Clientanwendung zu rendern, müssen Sie jedoch entweder die **Language** -Eigenschaft für das Objekt festlegen oder einen **Culture** - oder **Locale Identifier** -Parameter in der Verbindungszeichenfolge übergeben (z.B. durch Festlegen von `LocaleIdentifier=1036` , um französische Zeichenfolgen zurückzugeben).  
  
 Planen Sie die Verwendung von **Locale Identifier** , wenn Sie mehrere gleichzeitige Übersetzungen desselben Objekts in verschiedenen Sprachen unterstützen möchten. Das Festlegen der **Language** -Eigenschaft funktioniert, hat aber Auswirkungen auf Verarbeitung und Abfragen, die möglicherweise unerwartete Ergebnisse liefern. Das Festlegen von **Locale Identifier** ist die bessere Wahl, da es nur verwendet wird, um die übersetzten Zeichenfolgen zurückzugeben.  
  
 Eine Übersetzung besteht aus einem Gebietsschemabezeichner (LCID), einer übersetzten Beschriftung für das Objekt (z. B. Dimensions- oder Attributname) und optional einer Bindung an eine Spalte, die Datenwerte in der Zielsprache enthält. Sie können mehrere Übersetzungen haben, jedoch nur jeweils eine für eine bestimmte Verbindung verwenden. Theoretisch können Sie beliebig viele Übersetzungen im Modell einbetten. Jede Übersetzung erhöht jedoch die Komplexität beim Testen, und alle Übersetzungen müssen dieselbe Sortierung verwenden. Beim Entwerfen Ihrer Lösung sollten Sie diese natürlichen Einschränkungen bedenken.  
  
> [!TIP]  
>  Sie können Clientanwendungen wie Excel, SQL Server Management Studio und SQL Server Profiler verwenden, um übersetzte Zeichenfolgen zurückzugeben. Weitere Informationen finden Sie unter [Tipps und Best Practices für die Globalisierung &#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md) .  
  
## <a name="how-to-add-translated-metadata-to-model-in-analysis-services"></a>Hinzufügen von übersetzten Metadaten zum Modell in Analysis Services  
 Schrittweise Anweisungen erhalten Sie über die folgenden Links:  
  
-   [Übersetzungen in tabellenmodellen](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)  
  
-   [Übersetzungen in mehrdimensionalen Modellen](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Globalisierungsszenarien für Analysis Services](../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [Sprachen und Sortierungen &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md)   
 [Festlegen oder Ändern der Spaltensortierung](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Tipps und Best Practices für die Globalisierung &#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
