---
title: Ausfüllen (Dialog Feld) (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportbody.fill.f1
- "10065"
- "10501"
- sql12.rtp.rptdesigner.shared.filldv.f1
- sql12.rtp.rptdesigner.rectangleproperties.fill.f1
- "10064"
- sql12.rtp.rptdesigner.textboxproperties.fill.f1
- "10124"
ms.assetid: 93a91d02-d558-4a0e-8d17-3fdf21e208d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86f54b00e530e70d1952461ce7b98b9238e4c3f3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109161"
---
# <a name="fill-dialog-box-report-builder-and-ssrs"></a>Ausfüllen (Dialogfeld) (Berichts-Generator und SSRS)
  Auf der Registerkarte **Ausfüllen** können Sie Farboptionen für den Hintergrund einer oder mehrerer Zellen in einem Datenbereich oder einem Textfeld angeben.  
  
## <a name="options"></a>Optionen  
 **Füllfarbe**  
 Klicken Sie auf die Farbschaltfläche, um eine Füllfarbe für das Rechteck auszuwählen. Klicken Sie auf die Ausdrucksschaltfläche (**fx**), um den _Ausdruck_ zu bearbeiten. Hierbei kann es sich um einen Hexadezimalwert für die RGB-Farbe oder eine der vordefinierten Farben im Dialogfeld **Ausdruck** handeln. Um eine Liste vordefinierter Farben anzuzeigen, wählen Sie **Web** im Bereich **Element**aus. Die im Bereich **Titel** aufgelisteten Farbnamen können in den Ausdruckstextbereich eingegeben werden. Verwenden Sie bei der Eingabe des Farbnamens kein Gleichheitszeichen (=) oder Anführungszeichen ("").  
  
 **Bildquelle auswählen**  
 Geben Sie den Speicherort des Bilds an, sodass der Berichtsprozessor dieses beim Rendern des Berichts anzeigen kann.  
  
-   **Extern** Wählen Sie diese Option aus, wenn das Bild als Datei auf einem Berichtsserver oder Webserver gespeichert bleiben soll.  
  
-   **Eingebettet** Wählen Sie diese Option aus, wenn Sie das Bild in den Bericht einbetten möchten.  
  
-   **Datenbank** Wählen Sie diese Option aus, wenn Sie einen Datenbankfeldnamen für die Bilder, die in Ihrem Bericht enthalten sein sollen, einschließen möchten.  
  
 **Dieses Bild verwenden**  
 Diese Option wird angezeigt, wenn Sie die Option **Eingebettet** oder **Extern** auswählen.  
  
 Wenn Sie das Bild einbetten, wählen Sie das Bild, das Sie zum Bericht hinzufügen möchten, in der Dropdownliste aus. Klicken Sie auf **Importieren** , um das Bild der Dropdownliste hinzuzufügen. Wenn Sie ein Bild im Bereich **Daten** hinzugefügt haben, können Sie dieses Bild auswählen, indem Sie auf die Option **Eingebettet** klicken und das Bild in der Dropdownliste auswählen.  
  
 Wenn Sie die Option **Extern** aktivieren, geben Sie die URL des Bilds ein. Verwenden Sie für einen Bericht, der auf einem für den einheitlichen Modus konfigurierten Berichts Server veröffentlicht werden soll, einen vollständigen oder relativen Pfad (z. b. http://*\<Servername>*/images/image1.jpg). Verwenden Sie für einen Bericht, der auf einem im integrierten SharePoint-Modus konfigurierten Berichts Server veröffentlicht wurde, eine voll qualifizierte URL (z. b. http://*\<SharePointServerName>/\<Site>*/Documents/images/image1.jpg).  
  
 **Importieren**  
 Diese Option ist verfügbar, wenn Sie **Eingebettet**auswählen. Klicken Sie auf diese Schaltfläche, um der Dropdownliste **Dieses Bild verwenden** ein Bild hinzuzufügen.  
  
 **Dieses Feld verwenden**  
 Diese Option ist verfügbar, wenn Sie **Datenbank**auswählen. Wählen Sie den Feldnamen aus.  
  
 **Diesen MIME-Typ verwenden**  
 Wählen Sie das entsprechende Format der in der Datenbank enthaltenen Bilder aus (z. B. BMP, JPEG, GIF, PNG oder X-PNG).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Berichts Elementen &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Formatieren von Text und Platzhaltern &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Bilder &#40;Berichts-Generator und SSRS&#41;](report-design/images-report-builder-and-ssrs.md)  
  
  
