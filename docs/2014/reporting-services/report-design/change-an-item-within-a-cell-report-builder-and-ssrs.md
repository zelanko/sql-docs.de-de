---
title: Ändern eines Elements in einer Zelle (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 9461a5cdfaf6b10d229380681b626ff2a6172bf1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148103"
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a>Ändern eines Elements in einer Zelle (Berichts-Generator und SSRS)
  Nur ein Nichtcontainerelement, z. B. ein Textfeld, eine Zeile oder ein Bild, kann durch ein neues Berichtselement ersetzt werden. Sie können beispielsweise eine Tabelle in ein Textfeld ziehen, um das Textfeld durch eine Tabelle zu ersetzen.  
  
 Enthält die Zelle ein Containerelement, wie z. B. ein Rechteck, eine Liste, eine Tabelle oder eine Matrix, wird das neue Element zum enthaltenen Element hinzugefügt, anstatt es zu ersetzen. Um ein Containerelement durch ein neues Element zu ersetzen, löschen Sie den Container. Beim Löschen des Containerelements wird dafür ein Textfeld eingefügt, das Sie durch ein anderes Element ersetzen können.  
  
 Standardmäßig enthalten alle Zellen in einem Tabellen-, Matrix- oder Listendatenbereich ein Textfeld.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-an-item-within-a-cell"></a>So ändern Sie ein Element in einer Zelle  
  
-   Klicken Sie auf der Registerkarte **Einfügen** in der Gruppe **Datenbereiche** oder **Berichtselemente** auf das Element, das Sie dem Bericht hinzufügen möchten, und klicken Sie dann auf den Bericht. Das Element wird dem Bericht hinzugefügt.  
  
> [!NOTE]  
>  Das Dialogfeld **Bildeigenschaften** wird geöffnet, wenn Sie ein Bildberichtselement in eine Zelle ziehen, in der Sie Eigenschaften wie die Quelle des Bilds festlegen können, bevor das Bild der Zelle hinzugefügt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Bilder, Textfelder, Rechtecke und Linien &#40;Berichts-Generator und SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  