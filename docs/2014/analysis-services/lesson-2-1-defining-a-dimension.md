---
title: Definieren einer Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 112696db-3838-4b50-91bd-d2ce5fa04ee5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74561047f149ae6a6bdcd0cd54347d842e49569f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079087"
---
# <a name="defining-a-dimension"></a>Definieren einer Dimension.
  In der folgenden Aufgabe verwenden Sie den Dimensions-Assistenten, um eine Date-Dimension zu erstellen.  
  
> [!NOTE]  
>  Für diese Lektion ist es erforderlich, dass Sie alle Prozeduren in Lektion 1 abgeschlossen haben.  
  
### <a name="to-define-a-dimension"></a>So definieren Sie eine Dimension  
  
1.  Klicken Sie im Projektmappen-Explorer (auf der rechten Seite von Microsoft Visual Studio) mit der rechten Maustaste auf **Dimensionen**, und klicken Sie anschließend auf **Neue Dimension**. Der Dimensions-Assistent wird angezeigt.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Dimensions-Assistenten** auf **Weiter**.  
  
3.  Überprüfen Sie, ob die Option **Vorhandene Tabelle verwenden** auf der Seite **Erstellungsmethode auswählen** ausgewählt ist, und klicken Sie anschließend auf **Weiter**.  
  
4.  Überprüfen Sie auf der Seite **Quellinformationen angeben** , ob die **Adventure Works DW 2012** -Datenquellensicht ausgewählt ist.  
  
5.  Wählen Sie in der Liste **Haupttabelle** den Eintrag **Date**aus.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Aktivieren Sie auf der Seite **Dimensionsattribute auswählen** die Kontrollkästchen neben den folgenden Attributen:  
  
    -   **Datums Schlüssel**  
  
    -   **Alternativer Schlüssel für das vollständige Datum**  
  
    -   **Name des englischen Monats**  
  
    -   **Kalenderquartal**  
  
    -   **Kalenderjahr**  
  
    -   **Kalender Semester**  
  
8.  Ändern Sie die Einstellung von der Spalte **Attributtyp** des **Full Date Alternate Key** -Attributs von **Regulär** in **Datum**. Klicken Sie hierzu auf **Regulär** in der Spalte **Attributtyp** . Klicken Sie anschließend auf den Pfeil, um die Optionen zu erweitern. Klicken Sie anschließend auf **Date** > **Calendar** > **Date**. Klicken Sie auf **OK**. Wiederholen Sie diese Schritte, um den Attributtyp der Attribute wie folgt zu ändern:  
  
    -   **English Month Name** in **Month**  
  
    -   **Kalenderquartal** bis **Quartal**  
  
    -   **Kalenderjahr** bis **Jahr**  
  
    -   **Kalender Semester** bis **Halbjahr**  
  
9. Klicken Sie auf **Weiter**.  
  
10. Auf der Seite **Assistenten abschließen** können Sie im Bereich Vorschau die **Date** -Dimension und ihre Attribute sehen.  
  
11. Klicken Sie auf **Fertig stellen**, um den Assistenten abzuschließen.  
  
     Im Projektmappen-Explorer wird im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Projekt die Date-Dimension im Ordner **Dimensionen** angezeigt. Im Zentrum der Entwicklungsumgebung zeigt der Dimensions-Designer die Date-Dimension an.  
  
12. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Definieren eines Cubes](lesson-2-2-defining-a-cube.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)   
 [Erstellen einer Dimension mithilfe einer vorhandenen Tabelle](multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Erstellen einer Dimension mit dem Dimensions-Assistenten](multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)  
  
  
