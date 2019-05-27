---
title: Exportieren eines Berichts in ein anderes Dateiformat (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b577568b-ecbd-44c3-be88-31dab6fc38a2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6da8c1190c07d3df930a2d83937e3a5ec39da32
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66109179"
---
# <a name="export-a-report-as-another-file-type-report-builder-and-ssrs"></a>Exportieren eines Berichts in ein anderes Dateiformat (Berichts-Generator und SSRS)
  Sie können einen Bericht in einem anderen Dateiformat wie CSV, Image, PDF, [!INCLUDE[ofprword](../includes/ofprword-md.md)]oder [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]rendern, während Sie die Vorschau für den Bericht im Berichts-Generator oder Berichts-Designer anzeigen. Sie können den Bericht aber auch rendern, während Sie den Bericht auf dem Berichtsserver anzeigen. Das Rendern des Berichts in ein bestimmtes Format ist sinnvoll, wenn Sie den Bericht sofort als anderen Dateityp speichern möchten, ohne ihn auf dem Berichtsserver zu veröffentlichen, oder wenn Sie sehen möchten, wie Ihr Berichtsentwurf den Lesern in einem bestimmten Format angezeigt wird. Das Rendern des Berichts auf dem Berichtsserver ist sinnvoll, wenn Sie Abonnements einrichten, Berichte per E-Mail bereitstellen oder einen Bericht speichern möchten, der auf dem Berichtsserver verfügbar ist. Weitere Informationen finden Sie unter [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-export-a-report-as-another-file-type-in-report-builder"></a>So exportieren Sie einen Bericht mit einem anderen Dateityp im Berichts-Generator  
  
1.  Zeigen Sie eine Vorschau des Berichts an.  
  
2.  Klicken Sie im Menüband auf **Exportieren**.  
  
3.  Wählen Sie das Format aus, das Sie verwenden möchten.  
  
     Das Dialogfeld **Speichern unter** wird geöffnet. Standardmäßig entspricht der Dateiname dem Namen des exportierten Berichts. Optional können Sie den Dateinamen ändern.  
  
4.  Navigieren Sie zur Position, an der Sie den exportierten Bericht gespeichert haben, und öffnen Sie ihn.  
  
> [!NOTE]  
>  Wenn das Programm den Bericht nicht im gewählten Format öffnen kann, weil diesem Dateityp kein Programm zugeordnet ist, werden Sie aufgefordert, den exportierten Bericht zu speichern oder im Internet ein Programm zum Öffnen des Berichts zu suchen.  
  
### <a name="to-export-a-report-as-another-file-type-in-report-manager"></a>So exportieren Sie einen Bericht als anderen Dateityp im Berichts-Manager  
  
1.  Navigieren Sie auf der Seite **Home** vom Berichts-Manager aus zum Bericht, den Sie exportieren möchten.  
  
2.  Klicken Sie auf den Bericht.  
  
     Der Bericht wird generiert.  
  
3.  Klicken Sie auf der Berichts-Viewer-Symbolleiste auf den Dropdownpfeil **Format auswählen** .  
  
4.  Wählen Sie das Format aus, das Sie verwenden möchten.  
  
5.  Klicken Sie auf **Exportieren**.  
  
     Eine Meldung wird angezeigt, und Sie werden gefragt, ob Sie die Datei öffnen oder speichern möchten.  
  
6.  Klicken Sie auf **Öffnen**, um den Bericht im ausgewählten Exportformat anzuzeigen.  
  
     \- oder –  
  
     Klicken Sie auf **Speichern**, um den Bericht sofort im ausgewählten Exportformat zu speichern.  
  
     Der Bericht wird mit der Anwendung, die dem von Ihnen gewählten Format zugeordnet ist, entweder angezeigt oder gespeichert. Wenn Sie auf **Speichern**klicken, werden Sie aufgefordert, einen Speicherort für Ihren Bericht anzugeben.  
  
     **Hinweis** Wenn das Programm den Bericht nicht im gewählten Format öffnen kann, weil diesem Dateityp kein Programm zugeordnet ist, werden Sie aufgefordert, den exportierten Bericht zu speichern oder im Internet ein Programm zum Öffnen des Berichts zu suchen.  
  
### <a name="to-export-a-report-as-another-file-type-in-a-sharepoint-library"></a>So exportieren Sie einen Bericht als anderen Dateityp in eine SharePoint-Bibliothek  
  
1.  Zeigen Sie eine Vorschau des Berichts an.  
  
2.  Klicken Sie auf der Symbolleiste auf **Aktionen**, zeigen Sie auf **Exportieren**, und wählen Sie dann das Format aus, das Sie verwenden möchten.  
  
     Das Dialogfeld **Dateidownload** wird geöffnet.  
  
3.  Klicken Sie auf **Öffnen**, um den Bericht im ausgewählten Exportformat anzuzeigen.  
  
     \- oder –  
  
     Klicken Sie auf **Speichern**, um den Bericht sofort im ausgewählten Exportformat zu speichern.  
  
     Der Bericht wird mit der Anwendung, die dem von Ihnen gewählten Format zugeordnet ist, entweder angezeigt oder gespeichert. Wenn Sie auf **Speichern**klicken, werden Sie aufgefordert, einen Speicherort für Ihren Bericht anzugeben.  
  
     Sie können den Dateinamen des exportierten Berichts ändern.  
  
     **Hinweis** Wenn das Programm den Bericht nicht im gewählten Format öffnen kann, weil diesem Dateityp kein Programm zugeordnet ist, werden Sie aufgefordert, den exportierten Bericht zu speichern oder im Internet ein Programm zum Öffnen des Berichts zu suchen.  
  
## <a name="see-also"></a>Siehe auch  
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)   
 [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen &#40;Berichts-Generator und SSRS&#41;](report-builder/interactive-functionality-different-report-rendering-extensions.md)  
  
  
