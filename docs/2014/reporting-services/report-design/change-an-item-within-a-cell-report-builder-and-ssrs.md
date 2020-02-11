---
title: Ändern eines Elements in einer Zelle (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7676145c7f1beb28f2d6abedf57c3c33d1a41c9f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106351"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Bilder, Textfelder, Rechtecke und Linien &#40;Berichts-Generator und SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
