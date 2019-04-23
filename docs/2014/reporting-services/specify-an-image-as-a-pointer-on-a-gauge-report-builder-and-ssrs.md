---
title: Festlegen eines Bilds als Zeiger auf einem Messgerät (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 9d73b3c3-a068-4868-a2be-0cd261b6e92b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0bc4168d6e6cf786b3137713d44441be0bd3a13f
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59932606"
---
# <a name="specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs"></a>Festlegen eines Bilds als Zeiger auf einem Messgerät (Berichts-Generator und SSRS)
  Messgeräte enthalten drei integrierte Formate, mit denen Sie die Darstellung des Zeigers anpassen können. Für ein radiales Messgerät sind die integrierten Stile: Nadel, Marker und Balken. Für ein lineares Messgerät lauten die integrierten Stile: Marker, Balken und Thermometer. Falls ein besonderer Zeiger benötigt wird, können Benutzer ein Bild erstellen und angeben, das dann als voll funktionsfähiger Zeiger verwendet wird.  
  
 Wenn Sie ein Bild für den Zeiger auswählen, muss dieses Bild die folgenden Voraussetzungen erfüllen:  
  
-   Der Ursprung des Zeigers bzw. das Zentrum der Drehung muss am oberen Rand des Bilds liegen.  
  
-   Das Ende des Zeigers muss nach unten zeigen.  
  
 Da der Zeiger eine unregelmäßige Form aufweist, müssen Sie mit einer Transparenzfarbe die überflüssigen Teile des Bilds ausblenden. Sie können hierfür eine Farbe verwenden, die normalerweise nicht auf dem Messgerät als Transparenzfarbe angezeigt wird, da die angegebenen Farben nicht auf dem Messgerät erscheinen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-an-image-as-a-pointer-on-the-gauge"></a>So legen Sie ein Bild als Zeiger auf dem Messgerät fest  
  
1.  Klicken Sie in der Entwurfsansicht auf den Zeiger des Messgeräts.  
  
2.  (Optional) Wenn auf dem Messgerät kein Zeiger vorhanden ist, mit der Maustaste auf das Messgerät, und wählen **Zeiger hinzufügen**. Es wird ein Zeiger zum Messgerät hinzugefügt.  
  
3.  Klicken Sie auf die **einfügen** Menüband auf die Registerkarte, und doppelklicken Sie auf das Bildsymbol. Das Dialogfeld **Bildeigenschaften** wird angezeigt.  
  
4.  Fügen Sie dem Bericht ein Bild hinzu. Weitere Informationen finden Sie unter [Einbetten eines Bilds in einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md).  
  
5.  Öffnen Sie den Bereich Eigenschaften.  
  
6.  Klicken Sie auf der Entwurfsoberfläche auf den Zeiger. Die Eigenschaften für den Zeiger werden im Eigenschaftenbereich angezeigt.  
  
7.  Erweitern Sie den PointerImage-Knoten.  
  
8.  In **Quelle**Option **eingebettete** aus der Dropdown-Liste.  
  
    > [!NOTE]  
    >  Falls das Bild in der Datenbank oder im Web gespeichert ist, wählen Sie die entsprechende Option für diese Eigenschaft aus. Weitere Informationen finden Sie unter [im Dialogfeld "Eigenschaften" Image "," Allgemein &#40;Berichts-Generator und SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md).  
  
9. In **Wert**, wählen Sie den Namen des Images aus der Dropdown-Liste.  
  
10. In **TransparentColor**, wählen Sie einen Farbwert aus, die Sie aus dem Image entfernen möchten. Dies führt zu einer gleichmäßigen Darstellung des Zeigers auf dem Messgerät.  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren von Zeigern auf einem Messgerät (Berichts-Generator und SSRS)](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Hinzufügen eines Messgeräts zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md)   
 [Formatieren von Linien, Farben und Bildern (Berichts-Generator und SSRS)](report-design/images-report-builder-and-ssrs.md)   
 [Messgeräte &#40;Berichts-Generator und SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md)  
  
  
