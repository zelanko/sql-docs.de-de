---
title: Hinzufügen eines Links zu einer URL (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: d3392c0b-7b62-4d27-bc04-2bd0c5487d08
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2dae0498da8fe1387b6b082d7cc6ae37af27d464
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59958532"
---
# <a name="add-a-hyperlink-to-a-url-report-builder-and-ssrs"></a>Hinzufügen eines Links zu einer URL (Berichts-Generator und SSRS)
  Sie können einem Berichtselement einen Hyperlink hinzufügen, wenn Benutzer in der Lage sein sollen, in einem Bericht auf einen Link zu klicken und einen Browser mit der von Ihnen angegebenen URL zu öffnen. Ein Link kann eine statische URL sein oder ein Ausdruck, der zu einer URL ausgewertet wird. Wenn ein Feld in einer Datenbank URLs enthält, kann der Ausdruck dieses Feld enthalten, wodurch eine dynamische Liste von Links in dem Bericht entsteht. Links können Textfeldern, Bildern, Diagrammen und Messgeräten hinzugefügt werden. Sie müssen sicherstellen, dass der Benutzer Zugriff auf die URL hat, die Sie bereitstellen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Sie können auch URLs zu Berichten auf beliebigen Berichtsservern angeben, für die Sie und Ihre Benutzer über eine Leseberechtigung verfügen, indem Sie URL-Anforderungen an den Berichtsserver verwenden. Sie können z. B. einen Bericht angeben und die Dokumentstruktur für Benutzer ausblenden, wenn diese den Bericht zum ersten Mal anzeigen. Weitere Informationen finden Sie unter [URL-Zugriff &#40;SSRS&#41;](../url-access-ssrs.md) in der [Reporting Services-Dokumentation](https://go.microsoft.com/fwlink/?linkid=121312) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
 Ein Link zu einer URL kann jedem Element hinzugefügt werden, das über eine **Action** -Eigenschaft verfügt, z. B. ein Textfeld, ein Bild oder eine berechnete Reihe in einem Diagramm. Wenn der Benutzer auf das Berichtselement klickt, wird die von Ihnen definierte Aktion ausgeführt. Weitere Informationen finden Sie unter [Aktionseigenschaften &#40;Dialogfeld, Berichts-Generator und SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) und [Angeben von Pfaden zu externen Elementen &#40;Berichts-Generator und SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
 Eine schnelle Einführung finden Sie unter [Tutorial: Formatieren von Text &#40;Berichts-Generator&#41;](../tutorial-format-text-report-builder.md).  
  
> [!NOTE]  
>  Links, die an Datasetfelder gebunden sind, sind unter Umständen anfällig für böswillige Manipulationen. Weitere Informationen finden Sie unter [Sichern von Berichten und Ressourcen](../security/secure-reports-and-resources.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-[Onlinedokumentation](https://go.microsoft.com/fwlink/?LinkId=154888) auf msdn.microsoft.com.  
  
### <a name="to-add-a-hyperlink"></a>So fügen Sie einen Link hinzu  
  
1.  Klicken Sie in der Berichtsentwurfsansicht mit der rechten Maustaste auf das Textfeld, Bild oder Diagramm, dem Sie einen Link hinzufügen möchten, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld **Eigenschaften**auf Aktion.  
  
3.  Wählen Sie **Gehe zu URL**. Im Dialogfeld für diese Option wird ein zusätzlicher Abschnitt angezeigt.  
  
4.  Geben Sie in **URL auswählen**eine URL oder einen Ausdruck ein (bzw. wählen Sie diese aus), der eine URL ergibt, oder klicken Sie auf den Dropdownpfeil, und klicken Sie auf den Namen eines Felds, das eine URL enthält.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  (Optional) Der Text wird nicht automatisch als Link formatiert. Es empfiehlt sich, die Farbe und den Effekt des Texts zu ändern, um zu verdeutlichen, dass es sich um einen Link handelt. Ändern Sie im Abschnitt **Schriftart** auf der Registerkarte "Home" des Menübands z. B. die Farbe in Blau und den Effekt in "Unterstrichen".  
  
7.  Klicken Sie zum Testen des Links auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen, und klicken Sie dann auf das Berichtselement, für das Sie den Link festgelegt haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Interaktive Sortierung, Dokumentstrukturen und Links &#40;Berichts-Generator und SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)   
 [Erstellen einer Dokumentstruktur &#40;Berichts-Generator und SSRS&#41;](create-a-document-map-report-builder-and-ssrs.md)  
  
  
