---
title: Angeben eines Bilds als Zeiger auf einem Messgerät (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d73b3c3-a068-4868-a2be-0cd261b6e92b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c7a57987a5d1cd0ac7984db3b716521d9c7a09af
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66101145"
---
# <a name="specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs"></a>Festlegen eines Bilds als Zeiger auf einem Messgerät (Berichts-Generator und SSRS)
  Messgeräte enthalten drei integrierte Formate, mit denen Sie die Darstellung des Zeigers anpassen können. Für ein radiales Messgerät lauten die integrierten Stile: Nadel, Marker und Balken. Für ein lineares Messgerät lauten die integrierten Stile: Marker, Balken und Thermometer. Falls ein besonderer Zeiger benötigt wird, können Benutzer ein Bild erstellen und angeben, das dann als voll funktionsfähiger Zeiger verwendet wird.  
  
 Wenn Sie ein Bild für den Zeiger auswählen, muss dieses Bild die folgenden Voraussetzungen erfüllen:  
  
-   Der Ursprung des Zeigers bzw. das Zentrum der Drehung muss am oberen Rand des Bilds liegen.  
  
-   Das Ende des Zeigers muss nach unten zeigen.  
  
 Da der Zeiger eine unregelmäßige Form aufweist, müssen Sie mit einer Transparenzfarbe die überflüssigen Teile des Bilds ausblenden. Sie können hierfür eine Farbe verwenden, die normalerweise nicht auf dem Messgerät als Transparenzfarbe angezeigt wird, da die angegebenen Farben nicht auf dem Messgerät erscheinen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-an-image-as-a-pointer-on-the-gauge"></a>So legen Sie ein Bild als Zeiger auf dem Messgerät fest  
  
1.  Klicken Sie in der Entwurfsansicht auf den Zeiger des Messgeräts.  
  
2.  Optionale Wenn auf dem Messgerät kein Zeiger vorhanden ist, klicken Sie mit der rechten Maustaste auf das Messgerät, und wählen Sie **Zeiger hinzufügen**aus. Es wird ein Zeiger zum Messgerät hinzugefügt.  
  
3.  Klicken Sie im Menüband auf die Registerkarte **Einfügen** , und doppelklicken Sie auf das Bildsymbol. Das Dialogfeld **Bildeigenschaften** wird angezeigt.  
  
4.  Fügen Sie dem Bericht ein Bild hinzu. Weitere Informationen finden Sie unter [Einbetten eines Bilds in einen Bericht &#40;Berichts-Generator und SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md).  
  
5.  Öffnen Sie den Bereich Eigenschaften.  
  
6.  Klicken Sie auf der Entwurfsoberfläche auf den Zeiger. Die Eigenschaften für den Zeiger werden im Eigenschaftenbereich angezeigt.  
  
7.  Erweitern Sie den Knoten PointerImage.  
  
8.  Wählen Sie unter **Quelle**die Option **eingebettet** aus der Dropdown Liste aus.  
  
    > [!NOTE]  
    >  Falls das Bild in der Datenbank oder im Web gespeichert ist, wählen Sie die entsprechende Option für diese Eigenschaft aus. Weitere Informationen finden Sie unter [Bildeigenschaften (Dialog Feld), allgemein &#40;Berichts-Generator und SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md).  
  
9. Wählen Sie unter **Wert**den Namen des Images aus der Dropdown Liste aus.  
  
10. Wählen Sie in **TransparentColor**einen Farbwert aus, den Sie aus dem Bild entfernen möchten. Dies führt zu einer gleichmäßigen Darstellung des Zeigers auf dem Messgerät.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Zeigern auf einem Messgerät &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Hinzufügen eines Messgerätes zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md)   
 [Formatieren von Linien, Farben und Bildern &#40;Berichts-Generator und SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Messgeräte &#40;Berichts-Generator und SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md)  
  
  
