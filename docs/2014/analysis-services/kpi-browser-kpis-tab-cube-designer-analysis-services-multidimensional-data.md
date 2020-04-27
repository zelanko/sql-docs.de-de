---
title: KPI-Browser (Registerkarte ' KPIs ', Cube-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpibrowserpane.f1
ms.assetid: 2f61bde6-e6ec-4511-8645-c272374014ad
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 41000c78c4ff3a68e1d3acd107ce57c221a16e28
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66079503"
---
# <a name="kpi-browser-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a>KPI-Browser (Registerkarte 'KPIs', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Bereichs **KPI-Browser** der Registerkarte **KPIs** des Cube-Designers können Sie die KPI-Ergebnisse (Key Performance Indicators) anzeigen und testen. KPIs müssen vor dem Durchsuchen zuerst [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] auf einer-Instanz bereitgestellt werden.  
  
> [!NOTE]  
>  Der Bereich wird nur in der Browseransicht angezeigt.  
  
## <a name="options"></a>Optionen  
 **Teilcuberaster**  
 Definieren Sie mithilfe dieser Option einen Teilcube, und schränken Sie die im Bereich **Ergebnisse** angezeigten Ergebnisse der KPIs ein. Das Raster enthält die folgenden Spalten:  
  
 **Dimension**  
 Wählen Sie die Dimension aus, auf die dieser Filter angewendet wird.  
  
 **Hierarchy**  
 Wählen Sie die Hierarchie aus, auf die dieser Filter angewendet wird.  
  
 **Operator**  
 Wählen Sie den Operator aus, der definiert, wie der Ausdruck in **Filterausdruck** auf die ausgewählte Hierarchie angewendet wird. Die folgende Tabelle beschreibt die verfügbaren Operatoren.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Gleich**|Die Ergebnisse sind auf die in **Filterausdruck**definierte Menge beschränkt.|  
|**Ungleich**|Die Ergebnisse sind auf die Elemente beschränkt, die durch die in **Filterausdruck**definierte Menge ausgeschlossen werden.|  
|**In**|Die Ergebnisse sind auf die in **Filterausdruck**gewählte benannte Menge beschränkt.|  
|**Not In**|Die Ergebnisse sind auf die Elemente beschränkt, die durch die in **Filterausdruck**gewählte benannte Menge ausgeschlossen werden.|  
|**Inhalt**|Die Ergebnisse sind auf die Elemente beschränkt, deren Elementnamen die in **Filterausdruck**angegebene Zeichenfolge enthalten.|  
|**Beginnt mit**|Die Ergebnisse sind auf die Elemente beschränkt, deren Elementnamen mit der in **Filterausdruck**angegebenen Zeichenfolge beginnen.|  
|**Bereich (inklusiv)**|Die Ergebnisse sind auf den in **Filterausdruck**ausgewählten Bereich beschränkt.|  
|**Bereich (exklusiv)**|Die Ergebnisse sind auf die Elemente beschränkt, die durch den in **Filterausdruck**ausgewählten Bereich ausgeschlossen werden.|  
|**MDX**|Die Ergebnisse sind auf den in **Filterausdruck**festgelegten MDX-Ausdruck (Multidimensional Expressions) beschränkt.|  
  
 **Filterausdruck**  
 Geben Sie den Ausdruck ein, der durch **Operator**ausgewertet werden soll, um die zu durchsuchenden KPI-Ergebnisse einzuschränken.  
  
> [!NOTE]  
>  Bei dem Feld handelt es sich um ein dynamisches Dateneingabeelement, dessen Anzeigemodus sich je nach dem vom ausgewählten Operator benötigten Datentyp ändert.  
  
 **Ergebnis Raster**  
 Zeigt basierend auf einem unter **Filterraster**definierten Filter den ausgewerteten Wert, das Ziel, den Status und den Trend der KPIs an. Das Raster enthält die folgenden Spalten:  
  
 **Struktur anzeigen**  
 Zeigt die im Cube enthaltenen KPIs hierarchisch nach den Werten **Anzeigeordner** oder **Übergeordneter KPI** für jeden KPI organisiert an.  
  
 **Wert**  
 Zeigt den Wert des KPIs an.  
  
 **Zielsetzung**  
 Zeigt den Zielwert des KPIs an.  
  
 **Status**  
 Zeigt die Statusgrafik des KPIs an.  
  
 **Trends**  
 Zeigt die Trendgrafik des KPIs an.  
  
 **Weight**  
 Zeigt den Gewichtungungsfaktor des KPIs an.  
  
 **Beschreibung**  
 Zeigt ein Informationssymbol an, wenn für einen KPI eine Beschreibung bereit steht.  
  
 Zeigen Sie mit dem Cursor auf das Informationssymbol, um eine QuickInfo mit einer Beschreibung für den KPI anzuzeigen.  
  
> [!NOTE]  
>  Wenn während der Berechnung eines KPIs auf der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz ein Fehler auftritt, zeigt diese Option mit dem Fehler verknüpfte Informationen an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [KPIs &#40;Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
