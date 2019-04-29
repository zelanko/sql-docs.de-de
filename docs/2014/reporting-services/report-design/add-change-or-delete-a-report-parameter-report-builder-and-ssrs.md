---
title: Hinzufügen, Ändern oder Löschen von Berichtsparametern (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: d44a8e0a-10cf-4502-9391-09743ffc9bad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f6069aba71f5c6026db2bfa083a71d923a727e50
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63206838"
---
# <a name="add-change-or-delete-a-report-parameter-report-builder-and-ssrs"></a>Hinzufügen, Ändern oder Löschen von Berichtsparametern (Berichts-Generator und SSRS)
  Mithilfe von Berichtsparametern können Sie Berichtsdaten auswählen, eine Verbindung zwischen verwandten Berichten herstellen und die Berichtspräsentation anpassen. Sie können einen Standardwert und eine Liste mit verfügbaren Werten bereitstellen, und die Benutzer können dann eine Auswahl treffen.  
  
 Nachdem ein Bericht veröffentlicht wurde, können Sie die Standardwerte, die verfügbaren Werte und andere Berichtsparametereigenschaften auf dem Berichtsserver ändern. Sie können mehrere Gruppen mit Standardparameterwerten bereitstellen, indem Sie verknüpfte Berichte erstellen. Weitere Informationen finden Sie unter "Festlegen von Parametereigenschaften für einen publizierten Bericht" in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dokumentation in der [SQL Server-Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=120955).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-or-edit-a-report-parameter"></a>So können Sie einen Berichtsparameter hinzufügen oder bearbeiten  
  
1.  Klicken Sie im Bereich **Berichtsdaten** mit der rechten Maustaste auf den Knoten **Parameter** , und klicken Sie dann auf **Parameter hinzufügen**. Das Dialogfeld **Berichtsparametereigenschaften** wird geöffnet.  
  
2.  Geben Sie unter **Name**einen Namen für den Parameter ein, oder übernehmen Sie den Standardnamen.  
  
3.  Geben Sie unter **Eingabeaufforderung**den Text ein, der neben dem Parametertextfeld angezeigt wird, wenn der Bericht ausgeführt wird.  
  
4.  Wählen Sie unter **Datentyp**den Datentyp für den Parameterwert aus.  
  
5.  Falls der Parameter einen leeren Wert enthalten darf, wählen Sie **Leeren Wert zulassen**aus.  
  
6.  Falls der Parameter einen Nullwert enthalten darf, wählen Sie **NULL-Wert zulassen**aus.  
  
7.  Falls für einen Parameter mehrere Werte ausgewählt werden dürfen, aktivieren Sie die Option **Mehrere Werte zulassen**.  
  
8.  Legen Sie die Sichtbarkeit fest.  
  
    -   Wenn der Parameter oben im Bericht auf der Symbolleiste angezeigt werden soll, wählen Sie **Sichtbar**aus.  
  
    -   Um den Parameter auszublenden und nicht auf der Symbolleiste anzuzeigen, wählen Sie **Ausgeblendet**aus.  
  
    -   Um den Parameter auszublenden und zu verhindern, dass er nach Veröffentlichung des Berichts auf dem Berichtsserver geändert wird, wählen Sie die Option **Intern**aus. Der Berichtsparameter kann dann nur in der Berichtsdefinition angezeigt werden. Bei dieser Option müssen Sie einen Standardwert festlegen oder NULL-Werte für den Parameter zulassen.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-report-parameter"></a>So löschen Sie einen Berichtsparameter  
  
1.  Erweitern Sie im Bereich **Berichtsdaten** den Knoten **Parameter** .  
  
2.  Klicken Sie mit der rechten Maustaste auf den Berichtsparameter, und klicken Sie anschließend auf **Löschen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen, Ändern oder Löschen von verfügbaren Werten für einen Berichtsparameter &#40;Berichts-Generator und SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)   
 [Hinzufügen, Ändern oder Löschen von Standardwerten für einen Berichtsparameter (Berichts-Generator und SSRS)](add-change-or-delete-default-values-for-a-report-parameter.md)   
 [Ändern der Reihenfolge von Berichtsparametern &#40;Berichts-Generator und SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)   
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Hinzufügen von kaskadierenden Parametern zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Tutorial: Hinzufügen eines Parameters zu einem Bericht (Berichts-Generator)](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Lernprogramme &#40;Berichts-Generator&#41;](../report-builder-tutorials.md)   
 [Hinzufügen von Datasetfiltern, Datenbereichsfiltern und Gruppenfiltern &#40;Berichts-Generator und SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Verweise auf Parameters-Sammlungen &#40;Berichts-Generator und SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md)   
 [Hinzufügen eines aus mehreren Werten bestehenden Parameters zu einem Bericht](add-a-multi-value-parameter-to-a-report.md)  
  
  
