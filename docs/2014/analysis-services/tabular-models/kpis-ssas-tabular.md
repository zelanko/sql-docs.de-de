---
title: KPIs (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: a0524602-5239-45a7-8c44-2477302a3637
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 596fc7d8ebdbdac3795920948b5082a0e066ba0d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104620"
---
# <a name="kpis-ssas-tabular"></a>KPIs (SSAS – tabellarisch)
  Ein *KPI* (Key Performance Indicator) wird in einem Tabellenmodell verwendet, um die Leistung eines durch ein *Basismeasure* definierten Werts im Vergleich zu einem *Zielwert* zu messen, der ebenfalls durch ein Measure oder einen absoluten Wert definiert wird. Dieses Thema bietet Entwicklern von tabellarischen Modellen einen grundlegenden Überblick der in einem Tabellenmodell verwendeten KPIs.  
  
 Abschnitte in diesem Thema:  
  
-   [Vorteile](#bkmk_benefits)  
  
-   [Beispiel](#bkmk_example)  
  
-   [Erstellen und Bearbeiten von KPIs](#bkmk_create)  
  
-   [Verwandte Aufgaben](#bkmk_related_tasks)  
  
##  <a name="bkmk_benefits"></a> Vorteile  
 Key Performance Indicator (KPI) ist ein Begriff aus der Wirtschaft, der eine quantifizierbare Maßeinheit zur Messung der Umsetzung von Geschäftszielen darstellt. KPIs werden im Lauf der Zeit häufig ausgewertet. Die Vertriebsabteilung eines Unternehmens könnte KPIs beispielsweise verwenden, um den monatlichen Bruttogewinn mit dem vorausgesagten Bruttogewinn zu vergleichen. Die Buchhaltung könnte die monatlichen Ausgaben und Einnahmen gegenüberstellen, um eine Kostenauswertung vorzunehmen, und die Personalabteilung könnte den Quartalsumsatz pro Mitarbeiter ermitteln. Beides sind Beispiele für KPIs. Um eine schnelle und genaue Verlaufsübersicht ihrer Geschäftserfolge zu erhalten und Trends zu erkennen, greifen Fachanwender oft auf KPIs zurück, die in geschäftlichen Kennzahlensystemen gruppiert werden.  
  
 Ein KPI in einem Tabellenmodell enthält:  
  
 **Basiswert**  
 Ein Basiswert wird durch ein Measure definiert, das zu einem Wert aufgelöst wird. Dieser Wert, kann z. B. ein Aggregat tatsächlicher Umsatzzahlen oder ein berechnetes Measure wie der Ertrag für einen bestimmten Zeitraum sein.  
  
 **Zielwert**  
 Ein Zielwert wird entweder durch ein Measure definiert, das zu einem Wert aufgelöst wird, oder durch einen absoluten Wert. Ein Zielwert könnte beispielsweise der Betrag sein, um den die Führungskräfte einer Organisation die Verkaufszahlen oder Gewinne steigern möchten.  
  
 **Statusschwellenwerte**  
 Ein Statusschwellenwert wird durch den Bereich zwischen einem niedrigen und hohen Schwellenwert oder durch einen festen Wert definiert. Der Statusschwellenwert wird anhand einer Grafik dargestellt, damit Benutzer problemlos den Status des Basiswerts im Vergleich zum Zielwert ermitteln können.  
  
##  <a name="bkmk_example"></a> Beispiel  
 Der Vertriebsleiter von Adventure Works möchte eine PivotTable erstellen, in der schnell angezeigt wird, ob Vertriebsmitarbeiter ihre Umsatzvorgaben in einem bestimmten Zeitraum (Jahr) erfüllen. Für jeden Vertriebsmitarbeiter sollen in der PivotTable die tatsächlichen Verkaufszahlen (in Dollar), die Umsatzvorgabe (in Dollar) und eine einfache Statusgrafik angezeigt werden, die Aufschluss darüber gibt, ob der Vertriebsmitarbeiter unter oder über dieser Vorgabe liegt bzw. diese genau erfüllt. Zudem möchte der Vertriebsleiter die Daten nach Jahr unterteilen.  
  
 Mit Unterstützung eines Kollegen, der für die Entwicklung von BI-Lösungen zuständig ist, fügt der Vertriebsleiter dem tabellarischen AdventureWorks-Modell einen "Sales KPI" hinzu. Anschließend stellt er mithilfe von [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] eine Verbindung mit dem tabellarischen Adventure Works-Modell als Datenquelle her und erstellt eine PivotTable mit den Feldern (Measures und KPI) und Slicern, um zu analysieren, ob die Vertriebsmannschaft ihre Vorgaben erfüllt.  
  
 Im Modell wird ein Measure für die Spalte "SalesAmount" in der Tabelle "FactResellerSales" erstellt, das die tatsächlichen Vertriebszahlen für jeden Vertriebsmitarbeiter in Dollar angibt. Durch dieses Measure wird der Basiswert des KPIs definiert.  
  
 Das Sales-Measure wird anhand der folgenden Formel erstellt:  
  
```  
Sales:=Sum(FactResellerSales[SalesAmount])  
```  
  
 In der Spalte "SalesAmountQuota" der Tabelle "FactSalesQuota" sind die Umsatzvorgaben für jeden Mitarbeiter definiert. Die Werte in dieser Spalte dienen als Zielmeasure (Wert) im KPI.  
  
 Das Measure "SalesAmountQuota" wird anhand der folgenden Formel erstellt:  
  
```  
Target SalesAmountQuota:=Sum(FactSalesQuota[SalesAmountQuota])  
```  
  
> [!NOTE]  
>  Es besteht eine Beziehung zwischen der Spalte "EmployeeKey" in der Tabelle "FactSalesQuota" und der Spalte "EmployeeKey" in der Tabelle "DimEmployees". Diese Beziehung ist erforderlich, damit jeder Vertriebsmitarbeiter aus der Tabelle "DimEmployee" in der Tabelle "FactSalesQuota" dargestellt werden kann.  
  
 Nachdem die Measures nun erstellt wurden, um als Basis- und Zielwert des KPIs zu fungieren, wird das Sales-Measure zu einem neuen Sales-KPI erweitert. Im "Sales KPI" ist das Measure "Target SalesAmountQuota" als Zielwert definiert. Der Statusschwellenwert wird als Bereich von Prozentzahlen definiert, wobei 100 % der Zielvorgabe entsprechen. Das würde bedeuten, dass die durch das Sales-Measure definierten tatsächlichen Verkaufszahlen die Vorgaben erfüllen, die im Measure "Target SalesAmountQuota" definiert sind. Zum Definieren der niedrigen und hohen Prozentwerte wird die Statusleiste verwendet, und es wird ein Grafiktyp ausgewählt.  
  
 Der Vertriebsleiter kann jetzt eine PivotTable erstellen, indem er den Basiswert, Zielwert und den Status des KPIs dem Feld Werte hinzufügt. Die Spalte "Employees" wird dem Feld "RowLabel" hinzugefügt, und die Spalte "CalendarYear" wird als Slicer verwendet.  
  
 Der Vertriebsleiter kann die tatsächlichen Umsatzzahlen, die Vertriebsvorgaben und den Status jedes Vertriebsmitarbeiters jetzt nach Jahr unterteilen. So lassen sich Vertriebstrends über Jahre analysieren, um zu ermitteln, ob die Vertriebsvorgaben für einen Vertriebsmitarbeiter angepasst werden müssen.  
  
##  <a name="bkmk_create"></a> Erstellen und Bearbeiten von KPIs  
 Zum Erstellen von KPIs im Modell-Designer verwenden Sie das Dialogfeld Key Performance Indicator. Da KPIs einem Measure zugeordnet werden müssen, erstellen Sie einen KPI, indem Sie ein Measure erweitern, das einen Basiswert ergibt, und dann entweder ein Measure erstellen, das einen Zielwert ergibt, oder einen absoluten Wert eingeben. Nachdem Basismeasure (Wert) und Zielwert definiert wurden, können Sie die Parameter für den Statusschwellenwert zwischen dem Basis- und Zielwert definieren. Der Status wird in einem grafischen Format mit auswählbaren Symbolen, Balken, Diagrammen oder Farben angezeigt. Anschließend können Basiswert, Zielwert und Status einem Bericht oder einer PivotTable als Werte hinzugefügt werden, die für andere Datenfelder in Slices aufgeteilt werden können.  
  
 Um das Dialogfeld **Key Performance Indicator**im Measureraster für eine Tabelle anzuzeigen, klicken Sie mit der rechten Maustaste auf ein Measure, das als Basiswert dient, und klicken Sie dann auf KPI erstellen. Nachdem ein Measure als Basiswert zu einem KPI erweitert wurde, wird im Measureraster neben dem Measurenamen ein Symbol angezeigt, das angibt, dass das Measure einem KPI zugeordnet ist.  
  
##  <a name="bkmk_related_tasks"></a> Verwandte Aufgaben  
  
|Thema|Description|  
|-----------|-----------------|  
|[Erstellen und Verwalten von KPIs &#40;SSAS – tabellarisch&#41;](kpis-ssas-tabular.md)|Beschreibt das Erstellen eines KPIs mit einem Basismeasure, einem Zielmeasure und Statusschwellenwerten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Measures &#40;SSAS – tabellarisch&#41;](measures-ssas-tabular.md)   
 [Perspektiven &#40;SSAS – tabellarisch&#41;](perspectives-ssas-tabular.md)  
  
  
