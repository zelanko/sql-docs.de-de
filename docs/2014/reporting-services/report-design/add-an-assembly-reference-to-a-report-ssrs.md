---
title: Hinzufügen eines Assemblyverweises zu einem Bericht (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23dda0c65589e55849f906c621e42ce70f0d7ab5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106757"
---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a>Hinzufügen eines Assemblyverweises zu einem Bericht (SSRS)
  Wenn Sie benutzerdefinierten Code einbetten, der Verweise auf [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Klassen enthält, die sich nicht in <xref:System.Math> oder <xref:System.Convert> befinden, müssen Sie einen Assemblyverweis auf den Bericht bereitstellen, damit der Berichtsprozessor die Namen auflösen kann. Weitere Informationen finden Sie unter [Hinzufügen von Code zu einem Bericht &#40;SSRS&#41;](add-code-to-a-report-ssrs.md).  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a>So fügen Sie einen Assemblyverweis einem Bericht hinzu  
  
1.  Klicken Sie in der **Entwurfsansicht** mit der rechten Maustaste auf die Entwurfsoberfläche außerhalb des Rahmens des Berichts, und klicken Sie auf **Berichtseigenschaften**.  
  
2.  Klicken Sie auf **Verweise**.  
  
3.  Klicken Sie in **Assemblys hinzufügen oder entfernen**auf **Hinzufügen** , und klicken Sie dann auf die Schaltfläche mit den Auslassungspunkten, um zur Assembly zu wechseln.  
  
4.  Klicken Sie unter **Klassen hinzufügen oder entfernen**auf **Hinzufügen** , und geben Sie dann den Namen der Klasse ein. Geben Sie außerdem einen Instanznamen an, der im Bericht verwendet werden soll.  
  
    > [!NOTE]  
    >  Geben Sie nur für instanzbasierte Mitglieder einen Klassen- und Instanznamen an. Geben Sie in der Liste **Klassen** keine statischen Mitglieder an. Weitere Informationen finden Sie unter [Benutzerdefinierter Code und Assemblyverweise in Ausdrücken in Berichts-Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)-Ausdruck dar.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](../custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Berichtseigenschaften (Dialogfeld), Verweise](../report-properties-dialog-box-references.md)  
  
  
