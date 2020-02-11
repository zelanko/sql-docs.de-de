---
title: Dialog Feld ' Abruf Abfrage erstellen ' (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.createpollingquerydialog.f1
ms.assetid: 0f2902b5-796a-4eb0-be03-01514dc01b9a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: faf96ad02005c0385ec56e1f8763da2e82f093ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086833"
---
# <a name="create-polling-query-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Abrufabfrage erstellen' (Analysis Services – Mehrdimensionale Daten)
  Verwenden Sie das Dialogfeld **Abrufabfrage erstellen** von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , um im Dialogfeld **Speicheroptionen** auf der Registerkarte **Benachrichtigungen** eine Abrufabfrage zu erstellen. Eine Abrufabfrage ist normalerweise eine SINGLETON-Abfrage, die einen Wert zurückgibt, mit dessen Hilfe [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bestimmen kann, ob an Tabellen oder anderen relationalen Objekten Änderungen vorgenommen wurden. Klicken Sie zum Anzeigen des Dialogfelds **Abrufabfrage erstellen** in der Spalte **Abrufabfrage** des Rasters für die Option **Geplantes Abrufen** auf der Registerkarte **Benachrichtigungen** des Dialogfelds **Speicheroptionen** auf die Schaltfläche mit den Auslassungspunkten (**...**). Weitere Informationen zur Registerkarte **Benachrichtigungen** des Dialogfelds **Speicheroptionen** finden Sie unter [Benachrichtigungen &#40;Dialogfeld „Speicheroptionen“&#41; &#40;Analysis Services – Mehrdimensionale Daten&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md).  
  
 Welcher Werttyp durch die Abrufabfrage zurückgegeben wird, ist von der Art des Updates abhängig, das für den mehrdimensionalen OLAP-Zwischenspeicher (MOLAP) für das Objekt geplant ist, das auf der Tabelle basiert, für die die Abfrage ausgeführt wird:  
  
-   Wenn im Dialogfeld **Speicheroptionen** auf der Registerkarte **Benachrichtigungen** die Option **Inkrementelle Updates aktivieren** nicht ausgewählt wird, wird der MOLAP-Zwischenspeicher für das Objekt von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] vollständig aktualisiert, sobald während des geplanten Abrufvorgangs eine Änderung erkannt wird. Durch die verwendete Abrufabfrage wird bestimmt, ob der Tabelle seit dem letzten Abrufzeitraum Datensätze hinzugefügt wurden.  
  
-   Wenn im Dialogfeld **Speicheroptionen** auf der Registerkarte **Benachrichtigungen** die Option **Inkrementelle Updates aktivieren** ausgewählt wird, wird der MOLAP-Zwischenspeicher für das Objekt von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] inkrementell aktualisiert, sobald während des geplanten Abrufvorgangs eine Änderung erkannt wird. Durch die verwendete Abrufabfrage wird der letzte Datensatz in der Tabelle bestimmt.  
  
 Beispiel: Sie können mit den folgenden Abrufabfragen entweder vollständige oder inkrementelle Updates für die Customer-Dimension in der [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] -Beispieldatenbank in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bereitstellen:  
  
|Updatetyp|Abrufabfrage|  
|-----------------|-------------------|  
|Vollständiges Update|`SELECT`<br /><br /> `COUNT(*) AS TotalCount`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`|  
|Inkrementelles Update|`SELECT`<br /><br /> `MAX([CustomerKey]) AS LastCustomerKey`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`|  
  
 Weitere Informationen zu vollständigen und inkrementellen Updates für geplante Abrufbenachrichtigungen finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
 Bei der eingegebenen Abfrage muss es sich um einen gültigen Abfragebefehl für den zugrunde liegenden Anbieter handeln. Die Abfrage wird mit dem zugrunde liegenden Anbieter zur Überprüfung vorbereitet und dient der Identifizierung der zurückgegebenen Spalten. Das Dialogfeld kann in zwei Sichten dargestellt werden:  
  
-   Visual Database Tools (VDT)-Abfrage-Generator  
  
     In der Sicht VDT-Abfrage-Generator steht allen Benutzern eine Gruppe von Benutzeroberflächentools zur visuellen Erstellung und für den Test von SQL-Abfragen zur Verfügung.  
  
-   Standardabfrage-Generator  
  
     Erfahreneren Benutzern steht mit dem Standardabfrage-Generator für die Erstellung und den Test von SQL-Abfragen eine einfachere Benutzeroberfläche mit direkterem Zugriff zur Verfügung.  
  
## <a name="options"></a>Tastatur  
 **Data Source**  
 Gibt die Datenquelle für die Abfrage an.  
  
 **Abfrage Definition**  
 Durch die Abfragedefinition werden eine Symbolleiste und Bereiche bereitgestellt, die der ausgewählten Sicht entsprechend zum Definieren der Abfrage verwendet werden.  
  
 **Symbolleiste**  
 Mithilfe der Symbolleiste können Sie Datasets verwalten, Bereiche zur Anzeige auswählen und unterschiedliche Abfragefunktionen steuern.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Zum Standardabfrage-Generator wechseln**|Wählen Sie diese Option aus, um nur die Optionen anzuzeigen, die in der Sicht des Standardabfrage-Generators verfügbar sind. Es werden nur die folgenden Optionen angezeigt:<br /><br /> **SQL-Bereich**<br /><br /> **Ergebnisbereich**<br /><br /> **Symbolleiste**, nur **zu VDT Abfrage-Generator wechseln** und **Ausführen**<br /><br /> <br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**Zum VDT-Abfrage-Generator wechseln**|Wählen Sie diese Option aus, um alle Optionen anzuzeigen, die in der Sicht VDT-Abfrage-Generator (Visual Database Tools) verfügbar sind.<br /><br /> Hinweis: Die Option ist nur verfügbar, wenn **Zum Standardabfrage-Generator wechseln** ausgewählt ist.|  
|**Diagrammbereich ein-/ausblenden**|Blendet den **Diagrammbereich**ein oder aus.<br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**Raster Bereich ein-/ausblenden**|Blendet den **Rasterbereich**ein oder aus.<br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**SQL-Bereich ein-/ausblenden**|Blendet den **SQL-Bereich**ein oder aus.<br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**Ergebnisbereich ein-/ausblenden**|Blendet den **Ergebnisbereich**ein oder aus.<br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**Ausführen**|Führt die Abfrage aus. Ergebnisse werden im **Ergebnisbereich**angezeigt.|  
|**SQL überprüfen**|Überprüft die SQL-Anweisung in der Abfrage.<br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**Aufsteigend sortieren**|Sortiert die Ausgabezeilen der ausgewählten Spalte im **Rasterbereich**in aufsteigender Reihenfolge.<br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**Absteigend sortieren**|Sortiert die Ausgabezeilen der ausgewählten Spalte im **Rasterbereich**in absteigender Reihenfolge.<br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**Filter entfernen**|Entfernt die Sortierkriterien ggf. für die ausgewählte Zeile im **Rasterbereich**.<br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**Verwenden von Group by**|Fügt der Abfrage die Gruppierungsfunktionalität hinzu.<br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**Tabelle hinzufügen**|Zeigt das Dialogfeld **Tabelle hinzufügen** an, in dem der Abfrage eine neue Tabelle oder Sicht hinzugefügt werden kann. Weitere Informationen zum Dialogfeld **Tabelle hinzufügen** finden Sie unter [Tabelle hinzufügen &#40;Dialogfeld, Analysis Services – Mehrdimensionale Daten&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Hinweis: diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
  
 **Diagrammbereich**  
 Zeigt die Objekte an, auf die durch die Abfrage als Diagramm verwiesen wird. Das Diagramm zeigt die in der Abfrage enthaltenen Tabellen sowie die Art, wie diese miteinander verknüpft sind. Aktivieren oder deaktivieren Sie das Kontrollkästchen neben einer Spalte in einer Tabelle, um die entsprechende Spalte der Abfrageausgabe hinzuzufügen bzw. sie daraus zu entfernen.  
  
 Wenn Sie der Abfrage Tabellen hinzufügen, werden im Dialogfeld auf der Grundlage der Schlüssel in der Tabelle Joins zwischen Tabellen erstellt. Um einen Join hinzuzufügen, ziehen Sie ein Feld aus einer Tabelle auf ein Feld in einer anderen Tabelle. Sie können den Join verwalten, indem Sie mit der rechten Maustaste auf den Join klicken.  
  
 Klicken Sie mit der rechten Maustaste auf den Bereich **Diagramm** , um Tabellen hinzuzufügen oder zu entfernen, alle Tabellen auszuwählen oder Bereiche ein- oder auszublenden.  
  
> [!NOTE]  
>  Die Inhalte von **Diagramm**Bereich, **Raster**Bereich und **SQL** -Bereich werden synchronisiert, sodass sich Änderungen in einem Bereich in den anderen beiden Bereichen widerspiegeln.  
  
> [!IMPORTANT]  
>  Das Ändern von Abfragetypen wird in dem Dialogfeld nicht unterstützt.  
  
 **Raster Bereich**  
 Zeigt die Objekte an, auf die durch die Abfrage in einem Raster verwiesen wird. In diesem Bereich können Sie der Abfrage Spalten hinzufügen oder Spalten aus der Abfrage entfernen sowie die Einstellungen für die einzelnen Spalten ändern.  
  
> [!NOTE]  
>  Die Inhalte von **Diagramm**Bereich, **Raster**Bereich und **SQL** -Bereich werden synchronisiert, sodass sich Änderungen in einem Bereich in den anderen beiden Bereichen widerspiegeln.  
  
 **SQL-Bereich**  
 Zeigt die Abfrage als SQL-Anweisung an. Geben Sie die entsprechenden Werte ein, um die SQL-Anweisung für die Abfrage zu ändern.  
  
> [!NOTE]  
>  Die Inhalte von **Diagramm**Bereich, **Raster**Bereich und **SQL** -Bereich werden synchronisiert, sodass sich Änderungen in einem Bereich in den anderen beiden Bereichen widerspiegeln.  
  
 **Ergebnisbereich**  
 Zeigt die Ergebnisse der Abfrage an, wenn Sie im Bereich **Symbolleiste** auf **Ausführen** klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
