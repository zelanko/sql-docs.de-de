---
title: Einbetten eines Bilds in einen Bericht (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.embeddedimages.f1
- "10060"
ms.assetid: aed77345-5eeb-41f0-96c9-db6b4a11ec6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53aa9c9131edce40c62fbfab6899ef7531ffca01
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105963"
---
# <a name="embed-an-image-in-a-report-report-builder-and-ssrs"></a>Einbetten eines Bilds in einen Bericht (Berichts-Generator und SSRS)
  Ein Bericht kann ein eingebettetes Bild enthalten. Durch das Einbetten eines Bilds wird sichergestellt, dass das Bild immer für den Bericht verfügbar ist. Gleichzeitig nimmt allerdings die Größe der Berichtsdefinition zu; das ist die Datei, die den Bericht definiert. Die in einen Bericht eingebetteten Bilder werden im Berichtsdatenbereich aufgeführt.  
  
 Sie können ein Bild in die Berichtsdefinition einbetten, bevor Sie es der Entwurfsoberfläche hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen eines Hintergrundbilds (Berichts-Generator und SSRS)](add-a-background-image-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-a-report"></a>So betten Sie ein Bild in einen Bericht ein  
  
1.  Klicken Sie in der Berichtsentwurfsansicht auf der Registerkarte **Einfügen** auf **Bild**.  
  
2.  Klicken Sie auf die Entwurfsoberfläche, und ziehen Sie ein Feld auf die gewünschte Größe des Bilds.  
  
3.  Geben Sie im Dialogfeld **Bildeigenschaften** auf der Seite **Allgemein** einen Namen im Textfeld **Name** ein, oder übernehmen Sie den Standardnamen.  
  
4.  Geben Sie (optional) im Textfeld **QuickInfo** Text ein, der angezeigt wird, wenn der Benutzer im gerenderten Bericht auf das Bild zeigt.  
  
5.  Wählen Sie unter **Bildquelle auswählen**die Option **Eingebettet**aus.  
  
6.  Klicken Sie neben dem Textfeld **Dieses Bild verwenden** auf die Schaltfläche **Importieren** .  
  
7.  Wählen Sie unter **Dateityp**den Bilddateityp aus, navigieren Sie zu der Datei, und klicken Sie dann auf **Öffnen**.  
  
8.  Klicken Sie im Dialogfeld **Bildeigenschaften** auf **OK**.  
  
     Das Bild wird in dem auf der Entwurfsoberfläche gezeichneten Feld und die Datei unterhalb des Bildordners im Berichtsdatenbereich angezeigt.  
  
    > [!NOTE]  
    >  Der MIME-Typ (z. B. BMP) wird beim Importieren des Bilds automatisch abgeleitet. Um den MIME-Typ zu ändern, befolgen Sie die nächste Vorgehensweise.  
  
### <a name="optional-to-change-the-mime-type-of-an-imported-image"></a>(Optional) So ändern Sie den MIME-Typ eines importierten Bilds  
  
1.  Öffnen Sie den Bericht in der Entwurfsansicht.  
  
2.  Wählen Sie das Bild in der Entwurfsoberfläche aus. Der Bereich **Eigenschaften** zeigt die Bildeigenschaften an.  
  
    > [!NOTE]  
    >  Zum Anzeigen des Bereichs „Eigenschaften“ klicken Sie auf der Registerkarte **Ansicht** auf **Eigenschaften**.  
  
3.  Klicken Sie auf das Textfeld neben der **MIMEType** -Eigenschaft, und wählen Sie in der Dropdownliste einen neuen MIME-Typ aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bilder &#40;Berichts-Generator und SSRS&#41;](images-report-builder-and-ssrs.md)   
 [Hinzufügen eines datengebundenen Bilds (Berichts-Generator und SSRS)](add-a-data-bound-image-report-builder-and-ssrs.md)   
 [Bildeigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
