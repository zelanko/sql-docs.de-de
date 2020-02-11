---
title: Hinzufügen benutzerdefinierter Orte zu einer Karte (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- MICROSOFT.REPORTDESIGNER.MAPPOINT.POINTTEMPLATE
ms.assetid: 7d36faae-5bcc-446a-9eba-f42349cafacb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ca3bf0e120cfe76aa3b58be1ca6a50991b9fb06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106648"
---
# <a name="add-custom-locations-to-a-map-report-builder-and-ssrs"></a>Hinzufügen benutzerdefinierter Orte zu einer Karte (Berichts-Generator und SSRS)
  Nachdem Sie einem Bericht eine Karte hinzugefügt haben, können Sie eigene Punktpositionen hinzufügen.  
  
 Die Anzeigeeigenschaften für alle Punkte in einer Ebene werden durch Festlegen von Optionen für die Punkteigenschaften für die Ebene gesteuert. Für einen ausgewählten eingebetteten Punkt können Sie die Anzeigeeigenschaften überschreiben.  
  
> [!NOTE]  
>  Wenn Sie die Ebenenanzeigeeigenschaften für den eingebetteten Punkt überschreiben, sind die Änderungen, die Sie vornehmen, nicht umkehrbar.  
  
 Weitere Informationen finden Sie unter [Unterschiedliche Polygon-, Linien- und Punktanzeigen bei der Verwendung von Regeln und analytischen Daten &#40;Berichts-Generator und SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-point-layer"></a>So fügen Sie eine Punktebene hinzu  
  
1.  Klicken Sie auf der Berichtsentwurfsoberfläche auf die Karte, um sie auszuwählen und den Kartenbereich anzuzeigen.  
  
2.  Klicken Sie auf der Symbolleiste auf **Ebene hinzufügen**.  
  
3.  Klicken Sie in der Dropdownliste auf **Punktebene hinzufügen**. Der Karte wird eine Punktebene ohne Punkte hinzugefügt. Standardmäßig ist die Punktebene für eingebettete Punkte bereit.  
  
### <a name="to-add-a-custom-point"></a>So fügen Sie einen benutzerdefinierten Punkt hinzu  
  
1.  Klicken Sie auf der Berichtsentwurfsoberfläche auf die Karte, um sie auszuwählen und den Kartenbereich anzuzeigen.  
  
2.  Klicken Sie im Kartenbereich mit der rechten Maustaste auf eine Punktebene, die den Typ **Eingebettet**aufweist, und klicken Sie dann auf **Punkt hinzufügen**. Der Cursor verändert sich zu einem Fadenkreuz.  
  
3.  Um einen Punkt hinzuzufügen, klicken Sie auf einen Ort auf der Karte. Der ausgewählten Ebene wird an der Position, an der Sie klicken, ein eingebetteter Punkt hinzugefügt.  
  
### <a name="to-customize-the-display-for-an-embedded-point"></a>So passen Sie die Anzeige für einen eingebetteten Punkt an  
  
1.  Klicken Sie mit der rechten Maustaste auf den Punkt, und klicken Sie dann auf **Punkteigenschaften**. Das Dialogfeld **Eigenschaften für eingebettete Punkte der Karte** wird geöffnet.  
  
2.  Klicken Sie auf **Punktoptionen für diese Ebene überschreiben**. Mehrere Eigenschaftenseiten werden im linken Bereich angezeigt.  
  
3.  Klicken Sie auf die Seiten, und legen Sie die Anzeigeeigenschaften fest, die Sie auf diesen Punkt anwenden möchten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Karten &#40;Berichts-Generator und SSRS&#41;](maps-report-builder-and-ssrs.md)   
 [Unterschiedliche Polygon-, Linien- und Punktanzeigen bei der Verwendung von Regeln und analytischen Daten &#40;Berichts-Generator und SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
