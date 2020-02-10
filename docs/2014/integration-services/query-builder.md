---
title: Abfrage-Generator | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.querybuilder.f1
helpviewer_keywords:
- Query Builder dialog box
ms.assetid: 780752c9-6e3c-4f44-aaff-4f4d5e5a45c5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1880ceffb03389bc87ee8f25d1817a5e4f593566
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66056641"
---
# <a name="query-builder"></a>Abfrage-Generator
  Verwenden Sie das Dialogfeld **Abfrage-Generator** , um Abfragen zum Verwenden mit dem Task 'SQL ausführen', der OLE DB-Quelle, dem OLE DB-Ziel und der Transformation für die Suche zu erstellen.  
  
 Mit dem Abfrage-Generator können die folgenden Aufgaben ausgeführt werden:  
  
-   **Arbeiten mit einer grafischen Darstellung einer Abfrage oder mit SQL-Befehlen** Abfrage-Generator enthält einen Bereich, in dem die Abfrage grafisch angezeigt wird, und einen Bereich, in dem der SQL-Text der Abfrage angezeigt wird. Sie können entweder im grafischen oder im Textfensterbereich arbeiten. Der Abfrage-Generator synchronisiert die Sichten, damit sie immer aktuell sind.  
  
-   Verknüpfte **Tabellen miteinander verbinden** Wenn Sie der Abfrage mehrere Tabellen hinzufügen, bestimmt Abfrage-Generator automatisch, wie die Tabellen verknüpft sind, und erstellt den entsprechenden Joinbefehl.  
  
-   **Abfragen oder Aktualisieren von Datenbanken** Sie können Abfrage-Generator verwenden, um Daten mithilfe von Transact-SQL-SELECT-Anweisungen zurückzugeben und um Abfragen zu erstellen, mit denen Datensätze in einer Datenbank aktualisiert, hinzugefügt oder gelöscht werden.  
  
-   **Sofortiges Anzeigen und Bearbeiten von Ergebnissen** Sie können die Abfrage ausführen und mit einem Recordset in einem Raster arbeiten, das es Ihnen ermöglicht, einen Bildlauf durchzuführen und Datensätze in der Datenbank zu bearbeiten.  
  
 Mit den grafischen Tools im Dialogfeld **Abfrage-Generator** können Sie Abfragen mithilfe von Drag &amp; Drop konstruieren. Standardmäßig erstellt der Abfrage-Generator SELECT-Abfragen. Sie können jedoch auch INSERT-, UPDATE- oder DELETE-Abfragen erstellen. Alle Typen von SQL-Anweisungen können im Dialogfeld **Abfrage-Generator** analysiert und ausgeführt werden. Weitere Informationen zu SQL-Anweisungen in Paketen finden Sie unter [Integration Services-Abfragen &#40;SSIS&#41;](integration-services-ssis-queries.md).  
  
 Weitere Informationen zur Transact-SQL-Sprache und -Syntax finden Sie unter [Transact-SQL-Referenz &#40;Datenbank-Engine&#41;](/sql/t-sql/language-reference).  
  
 Sie können Variablen auch in einer Abfrage verwenden, um Werte für einen Eingabeparameter bereitzustellen, um Werte von Ausgabeparametern aufzuzeichnen und um Rückgabecodes zu speichern. Weitere Informationen zum Verwenden von Variablen in Abfragen, die in Paketen verwendet werden, finden Sie unter [SQL ausführen (Task)](control-flow/execute-sql-task.md), [OLE DB-Quelle](data-flow/ole-db-source.md)und [Integration Services &#40;SSIS&#41; Queries](integration-services-ssis-queries.md). Weitere Informationen zum Verwenden von Variablen im Task „SQL ausführen“ finden Sie unter [Parameter und Rückgabecodes im Task „SQL ausführen“](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) und [Resultsets im Task „SQL ausführen“](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).  
  
 Die Transformationen für Suche und Fuzzysuche können ebenfalls Variablen mit Parametern und Rückgabecodes verwenden. Die Informationen zur OLE DB-Quelle gelten auch für diese beiden Transformationen.  
  
## <a name="options"></a>Tastatur  
 **Symbolleiste**  
 Mithilfe der Symbolleiste können Sie Datasets verwalten, Bereiche zur Anzeige auswählen und Abfragefunktionen steuern.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Diagrammbereich ein-/ausblenden**|Blendet den **Diagramm** Bereich ein oder aus.|  
|**Raster Bereich ein-/ausblenden**|Blendet den **Raster** Bereich ein oder aus.|  
|**SQL-Bereich ein-/ausblenden**|Blendet den **SQL** -Bereich ein oder aus.|  
|**Ergebnisbereich ein-/ausblenden**|Blendet den Bereich **Ergebnisse** ein oder aus.|  
|**Ausführen**|Führt die Abfrage aus. Ergebnisse werden im Ergebnisbereich angezeigt.|  
|**SQL überprüfen**|Überprüft, ob das SQL-Konto gültig ist.|  
|**Aufsteigend sortieren**|Sortiert die Ausgabezeilen der ausgewählten Spalte des Rasterbereichs in aufsteigender Reihenfolge.|  
|**Absteigend sortieren**|Sortiert die Ausgabezeilen der ausgewählten Spalte des Rasterbereichs in absteigender Reihenfolge.|  
|**Filter entfernen**|Wählen Sie einen Spaltennamen im Rasterbereich aus, und klicken Sie auf **Filter entfernen** , um die Sortierungskriterien aus der Spalte zu entfernen.|  
|**Verwenden von Group by**|Fügt der Abfrage die GROUP BY-Funktionalität hinzu.|  
|**Tabelle hinzufügen**|Fügt der Abfrage eine neue Tabelle hinzu.|  
  
 **Abfrage Definition**  
 Die Abfragedefinition stellt eine Symbolleiste und Bereiche bereit, mit deren Hilfe die Abfrage definiert und getestet werden kann.  
  
|Bereich|BESCHREIBUNG|  
|----------|-----------------|  
|**Diagramm** Bereich|Zeigt die Abfrage in einem Diagramm an. Das Diagramm zeigt die in der Abfrage enthaltenen Tabellen sowie die Art, wie diese miteinander verknüpft sind. Aktivieren oder deaktivieren Sie das Kontrollkästchen neben einer Spalte in einer Tabelle, um die entsprechende Spalte der Abfrageausgabe hinzuzufügen bzw. sie daraus zu entfernen.<br /><br /> Wenn Sie der Abfrage Tabellen hinzufügen, erstellt der Abfrage-Generator auf der Grundlage der Tabellen Joins zwischen Tabellen, abhängig von den Schlüsseln in der Tabelle. Um einen Join hinzuzufügen, ziehen Sie ein Feld aus einer Tabelle auf ein Feld in einer anderen Tabelle. Sie können den Join verwalten, indem Sie mit der rechten Maustaste auf den Join klicken und Optionen aus einem Menü wählen.<br /><br /> Klicken Sie mit der rechten Maustaste auf den Bereich **Diagramm** , um Tabellen hinzuzufügen oder zu entfernen, alle Tabellen auszuwählen und Bereiche anzuzeigen oder auszublenden.|  
|**Raster** Bereich|Zeigt die Abfrage in einem Raster an. Sie können diesen Bereich verwenden, um der Abfrage Spalten hinzuzufügen bzw. Spalten daraus zu entfernen, sowie um die Einstellungen der einzelnen Spalten zu ändern.|  
|**SQL** -Bereich|Zeigt die Abfrage als SQL-Text an. Änderungen, die in den Bereichen **Diagramm** und **Raster** vorgenommen worden sind, werden hier angezeigt, genauso wie hier vorgenommene Änderungen in den Bereichen **Diagramm** und **Raster** angezeigt werden.|  
|**Ergebnis** Bereich|Zeigt die Ergebnisse der Abfrage an, wenn Sie auf die Schaltfläche **Ausführen** auf der Symbolleiste klicken.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL ausführen (Task)](control-flow/execute-sql-task.md)   
 [OLE DB-Quelle](data-flow/ole-db-source.md)   
 [OLE DB-Ziel](data-flow/ole-db-destination.md)   
 [Transformation für Suche](data-flow/transformations/lookup-transformation.md)   
 [Integration Services &#40;SSIS-&#41; Abfragen](integration-services-ssis-queries.md)   
 [MERGE in Integration Services-Paketen](control-flow/merge-in-integration-services-packages.md)  
  
  
