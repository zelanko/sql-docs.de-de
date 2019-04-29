---
title: Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92412bbde8a1032b34264ca254560f31704281e8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63135575"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS)
  Um rekursive Daten anzuzeigen, in dem die Beziehung zwischen übergeordnetem und untergeordnetem durch Felder im Dataset dargestellt wird, können Sie den Region Gruppenausdruck basierend auf dem untergeordneten Feld festgelegt und die übergeordnete Eigenschaft basierend auf dem übergeordneten Feld festlegen.  
  
 Anzeigen von hierarchischen Daten ist ein gängiges Szenario für rekursive Hierarchiegruppen, z. B. für Angestellte in einem Organisationsdiagramm. Das Dataset enthält eine Liste von Mitarbeitern und Managern, wobei die Namen der Manager auch in der Liste der Mitarbeiter angezeigt.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Erstellen von rekursiven Hierarchien  
 Um eine rekursive Hierarchie in einem Tablix-Datenbereich zu erstellen, müssen Sie den Gruppenausdruck auf das Feld festlegen, die angibt, das die untergeordneten Daten und die übergeordnete Eigenschaft der Gruppe, die das Feld, das die übergeordneten Daten enthält. Z. B. für ein Dataset mit Feldern für die Mitarbeiter-ID und Manager-ID, in dem Mitarbeiter, die an die Manager Berichten den Gruppenausdruck die Mitarbeiter-ID und die übergeordnete Eigenschaft auf Manager-ID.  
  
 Eine Gruppe, die als eine rekursive Hierarchie (d. h. eine Gruppe, die die übergeordnete Eigenschaft verwendet) definiert ist, haben nur einen Gruppierungsausdruck. Mit der `Level`-Funktion können Sie den Textabstand in Textfeldern bestimmen, um die Mitarbeiternamen entsprechend ihrer Ebene in der Hierarchie einzurücken.  
  
 Weitere Informationen finden Sie unter [hinzufügen oder Löschen einer Gruppe in einem Datenbereich &#40;Berichts-Generator und SSRS&#41; ](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) und [Erstellen einer rekursiven Hierarchiegruppe &#40;Berichts-Generator und SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Aggregatfunktionen, die Unterstützung der Rekursion  
 Können Sie Reporting Services-Aggregatfunktionen, die die Parameter akzeptieren *rekursive* um Zusammenfassungsdaten für eine rekursive Hierarchie zu berechnen. Die folgenden Funktionen akzeptieren `Recursive` als Parameter: [Summe](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [Anzahl](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Summe](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md), und [VarP](report-builder-functions-varp-function.md) . Weitere Informationen finden Sie unter [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Referenz zu Aggregatfunktionen &#40;Berichts-Generator und SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [Tabellen &#40;Berichts-Generator und SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrizen &#40;Berichts-Generator und SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Listet &#40;Berichts-Generator und SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
