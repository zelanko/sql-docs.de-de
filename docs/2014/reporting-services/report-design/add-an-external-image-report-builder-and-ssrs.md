---
title: Hinzufügen eines externen Bilds (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 58875d6b3fd43962929096912d46f8157f02b77b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056414"
---
# <a name="add-an-external-image-report-builder-and-ssrs"></a>Hinzufügen eines externen Bilds (Berichts-Generator und SSRS)
  Externe Bilder können auf einem Berichtsserver im einheitlichen Modus bzw. im integrierten SharePoint-Modus oder auf einer beliebigen anderen Website gespeichert sein. Wenn Sie externe Bilder im Bericht verwenden, müssen Sie prüfen, ob das Bild vorhanden ist und ob der Leser des Berichts Zugriffsberechtigungen für das Bild hat. Weitere Informationen finden Sie unter [Bilder &#40;Berichts-Generator und SSRS&#41;](images-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a>So fügen Sie ein externes Bild hinzu  
  
1.  Klicken Sie in der Berichtsentwurfsansicht auf der Registerkarte **Einfügen** auf **Bild**.  
  
2.  Klicken Sie auf die Entwurfsoberfläche, und ziehen Sie ein Feld auf die gewünschte Größe des Bilds.  
  
3.  Geben Sie im Dialogfeld **Bildeigenschaften** auf der Registerkarte **Allgemein** einen Namen im Textfeld **Name** ein, oder übernehmen Sie den Standardnamen.  
  
4.  (Optional) Geben Sie im Textfeld **QuickInfo** Text ein, der angezeigt wird, wenn der Benutzer in einem in HTML gerenderten Bericht auf das Bild zeigt.  
  
5.  Wählen Sie unter **Bildquelle auswählen**die Option **Extern**aus.  
  
     Wenn ein Bild auf einem Berichtsserver im einheitlichen Modus gespeichert ist, geben Sie im Feld **Dieses Bild verwenden** einen relativen Pfad zu dem Bild ein – beispielsweise „../images/image1.jpg“.  
  
     Um ein Bild auf einem Berichtsserver im integrierten SharePoint-Modus oder in einer beliebigen anderen Website zu verwenden, geben Sie im Feld **Dieses Bild verwenden** eine vollständige URL zum Bild ein – beispielsweise „http://\<SharePointservername>/\<site>/Documents/images/image1.jpg“.  
  
     Weitere Informationen finden Sie unter [Angeben von Pfaden zu externen Elementen &#40;Berichts-Generator und SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
6.  (Optional) Klicken Sie auf **Größe**, **Sichtbarkeit**, **Aktion**oder **Rahmen** , um weitere Eigenschaften für das Bildberichtselement festzulegen.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Einbetten eines Bilds in einem Bericht &#40;Berichts-Generator und SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Hinzufügen eines Hintergrundbilds (Berichts-Generator und SSRS)](add-a-background-image-report-builder-and-ssrs.md)   
 [Bildeigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  