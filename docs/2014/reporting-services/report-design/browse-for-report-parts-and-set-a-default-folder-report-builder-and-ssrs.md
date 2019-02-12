---
title: Suchen nach Berichtsteilen und Festlegen eines Standardordners (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5cf38068-65d1-4fe8-81f3-a404d8fbc663
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae8fddf7e008c1c97c30c18deb2d8aec60b77415
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56009582"
---
# <a name="browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs"></a>Suchen nach Berichtsteilen und Festlegen eines Standardordners (Berichts-Generator und SSRS)
  Die einfachste Möglichkeit, einen Bericht zu erstellen, besteht darin, vorhandene Berichtsteile wie Tabellen und Diagramme dem Bericht mithilfe des Berichtsteilkatalogs hinzuzufügen. Wenn Sie dem Bericht einen Berichtsteil hinzufügen, werden damit auch alle für die Verarbeitung erforderlichen Elemente hinzugefügt. Beispielsweise ist jeder Berichtsteil von einem Dataset (d. h., einer Abfrage und einer Verbindung zu einer Datenquelle) abhängig. Nachdem Sie dem Bericht den Berichtsteil hinzugefügt haben, können Sie diesen nach Bedarf ändern.  
  
 Sie können einen Standardordner für das Veröffentlichen von Berichtsteilen auf dem Berichtsserver oder auf einer in einen Berichtsserver integrierten SharePoint-Website festlegen.  
  
 Weitere Informationen finden Sie unter [Berichtsteile &#40;Berichts-Generator und SSRS&#41;](../report-parts-report-builder-and-ssrs.md).  
  
### <a name="to-browse-for-report-parts"></a>So suchen Sie nach Berichtsteilen  
  
1.  Klicken Sie im Menü **Einfügen** auf **Berichtsteile**.  
  
     Wurde noch keine Verbindung hergestellt, klicken Sie auf **Stellen Sie eine Verbindung mit einem Berichtsserver her**, und geben Sie den Namen des Berichtsservers ein.  
  
    > [!NOTE]  
    >  Für die Suche nach Berichtsteilen muss eine Verbindung mit einem Berichtsserver bestehen.  
  
2.  Sie können die Suche eingrenzen, indem Sie Details zum Berichtsteil angeben. Geben Sie Namen und Beschreibung ganz oder teilweise in das Feld **Suchen** ein, oder klicken Sie auf **Kriterien hinzufügen** , und fügen Sie Werte für einige oder alle diese Felder hinzu:  
  
    -   Erstellt von  
  
    -   Erstellt am  
  
    -   Datum der letzten Änderung  
  
    -   Zuletzt geändert von  
  
    -   Serverordner  
  
    -   Typ  
  
     Klicken Sie zum Suchen nach einem Bild beispielsweise auf **Kriterien hinzufügen**und anschließend auf **Typ**. Aktivieren Sie im Dropdownfeld das Kontrollkästchen **Bild** , drücken Sie die EINGABETASTE, und klicken Sie anschließend auf die Suchlupe.  
  
    > [!NOTE]  
    >  Suchen Sie für die Werte **Erstellt von** und **Zuletzt geändert von** nach dem Benutzernamen der Person, wie er auf dem Berichtsserver angegeben ist.  
  
### <a name="to-set-a-default-folder-for-report-parts"></a>So legen Sie einen Standardordner für Berichtsteile fest  
  
1.  Klicken Sie auf **Berichts-Generator**, und klicken Sie dann auf **Optionen**.  
  
2.  Geben Sie im Dialogfeld **Optionen** auf der Registerkarte **Einstellungen** einen Ordnernamen in das Textfeld **Berichtselemente standardmäßig in diesem Ordner veröffentlichen** ein.  
  
 Der Berichts-Generator erstellt diesen Ordner, wenn er noch nicht vorhanden ist und Sie über die Berechtigung verfügen, Ordner auf dem Berichtsserver zu erstellen.  
  
 Sie müssen den Berichts-Generator nicht neu starten, damit diese Einstellung wirksam wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Suchen Sie nach Updates oder Deaktivieren von Updates, deaktiviert &#40;Berichts-Generator und SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md)   
 [Berichtsteile &#40;Berichts-Generator und SSRS&#41;](../report-parts-report-builder-and-ssrs.md)   
 [Berichtsteile und Datasets in Berichts-Generator](../report-data/report-parts-and-datasets-in-report-builder.md)   
 [Problembehandlung bei Berichtsteilen &#40;Berichts-Generator und SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md)   
 [Veröffentlichen und erneutes Veröffentlichen von Berichtsteilen &#40;Berichts-Generator und SSRS&#41;](publish-and-republish-report-parts-report-builder-and-ssrs.md)  
  
  
