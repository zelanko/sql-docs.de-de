---
title: Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 589fe7470de4909d9513d80726c59412f5ea2447
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56292358"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS)
Legen Sie den Gruppenausdruck des Datenbereichs basierend auf dem untergeordneten Feld und die übergeordnete Eigenschaft basierend auf dem übergeordneten Feld fest, um rekursive Daten in paginierten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichten anzuzeigen (wobei die Beziehung zwischen übergeordnetem und untergeordnetem Feld von Feldern im Dataset dargestellt wird).  
  
 Eine hierarchische Anzeige von Daten wird häufig für rekursive Hierarchiegruppen verwendet, z. B. für Angestellte in einem Unternehmensdiagramm. Das Dataset enthält eine Liste mit Mitarbeitern und Managern, wobei die Namen der Manager auch in der Mitarbeiterliste enthalten sind.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Erstellen von rekursiven Hierarchien  
 Sie müssen den Gruppenausdruck auf das Feld festlegen, das die untergeordneten Daten enthält, und die übergeordnete Eigenschaft der Gruppe auf das Feld, das die übergeordneten Daten enthält, um eine rekursive Hierarchie in einem Tablix-Datenbereich zu erstellen. Legen Sie z.B. für ein Dataset, das Felder für die Mitarbeiter-ID und die Manager-ID enthält (wobei die Mitarbeiter an die Manager berichten) den Gruppenausdruck auf die Mitarbeiter-ID und die übergeordnete Eigenschaft auf die Manager-ID fest.  
  
 Eine Gruppe, die als rekursive Hierarchie definiert ist (also eine Gruppe, die die übergeordnete Eigenschaft verwendet), kann nur über einen einzelnen Gruppenausdruck verfügen. Mit der **Level** -Funktion können Sie die Auffüllung in Textfeldern bestimmen, um die Mitarbeiternamen entsprechend ihrer Ebene in der Hierarchie einzurücken.  
  
 Weitere Informationen finden Sie unter [Hinzufügen oder Löschen einer Gruppe in einem Datenbereich (Berichts-Generator und SSRS)](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) und [Erstellen einer rekursiven Hierarchiegruppe (Berichts-Generator und SSRS)](../../reporting-services/report-design/create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Aggregatfunktionen zur Unterstützung der Rekursion  
 Sie können Reporting Services-Aggregatfunktionen verwenden, die den Parameter *Rekursiv* akzeptieren, um Zusammenfassungsdaten für eine rekursive Hierarchie zu berechnen. Die folgenden Funktionen akzeptieren **Recursive** als Parameter: [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md), [Avg](../../reporting-services/report-design/report-builder-functions-avg-function.md), [Count](../../reporting-services/report-design/report-builder-functions-count-function.md), [CountDistinct](../../reporting-services/report-design/report-builder-functions-countdistinct-function.md), [CountRows](../../reporting-services/report-design/report-builder-functions-countrows-function.md), [Max](../../reporting-services/report-design/report-builder-functions-max-function.md), [Min](../../reporting-services/report-design/report-builder-functions-min-function.md), [StDev](../../reporting-services/report-design/report-builder-functions-stdev-function.md), [StDevP](../../reporting-services/report-design/report-builder-functions-stdevp-function.md), [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md), [Var](../../reporting-services/report-design/report-builder-functions-var-function.md) und [VarP](../../reporting-services/report-design/report-builder-functions-varp-function.md). Weitere Informationen finden Sie unter [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)   
 [Tabellen (Berichts-Generator und SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Matrizen (Berichts-Generator und SSRS)](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)    
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
