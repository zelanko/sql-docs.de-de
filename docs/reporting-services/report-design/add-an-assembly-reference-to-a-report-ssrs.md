---
title: Hinzufügen eines Assemblyverweises zu einem Bericht | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie einem Bericht einen Assemblyverweis hinzufügen, damit der Berichtsprozessor Namen im Berichts-Generator auflösen kann.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
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
ms.openlocfilehash: 8bbad43a5aa0339ccc13002073facf54de729a58
ms.sourcegitcommit: 02b22274da4a103760a376c4ddf26c4829018454
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2020
ms.locfileid: "84681209"
---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a>Hinzufügen eines Assemblyverweises zu einem Bericht (SSRS)
  Wenn Sie benutzerdefinierten Code einbetten, der Verweise auf [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Klassen enthält, die sich nicht in <xref:System.Math> oder <xref:System.Convert> befinden, müssen Sie einen Assemblyverweis auf den Bericht bereitstellen, damit der Berichtsprozessor die Namen auflösen kann. Weitere Informationen finden Sie unter [Hinzufügen von Code zu einem Bericht &#40;SSRS&#41;](../../reporting-services/report-design/add-code-to-a-report-ssrs.md).  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a>So fügen Sie einen Assemblyverweis einem Bericht hinzu  
  
1.  Klicken Sie in der **Entwurfsansicht** mit der rechten Maustaste auf die Entwurfsoberfläche außerhalb des Rahmens des Berichts, und klicken Sie auf **Berichtseigenschaften**.  
  
2.  Klicken Sie auf **Verweise**.  
  
3.  Klicken Sie in **Assemblys hinzufügen oder entfernen**auf **Hinzufügen** , und klicken Sie dann auf die Schaltfläche mit den Auslassungspunkten, um zur Assembly zu wechseln.  
  
4.  Klicken Sie unter **Klassen hinzufügen oder entfernen**auf **Hinzufügen** , und geben Sie dann den Namen der Klasse ein. Geben Sie außerdem einen Instanznamen an, der im Bericht verwendet werden soll.  
  
    > [!NOTE]  
    >  Geben Sie nur für instanzbasierte Mitglieder einen Klassen- und Instanznamen an. Geben Sie in der Liste **Klassen** keine statischen Mitglieder an. Weitere Informationen finden Sie unter [Benutzerdefinierter Code und Assemblyverweise in Ausdrücken in Berichts-Designer &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)-Ausdruck dar.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Berichtseigenschaften (Dialogfeld), Verweise](https://msdn.microsoft.com/library/4639d368-9918-4bb1-9953-7a724ca78dea)  
  
  
