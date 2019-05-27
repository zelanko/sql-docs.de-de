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
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66056641"
---
# <a name="query-builder"></a>Abfrage-Generator
  Verwenden Sie das Dialogfeld **Abfrage-Generator** , um Abfragen zum Verwenden mit dem Task 'SQL ausführen', der OLE DB-Quelle, dem OLE DB-Ziel und der Transformation für die Suche zu erstellen.  
  
 Mit dem Abfrage-Generator können die folgenden Aufgaben ausgeführt werden:  
  
-   **Arbeiten mit einer grafischen Darstellung einer Abfrage oder mit SQL-Befehlen** Der Abfrage-Generator enthält einen Bereich, in dem eine Abfrage grafisch dargestellt wird, und einen Bereich, in dem der SQL-Text der Abfrage angezeigt wird. Sie können entweder im grafischen oder im Textfensterbereich arbeiten. Der Abfrage-Generator synchronisiert die Sichten, damit sie immer aktuell sind.  
  
-   **Verbinden verknüpfter Tabellen** Wenn Sie der Abfrage mehrere Tabellen hinzufügen, bestimmt der Abfrage-Generator automatisch, wie die Tabellen miteinander in Beziehung stehen, und erstellt den geeigneten Joinbefehl.  
  
-   **Abfragen oder Aktualisieren von Datenbanken** Sie können den Abfrage-Generator verwenden, um mithilfe von SELECT-Anweisungen von Transact-SQL Daten zurückzugeben und um Abfragen zu erstellen, die Datensätze einer Datenbank aktualisieren, einer Datenbank hinzufügen oder aus einer Datenbank löschen.  
  
-   **Sofortiges Anzeigen und Bearbeiten der Ergebnisse** Sie können die Abfrage ausführen und ein Recordset in einem Raster verwenden, das Ihnen das Durchführen eines Bildlaufs und Bearbeiten der Datensätze in der Datenbank ermöglicht.  
  
 Mit den grafischen Tools im Dialogfeld **Abfrage-Generator** können Sie Abfragen mithilfe von Drag &amp; Drop konstruieren. Standardmäßig erstellt der Abfrage-Generator SELECT-Abfragen. Sie können jedoch auch INSERT-, UPDATE- oder DELETE-Abfragen erstellen. Alle Typen von SQL-Anweisungen können im Dialogfeld **Abfrage-Generator** analysiert und ausgeführt werden. Weitere Informationen zu SQL-Anweisungen in Paketen finden Sie unter [Integration Services-Abfragen &#40;SSIS&#41;](integration-services-ssis-queries.md).  
  
 Weitere Informationen zur Transact-SQL-Sprache und -Syntax finden Sie unter [Transact-SQL-Referenz &#40;Datenbank-Engine&#41;](/sql/t-sql/language-reference).  
  
 Sie können Variablen auch in einer Abfrage verwenden, um Werte für einen Eingabeparameter bereitzustellen, um Werte von Ausgabeparametern aufzuzeichnen und um Rückgabecodes zu speichern. Weitere Informationen zum Verwenden von Variablen in Abfragen, die in Paketen verwendet werden, finden Sie unter [SQL ausführen (Task)](control-flow/execute-sql-task.md), [OLE DB-Quelle](data-flow/ole-db-source.md)und [Integration Services &#40;SSIS&#41; Queries](integration-services-ssis-queries.md). Weitere Informationen zum Verwenden von Variablen im Task „SQL ausführen“ finden Sie unter [Parameter und Rückgabecodes im Task „SQL ausführen“](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) und [Resultsets im Task „SQL ausführen“](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).  
  
 Die Transformationen für Suche und Fuzzysuche können ebenfalls Variablen mit Parametern und Rückgabecodes verwenden. Die Informationen zur OLE DB-Quelle gelten auch für diese beiden Transformationen.  
  
## <a name="options"></a>Optionen  
 **Symbolleiste**  
 Mithilfe der Symbolleiste können Sie Datasets verwalten, Bereiche zur Anzeige auswählen und Abfragefunktionen steuern.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Diagrammbereich ein-/ausblenden**|Blendet den Bereich **Diagramm** ein oder aus.|  
|**Rasterbereich ein-/ausblenden**|Blendet den Bereich **Raster** ein oder aus.|  
|**SQL-Bereich ein-/ausblenden**|Blendet den Bereich **SQL** ein oder aus.|  
|**Ergebnisbereich ein-/ausblenden**|Blendet den Bereich **Ergebnisse** ein oder aus.|  
|**Ausführen**|Führt die Abfrage aus. Ergebnisse werden im Ergebnisbereich angezeigt.|  
|**SQL überprüfen**|Überprüft, ob das SQL-Konto gültig ist.|  
|**Aufsteigend sortieren**|Sortiert die Ausgabezeilen der ausgewählten Spalte des Rasterbereichs in aufsteigender Reihenfolge.|  
|**Absteigend sortieren**|Sortiert die Ausgabezeilen der ausgewählten Spalte des Rasterbereichs in absteigender Reihenfolge.|  
|**Filter entfernen**|Wählen Sie einen Spaltennamen im Rasterbereich aus, und klicken Sie auf **Filter entfernen** , um die Sortierungskriterien aus der Spalte zu entfernen.|  
|**GROUP BY verwenden**|Fügt der Abfrage die GROUP BY-Funktionalität hinzu.|  
|**Tabelle hinzufügen**|Fügt der Abfrage eine neue Tabelle hinzu.|  
  
 **Abfragedefinition**  
 Die Abfragedefinition stellt eine Symbolleiste und Bereiche bereit, mit deren Hilfe die Abfrage definiert und getestet werden kann.  
  
|Bereich|Description|  
|----------|-----------------|  
|Bereich**Diagramm** |Zeigt die Abfrage in einem Diagramm an. Das Diagramm zeigt die in der Abfrage enthaltenen Tabellen sowie die Art, wie diese miteinander verknüpft sind. Aktivieren oder deaktivieren Sie das Kontrollkästchen neben einer Spalte in einer Tabelle, um die entsprechende Spalte der Abfrageausgabe hinzuzufügen bzw. sie daraus zu entfernen.<br /><br /> Wenn Sie der Abfrage Tabellen hinzufügen, erstellt der Abfrage-Generator auf der Grundlage der Tabellen Joins zwischen Tabellen, abhängig von den Schlüsseln in der Tabelle. Um einen Join hinzuzufügen, ziehen Sie ein Feld aus einer Tabelle auf ein Feld in einer anderen Tabelle. Sie können den Join verwalten, indem Sie mit der rechten Maustaste auf den Join klicken und Optionen aus einem Menü wählen.<br /><br /> Klicken Sie mit der rechten Maustaste auf den Bereich **Diagramm** , um Tabellen hinzuzufügen oder zu entfernen, alle Tabellen auszuwählen oder Bereiche ein- oder auszublenden.|  
|Bereich**Raster** |Zeigt die Abfrage in einem Raster an. Sie können diesen Bereich verwenden, um der Abfrage Spalten hinzuzufügen bzw. Spalten daraus zu entfernen, sowie um die Einstellungen der einzelnen Spalten zu ändern.|  
|Bereich**SQL** |Zeigt die Abfrage als SQL-Text an. Änderungen, die in den Bereichen **Diagramm** und **Raster** vorgenommen worden sind, werden hier angezeigt, genauso wie hier vorgenommene Änderungen in den Bereichen **Diagramm** und **Raster** angezeigt werden.|  
|Bereich**Ergebnisse** |Zeigt die Ergebnisse der Abfrage an, wenn Sie auf die Schaltfläche **Ausführen** auf der Symbolleiste klicken.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL ausführen (Task)](control-flow/execute-sql-task.md)   
 [OLE DB-Quelle](data-flow/ole-db-source.md)   
 [OLE DB-Ziel](data-flow/ole-db-destination.md)   
 [Transformation für Suche](data-flow/transformations/lookup-transformation.md)   
 [Integrationsdienste &#40;SSIS&#41; Abfragen](integration-services-ssis-queries.md)   
 [MERGE in Integration Services-Paketen](control-flow/merge-in-integration-services-packages.md)  
  
  
