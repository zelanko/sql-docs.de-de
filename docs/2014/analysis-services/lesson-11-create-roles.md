---
title: 'Lektion 12: Erstellen von Rollen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec4bad8ef036e8f19ce0a856f3d9c04bafd0e7c5
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66079268"
---
# <a name="lesson-12-create-roles"></a>Lektion 12: Erstellen von Rollen
  In dieser Lektion erstellen Sie Rollen. Rollen stellen Modelldatenbankobjekt- und Datensicherheit bereit, indem sie den Zugriff auf die Windows-Benutzer einschränken, die Rollenmitglieder sind. Jede Rolle wird mit einer einzigen Berechtigung definiert: Keine, lesen, lesen und verarbeiten, Prozess oder Administrator. Rollen können in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]während der Modellerstellung im Dialogfeld Rollen-Manager definiert werden. Nachdem ein Modell bereitgestellt wurde, können Sie mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Rollen verwalten. Weitere Informationen finden Sie unter [Rollen &#40;SSAS – tabellarisch&#41;](tabular-models/roles-ssas-tabular.md).  
  
> [!NOTE]  
>  Das Erstellen von Rollen ist zum Abschließen dieses Lernprogramms nicht erforderlich. Das Konto, über das Sie derzeit angemeldet sind, verfügt standardmäßig über Administratorberechtigungen für das Modell. Um Benutzern in Ihrer Organisation jedoch das Durchsuchen des Modells mithilfe einer Berichterstellungsclientanwendung zu ermöglichen, müssen Sie mindestens eine Rolle mit Leseberechtigung erstellen und diese Benutzer als Mitglieder hinzufügen.  
  
 Sie erstellen drei Rollen:  
  
-   Sales Manager – diese Rolle kann Benutzer in Ihrer Organisation umfassen für die Leseberechtigungen für alle Modellobjekte und Daten haben sollen.  
  
-   Sales Analyst US – diese Rolle kann Benutzer in Ihrer Organisation umfassen für die Sie nur Daten zum Vertrieb in den USA (Vereinigte Staaten) wechseln können möchten. Für diese Rolle definieren Sie mit einer DAX-Formel einen *Zeilenfilter*, der Mitgliedern der Rolle lediglich das Durchsuchen von Daten in den USA ermöglicht.  
  
-   Administrator – diese Rolle kann Benutzer umfassen für die Administratorberechtigung verfügen, die uneingeschränkten Zugriff und Berechtigungen zum Ausführen von Verwaltungsaufgaben in der Model-Datenbank ermöglicht werden soll.  
  
 Da Windows-Benutzer- und -Gruppenkonten in der Organisation eindeutig sind, können Sie Mitgliedern Konten aus Ihrer Organisation hinzufügen. In diesem Lernprogramm können Sie die Angaben zu den Mitgliedern auch weglassen. Sie werden können die Auswirkungen der einzelnen Rollen weiter unten in der Lektion 12 testen: In Excel analysieren.  
  
 Geschätzte Zeit zum Abschließen dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 11: Erstellen von Partitionen](lesson-10-create-partitions.md).  
  
## <a name="create-roles"></a>Erstellen von Rollen  
  
#### <a name="to-create-a-sales-manager-user-role"></a>So erstellen Sie die Benutzerrolle "Sales Manager"  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und anschließend auf **Rollen**.  
  
2.  Klicken Sie im Dialogfeld **Rollen-Manager** auf **Neu**.  
  
     Der Liste wird eine neue Rolle mit der Berechtigung Keine hinzugefügt.  
  
3.  Klicken Sie auf die neue Rolle, und klicken Sie dann in der **Namen** Spalte benennen Sie die Rolle zum `Internet Sales Manager`.  
  
4.  Klicken Sie in der Spalte **Berechtigungen** auf die Dropdownliste, und wählen Sie anschließend die Berechtigung **Lesen** aus.  
  
5.  Optional: Klicken Sie auf die Registerkarte **Mitglieder** und anschließend auf **Hinzufügen**.  
  
6.  Geben Sie im Dialogfeld **Benutzer oder Gruppen auswählen** die Windows-Benutzer oder -Gruppen in Ihrer Organisation ein, die Sie der Rolle hinzufügen möchten.  
  
7.  Überprüfen Sie die Auswahl, und klicken Sie anschließend auf **OK**  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>So erstellen Sie die Benutzerrolle "Sales Analyst US"  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und anschließend auf **Rollen**.  
  
2.  Klicken Sie im Dialogfeld **Rollen-Manager** auf **Neu**.  
  
     Der Liste wird eine neue Rolle mit der Berechtigung Keine hinzugefügt.  
  
3.  Klicken Sie auf die neue Rolle, und klicken Sie dann in der **Namen** Spalte benennen Sie die Rolle zum `Internet Sales US`.  
  
4.  Klicken Sie in der Spalte **Berechtigungen** auf die Dropdownliste, und wählen Sie anschließend die Berechtigung **Lesen** aus.  
  
5.  Klicken Sie auf die Registerkarte Zeilenfilter, und geben Sie anschließend nur für die Tabelle **Geography** in der Spalte DAX Filter die folgende Formel ein:  
  
     `=Geography[Country Region Code] = "US"`  
  
     Eine Zeilenfilterformel muss in einen booleschen Wert (TRUE/FALSE) aufgelöst werden. Mit dieser Formel geben Sie an, dass nur Zeilen mit dem Wert der Länder-/ Regionscode "US" für den Benutzer sichtbar sein.  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
6.  Optional: Klicken Sie auf die Registerkarte **Mitglieder** und anschließend auf **Hinzufügen**.  
  
7.  Geben Sie im Dialogfeld **Benutzer oder Gruppen auswählen** die Windows-Benutzer oder -Gruppen in Ihrer Organisation ein, die Sie der Rolle hinzufügen möchten.  
  
8.  Überprüfen Sie die Auswahl, und klicken Sie anschließend auf **OK**  
  
#### <a name="to-create-an-administrator-role"></a>So erstellen Sie die Rolle "Administrator"  
  
1.  Klicken Sie im Dialogfeld **Rollen-Manager** auf **Neu**.  
  
2.  Klicken Sie auf die neue Rolle, und klicken Sie dann in der **Namen** Spalte benennen Sie die Rolle zum `Internet Sales Administrator`.  
  
3.  Klicken Sie in der Spalte **Berechtigungen** auf die Dropdownliste und wählen Sie anschließend die Berechtigung **Administrator** aus.  
  
4.  Klicken Sie auf die Registerkarte **Mitglieder** und anschließend auf **Hinzufügen**.  
  
5.  Optional: Geben Sie im Dialogfeld **Benutzer oder Gruppen auswählen** die Windows-Benutzer oder -Gruppen in Ihrer Organisation ein, die Sie der Rolle hinzufügen möchten.  
  
6.  Überprüfen Sie die Auswahl, und klicken Sie anschließend auf **OK**  
  
## <a name="next-steps"></a>Nächste Schritte  
 Um dieses Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: Lektion: [Lektion 13: In Excel analysieren](lesson-12-analyze-in-excel.md).  
  
  
