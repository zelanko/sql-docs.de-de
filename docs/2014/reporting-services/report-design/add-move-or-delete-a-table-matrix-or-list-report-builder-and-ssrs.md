---
title: Hinzufügen, Verschieben oder Löschen einer Tabelle, Matrix oder Liste (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 4b97c470-cde0-4bb1-a46e-5f5f5553feaa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: eb60f8152ad49b68723367cfb4f9f3941511954e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63020899"
---
# <a name="add-move-or-delete-a-table-matrix-or-list-report-builder-and-ssrs"></a>Hinzufügen, Verschieben oder Löschen einer Tabelle, Matrix oder Liste (Berichts-Generator und SSRS)
  Ein Datenbereich zeigt Daten aus einem Berichtsdataset an. Zu den Datenbereichen gehören Tabelle, Matrix, Liste, Diagramm und Messgerät. Um einen Datenbereich in einen anderen Datenbereich zu schachteln, fügen Sie die Datenbereiche getrennt hinzu, und ziehen Sie dann den Datenbereich, den Sie schachteln möchten, auf den anderen Datenbereich.  
  
 Am einfachsten können Sie einen Tabellen- oder Matrixdatenbereich einem Bericht hinzufügen, indem Sie den Assistenten Neue Tabelle oder Neue Matrix ausführen. Diese Assistenten führen Sie durch die einzelnen Schritte bei der Auswahl einer Verbindung mit einer Datenquelle, dem Anordnen von Feldern und der Auswahl von Layout und Stil.  
  
> [!NOTE]  
>  Der Assistent ist nur in Berichts-Generator verfügbar.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-table-or-matrix-to-a-report-by-using-the-new-table-or-new-matrix-wizard"></a>So fügen Sie einem Bericht mit den Assistenten "Neue Tabelle" oder "Neue Matrix" eine Tabelle oder Matrix hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** auf **Tabelle** oder **Matrix**und dann auf **Tabellen-Assistent** oder **Matrix-Assistent**.  
  
2.  Führen Sie die Schritte in der **NewTable** oder **neue Matrix** Assistenten.  
  
3.  Klicken Sie auf der Registerkarte **Home** auf **Ausführen** , um den gerenderten Bericht anzuzeigen.  
  
4.  Klicken Sie auf der Registerkarte **Ausführen** auf **Entwurf** , um den Bericht weiter zu bearbeiten.  
  
### <a name="to-add-a-data-region"></a>So fügen Sie einen Datenbereich hinzu  
  
1.  Klicken Sie auf dem **Menüband**in der Gruppe **Datenbereiche** auf den hinzuzufügenden Datenbereich.  
  
2.  Klicken Sie auf die Entwurfsoberfläche, und erstellen Sie dann durch Ziehen ein Feld mit der gewünschten Datenbereichsgröße.  
  
3.  Ziehen Sie ein Berichtsdataset-Feld aus dem Berichtsdatenbereich auf eine Datenbereichszelle. Jetzt ist der Datenbereich an Daten im Berichtsdataset gebunden.  
  
### <a name="to-select-a-data-region"></a>So wählen Sie einen Datenbereich aus  
  
-   Klicken Sie für einen Tablix-Datenbereich mit der rechten Maustaste auf den Eckziehpunkt. Klicken Sie für einen Diagramm- oder Messgerät-Datenbereich in den Datenbereich.  
  
     Ein Auswahlkästchen und acht Ziehpunkte werden angezeigt.  
  
     Klicken Sie für geschachtelte Datenbereiche mit der rechten Maustaste in den geschachtelten Datenbereich, klicken Sie auf **Auswählen**, und wählen Sie anschließend das gewünschte Berichtselement aus. Im Eigenschaftenbereich können Sie überprüfen, welches Berichtselement ausgewählt ist. Der Name des auf der Entwurfsoberfläche ausgewählten Elements wird in der Symbolleiste des Eigenschaftenbereichs angezeigt.  
  
### <a name="to-move-a-data-region"></a>So verschieben Sie einen Datenbereich  
  
-   Um einen Datenbereich zu verschieben, klicken Sie auf das Auswahlkästchen des Datenbereichs, und ziehen Sie ihn an die gewünschte Position. Verwenden Sie Ausrichtungslinien, um den Bereich an vorhandenen Berichtselementen auszurichten.  
  
     Wenn das Lineal nicht sichtbar ist, klicken Sie auf die Registerkarte Ansicht, und wählen Sie die Option **Lineal** aus.  
  
     Sie können den ausgewählten Datenbereich auf der Entwurfsoberfläche auch mit den Pfeiltasten verschieben.  
  
### <a name="to-delete-a-data-region"></a>So löschen Sie einen Datenbereich  
  
-   Wählen Sie den Datenbereich aus, klicken Sie mit der rechten Maustaste in den Datenbereich, und klicken Sie anschließend auf **Löschen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tabellen (Berichts-Generator und SSRS)](tables-report-builder-and-ssrs.md)   
 [Matrizen (Berichts-Generator und SSRS)](create-a-matrix-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
