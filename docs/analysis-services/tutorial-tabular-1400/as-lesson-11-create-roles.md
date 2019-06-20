---
title: 'Analysis Services-Tutorial – Lektion 11: Erstellen von Rollen | Microsoft-Dokumentation'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfiles"
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 6466eca2be66a20dfcab23f2097b71a2d0fc1cec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148951"
---
# <a name="create-roles"></a>Erstellen von Rollen

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion erstellen Sie Rollen. Rollen bieten Model-Datenbank modelldatenbankobjekt- und datensicherheit durch Einschränken des Zugriffs auf diejenigen Benutzer, die Mitglieder der Rolle sind. Jede Rolle wird mit einer einzigen Berechtigung definiert: Keine, lesen, lesen und verarbeiten, Prozess oder Administrator. Rollen können während der Modellerstellung mithilfe des Rollen-Manager definiert werden. Nachdem ein Modell bereitgestellt wurde, können Sie Rollen mithilfe von SQL Server Management Studio (SSMS) verwalten. Weitere Informationen finden Sie unter [Rollen](../tabular-models/roles-ssas-tabular.md)während der Modellerstellung im Dialogfeld Rollen-Manager definiert werden.
  
> [!NOTE]  
> Das Erstellen von Rollen ist zum Abschließen dieses Lernprogramms nicht erforderlich. Standardmäßig verfügt das Konto, dem Sie derzeit angemeldet sind Administratorrechte für das Modell. Für andere Benutzer in Ihrer Organisation mit einem berichterstellungsclient durchsuchen, müssen Sie allerdings mindestens eine Rolle mit Leseberechtigungen erstellen und diese Benutzer als Mitglieder hinzugefügt.  
  
Sie erstellen drei Rollen:  
  
-   **Vertriebsleiter** – diese Rolle kann Benutzer beinhalten, in Ihrer Organisation, die für die Leseberechtigungen für alle Modellobjekte und Daten haben sollen.  
  
-   **Sales Analyst US** – diese Rolle kann Benutzer beinhalten, in Ihrer Organisation, die für die Sie nur Daten zum Vertrieb in den Vereinigten Staaten wechseln können möchten. Für diese Rolle verwenden Sie eine DAX-Formel definiert eine *Zeilenfilter*, der Mitgliedern, um Daten nur für die USA zu durchsuchen.  
  
-   **Administrator** – diese Rolle kann Benutzer für die Administratorberechtigung, sind der unbegrenzten Zugriff und Berechtigungen zum Ausführen von administrativer Aufgaben für die Modelldatenbank beinhalten.  
  
Da Windows-Benutzer- und -Gruppenkonten in der Organisation eindeutig sind, können Sie Mitgliedern Konten aus Ihrer Organisation hinzufügen. In diesem Lernprogramm können Sie die Angaben zu den Mitgliedern auch weglassen. Testen Sie die Auswirkungen der einzelnen Rollen weiter unten in der Lektion 12: In Excel analysieren.  
  
Geschätzte Zeit zum Abschließen dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 10: Erstellen von Partitionen](../tutorial-tabular-1400/as-lesson-10-create-partitions.md).  
  
## <a name="create-roles"></a>Erstellen von Rollen  
  
#### <a name="to-create-a-sales-manager-user-role"></a>So erstellen Sie die Benutzerrolle "Sales Manager"  
  
1.  Im tabellarischen Modell-Explorer mit der Maustaste **Rollen** > **Rollen**.  
  
2.  Klicken Sie im Rollen-Manager **neu**.  
  
3.  Klicken Sie auf die neue Rolle, und klicken Sie dann in der **Namen** Spalte benennen Sie die Rolle in **Sales Manager**.  
  
4.  Klicken Sie in der Spalte **Berechtigungen** auf die Dropdownliste, und wählen Sie anschließend die Berechtigung **Lesen** aus. 

    ![als-lesson11-neue-Rolle](../tutorial-tabular-1400/media/as-lesson11-new-role.png) 
  
5.  Optional: Klicken Sie auf die **Mitglieder** Registerkarte, und klicken Sie dann auf **hinzufügen**. Geben Sie im Dialogfeld **Benutzer oder Gruppen auswählen** die Windows-Benutzer oder -Gruppen in Ihrer Organisation ein, die Sie der Rolle hinzufügen möchten.  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>So erstellen Sie die Benutzerrolle "Sales Analyst US"  
  
1.  Klicken Sie im Rollen-Manager **neu**.    
  
2.  Benennen Sie die Rolle zum **Sales Analyst US**.  
  
3.  Erteilen Sie dieser Rolle **lesen** Berechtigung.  
  
4.  Klicken Sie auf der Registerkarte "Zeilenfilter", und klicken Sie dann für die **DimGeography** Tabelle nur in der Spalte DAX-Filter geben Sie die folgende Formel:  
  
    ```Administrator
    =DimGeography[CountryRegionCode] = "US" 
    ```
    
    Eine Zeilenfilterformel muss in einen booleschen Wert (TRUE/FALSE) aufgelöst werden. Mit dieser Formel geben Sie an, dass nur Zeilen mit dem Wert der Länder-/ Regionscode "US" für den Benutzer sichtbar sind.  
    ![as-lesson11-role-filter](../tutorial-tabular-1400/media/as-lesson11-role-filter.png) 
  
6.  Optional: Klicken Sie auf die **Mitglieder** Registerkarte, und klicken Sie dann auf **hinzufügen**. Geben Sie im Dialogfeld **Benutzer oder Gruppen auswählen** die Windows-Benutzer oder -Gruppen in Ihrer Organisation ein, die Sie der Rolle hinzufügen möchten.  
  
#### <a name="to-create-an-administrator-user-role"></a>Erstellen Sie eine Administrator-Benutzerrolle  
  
1.  Klicken Sie auf **Neu**.  
  
2.  Benennen Sie die Rolle zum **Administrator**.  
  
3.  Erteilen Sie dieser Rolle **Administrator** Berechtigung.  
  
4.  Optional: Klicken Sie auf die **Mitglieder** Registerkarte, und klicken Sie dann auf **hinzufügen**. Geben Sie im Dialogfeld **Benutzer oder Gruppen auswählen** die Windows-Benutzer oder -Gruppen in Ihrer Organisation ein, die Sie der Rolle hinzufügen möchten. 
  
  
## <a name="whats-next"></a>Wie geht es weiter?

[Lektion 12: In Excel analysieren](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md).

  
  
