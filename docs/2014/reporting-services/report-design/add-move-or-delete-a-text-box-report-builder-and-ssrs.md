---
title: Hinzufügen, Verschieben oder Löschen von Textfeldern (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: f042cf81-d933-4ac7-9287-c074a46bde98
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2736c28c69491f18abd6c999cc3ac22071698da1
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56294468"
---
# <a name="add-move-or-delete-a-text-box-report-builder-and-ssrs"></a>Hinzufügen, Verschieben oder Löschen von Textfeldern (Berichts-Generator und SSRS)
  Textfelder sind das am häufigsten verwendete Berichtselement in Berichten. Sie können dem Hauptteil des Berichts ein Textfeld hinzufügen, um Informationen wie beispielsweise Titel, Parameterauswahlen, integrierte Felder und Datumsangaben anzuzeigen.  
  
 Jede Zelle in einer Tabelle oder Matrix ist in Wirklichkeit ein Textfeld. Die in einem Bericht mit Tabellen und Matrizen angezeigten Berichtsdaten ergeben sich fast alle aus der Auswertung des Inhalts der einzelnen Textfelder im Bericht durch den Berichtsprozessor. Sie können Zellen genau so formatieren, wie Sie andere Textfelder außerhalb des Datenbereichs formatieren würden.  
  
 Um einem Listendatenbereich ein Textfeld hinzuzufügen, müssen Sie zuerst das Textfeld hinzufügen und dann in die Liste ziehen.  
  
> [!NOTE]  
>  Wenn Sie auf ein Textfeld klicken, bearbeiten Sie sofort den Text im Textfeld. Um das Textfeld selbst auszuwählen, und nicht den Text in dem Textfeld, drücken Sie ESC.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-text-box"></a>So fügen Sie ein Textfeld hinzu  
  
1.  Klicken Sie in der Entwurfsansicht in der Registerkarte **Einfügen** auf **TextBox**.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf ein Feld, und ziehen Sie es auf die gewünschte Textfeldgröße. Alternativ können Sie auf die Entwurfsoberfläche klicken, um ein Textfeld mit der Standardgröße zu erstellen.  
  
### <a name="to-add-a-text-box-in-a-list"></a>So fügen Sie ein Textfeld in einer Liste hinzu  
  
1.  Klicken Sie in der Berichtsentwurfsansicht auf der Registerkarte **Einfügen** auf **Liste**.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf ein Feld, und ziehen Sie es auf die gewünschte Größe der Liste. Alternativ können Sie auf die Entwurfsoberfläche klicken, um eine Liste mit der Standardgröße zu erstellen.  
  
3.  Klicken Sie auf der Registerkarte **Einfügen** auf **Textfeld**.  
  
4.  Klicken Sie auf die Entwurfsoberfläche, und ziehen Sie dann in der Liste, die Sie in Schritt 1 hinzugefügt haben, ein Feld auf die gewünschte Textfeldgröße. Alternativ können Sie auf der Entwurfsoberfläche in die Liste klicken, um ein Textfeld mit der Standardgröße zu erstellen.  
  
5.  Wählen Sie das Textfeld aus, um zu überprüfen, ob es richtig in der Liste eingebettet ist.  
  
    > [!NOTE]  
    >  Wenn Sie im Bearbeitungsmodus in das Textfeld klicken, drücken Sie ESC, um das Textfeld zu wählen.  
  
6.  Prüfen Sie im Eigenschaftenbereich, ob die **Parent** -Eigenschaft dem Rechteck entspricht, das dem Listendatenbereich automatisch hinzugefügt wurde.  
  
    > [!NOTE]  
    >  Falls der Bereich „Eigenschaften“ nicht angezeigt wird, aktivieren Sie auf der Registerkarte **Ansicht** die Option **Eigenschaften** .  
  
### <a name="to-move-a-text-box"></a>So verschieben Sie ein Textfeld  
  
1.  Klicken Sie in der Berichtsentwurfssicht auf eine leere Stelle im Textfeld, um das Textfeld auszuwählen.  
  
    > [!NOTE]  
    >  Wenn Sie im Bearbeitungsmodus in das Textfeld klicken, drücken Sie ESC, um das Textfeld zu wählen.  
  
2.  Klicken Sie auf den Textfeldziehpunkt, und ziehen Sie das Textfeld an die neue Position. Alternativ können Sie die Pfeiltasten verwenden, um das ausgewählte Textfeld horizontal oder vertikal zu verschieben. Um das Textfeld in kleineren Schritten auf der Entwurfsoberfläche zu verschieben, verwenden Sie die Pfeiltasten mit gedrückter STRG-TASTE.  
  
### <a name="to-delete-a-text-box"></a>So löschen Sie ein Textfeld  
  
1.  Klicken Sie in der Berichtsentwurfssicht mit der rechten Maustaste auf eine leere Stelle im Textfeld, um das Textfeld auszuwählen, und klicken Sie dann auf **Löschen**. Oder klicken Sie auf eine leere Stelle im Textfeld, und drücken Sie dann die ENTF-Taste.  
  
    > [!NOTE]  
    >  Wenn Sie im Bearbeitungsmodus in das Textfeld klicken, drücken Sie ESC, um das Textfeld zu wählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Textfelder &#40;Berichts-Generator und SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Tastenkombinationen &#40;Berichts-Generator&#41;](../report-builder/keyboard-shortcuts-report-builder.md)  
  
  
