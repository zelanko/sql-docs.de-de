---
title: Hinzufügen eines externen Bilds (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a66fe9816a94281e6153162ec573d95b6629496e
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59935366"
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
  
     Wenn ein Bild auf einem Berichtsserver im einheitlichen Modus gespeichert ist, geben Sie im Feld **Dieses Bild verwenden** einen relativen Pfad zu dem Bild ein, z.B. „../images/image1.jpg“.  
  
     Geben Sie für ein Bild auf einem Berichtsserver im integrierten SharePoint-Modus oder einer beliebigen anderen Website, eine vollständige URL für das Bild in der **dieses Bild verwenden** Box-z. B. http://\<SharePointservername > /\<Site > / Documents/Images/Image1.jpg.  
  
     Weitere Informationen finden Sie unter [Angeben von Pfaden zu externen Elementen &#40;Berichts-Generator und SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
6.  (Optional) Klicken Sie auf **Größe**, **Sichtbarkeit**, **Aktion**oder **Rahmen** , um weitere Eigenschaften für das Bildberichtselement festzulegen.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Einbetten eines Bilds in einen Bericht &#40;Berichts-Generator und SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Hinzufügen eines Hintergrundbilds &#40;Berichts-Generator und SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md)   
 [Bildeigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
