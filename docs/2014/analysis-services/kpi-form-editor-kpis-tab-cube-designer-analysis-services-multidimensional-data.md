---
title: KPI-Formular-Editor (Registerkarte ' KPIs ', Cube-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpidefinitionpane.f1
ms.assetid: 45c6453a-bbe2-4ca5-836e-c7ef11cfcb65
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 49df3dcaf89d98d42da0a89ea7de0b8114093913
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166380"
---
# <a name="kpi-form-editor-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a>KPI-Formular-Editor (Registerkarte 'KPIs', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Im Bereich des **Formular-Editors für KPIs** auf der Registerkarte **KPIs** des Cube-Designers können Sie den ausgewählten Key Performance Indicator (KPI) erstellen oder ändern.  
  
> [!NOTE]  
>  Der Bereich wird nur in der Formularansicht angezeigt.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Namen des KPIs ein.  
  
 **Zugeordnete Measuregruppe**  
 Wählen Sie die Measuregruppe aus, die dem KPI zugeordnet ist. Die Clientanwendung kann diese Information verwenden, um zu bestimmen, welche Dimensionen verfügbar sind, wenn der Benutzer diesen KPI durchsucht.  
  
 **Wertausdruck**  
 Erweitern Sie diese Option, um den MDX-Ausdruck (Multidimensional Expressions) für den Wert des KPIs anzuzeigen oder zu bearbeiten.  
  
 Geben Sie den MDX-Ausdruck ein, der den Wert des KPIs zurückgibt.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 **Zielausdruck**  
 Erweitern Sie diese Option, um den MDX-Ausdruck für den Zielwert des KPIs anzuzeigen oder zu bearbeiten.  
  
 Geben Sie den MDX-Ausdruck ein, der den Zielwert des KPIs zurückgibt, wenn der KPI ausgeführt wird.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 **Status**  
 Erweitern Sie diese Option, um die Optionen **Statusgrafik** und **Statusausdruck** anzuzeigen.  
  
 **Statusgrafik**  
 Wählen Sie die Grafik aus, die von der Clientanwendung verwendet werden soll, um den Statuswert in grafischer Form darzustellen.  
  
> [!NOTE]  
>  Die Clientanwendung kann die ausgewählte Grafik unterstützen oder Sie durch eine angemessene Alternative ersetzen.  
  
 **Statusausdruck**  
 Geben Sie den MDX-Ausdruck ein, der den Statuswert des KPIs zurückgibt, wenn der KPI ausgeführt wird.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 Es wird empfohlen, dass dieser Ausdruck eine Dezimalzahl zwischen –1 und 1 zurückgibt. Eine niedrigere Zahl stellt eine negative Situation dar, während eine höhere Zahl eine positive Situation darstellt.  
  
> [!NOTE]  
>  Werte unter –1 und über 1 sind möglich, können aber möglicherweise von Clientanwendungen von Drittanbietern nicht ordnungsgemäß interpretiert werden.  
  
 **Trend**  
 Erweitern Sie diese Option, um die Optionen **Trendgrafik** und **Trendausdruck** anzuzeigen.  
  
 **Trendgrafik**  
 Wählen Sie die Grafik aus, die von der Clientanwendung verwendet werden soll, um den Trendwert in grafischer Form darzustellen.  
  
> [!NOTE]  
>  Die Clientanwendung kann die ausgewählte Grafik unterstützen oder Sie durch eine angemessene Alternative ersetzen.  
  
 **Trendausdruck**  
 Geben Sie den MDX-Ausdruck ein, der den Trendwert des KPIs zurückgibt.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 Der Trendausdruck kann auf beliebigen zeitbasierten Kriterien basieren, die in einem gegebenen Geschäftskontext einen Sinn ergeben. Es wird empfohlen, dass dieser Ausdruck eine Dezimalzahl zwischen –1 und 1 zurückgibt. Eine niedrigere Zahl stellt im Zeitverlauf einen negativen Trend dar, eine höhere Zahl stellt im Zeitverlauf einen positiven Trend dar.  
  
> [!NOTE]  
>  Werte unter –1 und über 1 sind möglich, können aber möglicherweise von Clientanwendungen von Drittanbietern nicht ordnungsgemäß interpretiert werden.  
  
 **Weitere Eigenschaften**  
 Erweitern Sie diese Option, um die Optionen **Anzeigeordner**, **Übergeordneter KPI**, **Aktuelles Zeitelement**, **Gewichtung** **und Beschreibung** anzuzeigen.  
  
 **Anzeigeordner**  
 Geben Sie die Kategorisierung des KPIs ein, die von der Clientanwendung zum Anzeigen verwendet werden soll.  
  
 Verwenden Sie einen umgekehrten Schrägstrich (\\), um die Ordnernamen in einem Anzeigeordner zu trennen, und ein Semikolon (;), um mehrere Anzeigeordner voneinander zu trennen. Beispiel: `Category\Goal\Scientific;Category\Goal\Metric`.  
  
 **Übergeordneter KPI**  
 Wählen Sie einen vorhandenen KPI aus, unter dem der von der Clientanwendung zu verwendende KPI kategorisiert werden soll.  
  
> [!NOTE]  
>  Wenn diese Option auf einen vorhandenen KPI festgelegt ist, wird **Anzeigeordner** ignoriert.  
  
 **Aktuelles Zeitelement**  
 Geben Sie den MDX-Ausdruck ein, der das Element zurückgibt, das den zeitlichen Kontext des KPIs identifiziert.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
> [!IMPORTANT]  
>  Der MDX-Ausdruck muss den eindeutigen Namen eines Elements innerhalb einer Zeitdimension zurückgeben, die der unter **Zugeordnete Measuregruppe**angegebenen Measuregruppe zugeordnet ist.  
  
 **Weight**  
 Erweitern Sie diese Option, um den MDX-Ausdruck für den Gewichtungsfaktor des KPIs anzuzeigen oder zu bearbeiten.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 **Beschreibung**  
 Geben Sie die optionale Beschreibung des KPIs ein.  
  
## <a name="see-also"></a>Siehe auch  
 [KPIs &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
