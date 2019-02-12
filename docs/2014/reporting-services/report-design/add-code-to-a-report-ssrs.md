---
title: Hinzufügen von Code zu einem Bericht (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2f117c8ba2bc933747c725662100cf438dcd67a1
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027900"
---
# <a name="add-code-to-a-report-ssrs"></a>Hinzufügen von Code zu einem Bericht (SSRS)
  Sie können in jedem beliebigen Ausdruck einen eigenen benutzerdefinierten Code aufrufen. Sie können Code auf folgende zwei Arten bereitstellen:  
  
-   Betten Sie in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] geschriebenen Code direkt in Ihren Bericht ein. Falls der Code auf ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] verweist, das nicht <xref:System.Math> oder <xref:System.Convert>ist, müssen Sie dem Bericht den Verweis hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen eines Assemblyverweises zu einem Bericht &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md). Weitere Informationen zu anderen Verweisen finden Sie unter [Benutzerdefinierter Code und Assemblyverweise in Ausdrücken in Berichts-Designer (SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
-   Stellen Sie mit dem [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]eine benutzerdefinierte Codeassembly bereit. Wenn Sie eine benutzerdefinierte Assembly bereitstellen, müssen Sie sie sowohl auf dem Computer, auf dem Sie den Bericht schreiben, als auch auf dem Berichtsserver, auf dem Sie den Bericht anzeigen, installieren. Weitere Informationen finden Sie unter [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md).  
  
### <a name="to-add-embedded-code-to-a-report"></a>So fügen Sie einem Bericht eingebetteten Code hinzu  
  
1.  Klicken Sie in der **Entwurfsansicht** mit der rechten Maustaste auf die Entwurfsoberfläche außerhalb des Rahmens des Berichts, und klicken Sie auf **Berichtseigenschaften**.  
  
2.  Klicken Sie auf **Code**.  
  
3.  Geben Sie den Code unter **Benutzerdefinierter Code**ein. Fehler im Code erzeugen Warnungen, wenn der Bericht ausgeführt wird. Im folgenden Beispiel wird eine benutzerdefinierte Funktion namens `ChangeWord` erstellt, die das Wort "`Bike`" mit "`Bicycle`" ersetzt.  
  
    ```  
    Public Function ChangeWord(ByVal s As String) As String  
       Dim strBuilder As New System.Text.StringBuilder(s)  
       If s.Contains("Bike") Then  
          strBuilder.Replace("Bike", "Bicycle")  
          Return strBuilder.ToString()  
          Else : Return s  
       End If  
    End Function  
    ```  
  
4.  Im folgenden Beispiel wird gezeigt, wie ein Datasetfeld namens Kategorie in einem Ausdruck an diese Funktion übergeben wird:  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     Wenn Sie diesen Ausdruck einer Tabellenzelle hinzufügen, in der Kategoriewerte angezeigt werden, wird, wenn das Wort "Bike" im Datasetfeld für diese Zeile enthalten ist, stattdessen das Wort "Bicycle" als Tabellenzellenwert angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtseigenschaften (Dialogfeld), Code](../report-properties-dialog-box-code.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Verweise auf Parametersammlungen &#40;Berichts-Generator und SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
