---
title: Erstellen oder bearbeiten (Dialogfeld) für die benannte Abfrage (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createnamedquery.f1
helpviewer_keywords:
- Create Named Query dialog box
ms.assetid: 8e192ad6-a0b1-4e21-bb3f-087c93e62941
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97f01b0bbf3d1ddc54ea4db2b771723e12d168d7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66086811"
---
# <a name="create-or-edit-named-query-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld "Benannte Abfrage erstellen oder bearbeiten" (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Benannte Abfrage erstellen/bearbeiten** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie eine benannte Abfrage im **Datenquellensicht-Designer** erstellen bzw. bearbeiten. Eine benannte Abfrage kann als Tabelle behandelt werden, auf der andere [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekte basieren können. Zum Anzeigen des Dialogfelds **Benannte Abfrage erstellen/bearbeiten** führen Sie einen der folgenden Schritte aus:  
  
-   Klicken Sie im Bereich **Symbolleiste** von **Datenquellensicht-Designer** auf **Neue benannte Abfrage**.  
  
-   Klicken Sie mit der rechten Maustaste auf den Bereich **Diagramm** im **Datenquellensicht-Designer** , und wählen Sie **Neue benannte Abfrage**aus.  
  
-   Klicken Sie im Bereich **Diagramm** oder **Tabellen** im **Datenquellensicht-Designer** mit der rechten Maustaste auf den Namen einer benannten Abfrage, und wählen Sie **Benannte Abfrage bearbeiten**aus.  
  
 Bei der eingegebenen Abfrage muss es sich um einen gültigen Abfragebefehl für den zugrunde liegenden Anbieter handeln. Die Abfrage wird mit dem zugrunde liegenden Anbieter zur Überprüfung vorbereitet und dient der Identifizierung der zurückgegebenen Spalten. Das Dialogfeld kann in zwei Sichten dargestellt werden:  
  
-   Visual Database Tools (VDT)-Abfrage-Generator  
  
     In der Sicht VDT-Abfrage-Generator steht allen Benutzern eine Gruppe von Benutzeroberflächentools zur visuellen Erstellung und für den Test von SQL-Abfragen zur Verfügung.  
  
-   Standardabfrage-Generator  
  
     Erfahreneren Benutzern steht mit dem Standardabfrage-Generator für die Erstellung und den Test von SQL-Abfragen eine einfachere Benutzeroberfläche mit direkterem Zugriff zur Verfügung.  
  
## <a name="options"></a>Optionen  
 **Name**  
 Geben Sie den Namen der Abfrage ein.  
  
 **Beschreibung**  
 Geben Sie die optionale Beschreibung der Abfrage ein.  
  
 **Data Source**  
 Gibt die Datenquelle für die Abfrage an.  
  
 **Abfragedefinition**  
 Durch die Abfragedefinition werden eine Symbolleiste und Bereiche bereitgestellt, die der ausgewählten Sicht entsprechend zum Definieren der Abfrage verwendet werden.  
  
 **Symbolleiste**  
 Mithilfe der Symbolleiste können Sie Datasets verwalten, Bereiche zur Anzeige auswählen und unterschiedliche Abfragefunktionen steuern.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Zum Standardabfrage-Generator wechseln**|Wählen Sie diese Option aus, um nur die Optionen anzuzeigen, die in der Sicht des Standardabfrage-Generators verfügbar sind. Es werden nur die folgenden Optionen angezeigt:<br />**SQL-Bereich**<br />**Ergebnisbereich**<br />**Symbolleiste**, nur mit den Schaltflächen **Zum VDT-Abfrage-Generator wechseln** und **Ausführen**<br /><br /> <br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **zum VDT-Abfrage-Generator** ausgewählt ist.|  
|**Zum VDT-Abfrage-Generator wechseln**|Wählen Sie diese Option aus, um alle Optionen anzuzeigen, die in der Sicht VDT-Abfrage-Generator (Visual Database Tools) verfügbar sind.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **wechseln Sie zum Standardabfrage-Generator** ausgewählt ist.|  
|**Diagrammbereich ein-/ausblenden**|Blendet den **Diagrammbereich**ein oder aus.<br /><br /> **Hinweis** Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
|**Rasterbereich ein-/ausblenden**|Blendet den **Rasterbereich**ein oder aus.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **zum VDT-Abfrage-Generator** ausgewählt ist.|  
|**SQL-Bereich ein-/ausblenden**|Blendet den **SQL-Bereich**ein oder aus.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **zum VDT-Abfrage-Generator** ausgewählt ist.|  
|**Ergebnisbereich ein-/ausblenden**|Blendet den **Ergebnisbereich**ein oder aus.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **zum VDT-Abfrage-Generator** ausgewählt ist.|  
|**Ausführen**|Führt die Abfrage aus. Ergebnisse werden im **Ergebnisbereich**angezeigt.|  
|**SQL überprüfen**|Überprüft die SQL-Anweisung in der Abfrage.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **zum VDT-Abfrage-Generator** ausgewählt ist.|  
|**Aufsteigend sortieren**|Sortiert die Ausgabezeilen der ausgewählten Spalte im **Rasterbereich**in aufsteigender Reihenfolge.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **zum VDT-Abfrage-Generator** ausgewählt ist.|  
|**Absteigend sortieren**|Sortiert die Ausgabezeilen der ausgewählten Spalte im **Rasterbereich**in absteigender Reihenfolge.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **zum VDT-Abfrage-Generator** ausgewählt ist.|  
|**Filter entfernen**|Entfernt die Sortierkriterien ggf. für die ausgewählte Zeile im **Rasterbereich**.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **zum VDT-Abfrage-Generator** ausgewählt ist.|  
|**GROUP BY verwenden**|Fügt der Abfrage die Gruppierungsfunktionalität hinzu.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **zum VDT-Abfrage-Generator** ausgewählt ist.|  
|**Tabelle hinzufügen**|Zeigt das Dialogfeld **Tabelle hinzufügen** an, in dem der Abfrage eine neue Tabelle oder Sicht hinzugefügt werden kann. Weitere Informationen zum Dialogfeld **Tabelle hinzufügen** finden Sie unter [Tabelle hinzufügen &#40;Dialogfeld, Analysis Services – Mehrdimensionale Daten&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **zum VDT-Abfrage-Generator** ausgewählt ist.|  
  
 **Diagrammbereich**  
 Zeigt die Objekte an, auf die durch die Abfrage als Diagramm verwiesen wird. Das Diagramm zeigt die in der Abfrage enthaltenen Tabellen sowie die Art, wie diese miteinander verknüpft sind. Aktivieren oder deaktivieren Sie das Kontrollkästchen neben einer Spalte in einer Tabelle, um die entsprechende Spalte der Abfrageausgabe hinzuzufügen bzw. sie daraus zu entfernen.  
  
 Wenn Sie der Abfrage Tabellen hinzufügen, werden im Dialogfeld auf der Grundlage der Schlüssel in der Tabelle Joins zwischen Tabellen erstellt. Um einen Join hinzuzufügen, ziehen Sie ein Feld aus einer Tabelle auf ein Feld in einer anderen Tabelle. Sie können den Join verwalten, indem Sie mit der rechten Maustaste auf den Join klicken.  
  
 Klicken Sie mit der rechten Maustaste auf den Bereich **Diagramm** , um Tabellen hinzuzufügen oder zu entfernen, alle Tabellen auszuwählen oder Bereiche ein- oder auszublenden.  
  
> [!NOTE]  
>  Die Inhalte der Bereiche **Diagramm**, **Raster**und **SQL** werden synchronisiert, sodass sich Änderungen in einem Bereich sofort auch auf die anderen beiden Bereiche auswirken.  
  
> [!IMPORTANT]  
>  Das Ändern von Abfragetypen wird in dem Dialogfeld nicht unterstützt.  
  
 **Rasterbereich**  
 Zeigt die Objekte an, auf die durch die Abfrage in einem Raster verwiesen wird. In diesem Bereich können Sie der Abfrage Spalten hinzufügen oder Spalten aus der Abfrage entfernen sowie die Einstellungen für die einzelnen Spalten ändern.  
  
> [!NOTE]  
>  Die Inhalte der Bereiche **Diagramm**, **Raster**und **SQL** werden synchronisiert, sodass sich Änderungen in einem Bereich sofort auch auf die anderen beiden Bereiche auswirken.  
  
 **SQL-Bereich**  
 Zeigt die Abfrage als SQL-Anweisung an. Geben Sie die entsprechenden Werte ein, um die SQL-Anweisung für die Abfrage zu ändern.  
  
> [!NOTE]  
>  Die Inhalte der Bereiche **Diagramm**, **Raster**und **SQL** werden synchronisiert, sodass sich Änderungen in einem Bereich sofort auch auf die anderen beiden Bereiche auswirken.  
  
 **Ergebnisbereich**  
 Zeigt die Ergebnisse der Abfrage an, wenn Sie im Bereich **Symbolleiste** auf **Ausführen** klicken.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Definieren von benannten Abfragen in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)  
  
  
