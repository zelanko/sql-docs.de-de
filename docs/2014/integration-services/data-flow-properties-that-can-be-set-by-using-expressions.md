---
title: Datenfluss-Eigenschaften, die mithilfe von Ausdrücken festgelegt werden können | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, property expressions
- Integration Services packages, property expressions
- packages [Integration Services], properties
- SSIS packages, property expressions
- property expressions [Integration Services]
ms.assetid: cd0e171a-08be-45d6-81dc-ed94f37698b8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d561840bfe2c10d7b269bb952b934d22dd957d32
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135200"
---
# <a name="data-flow-properties-that-can-be-set-by-using-expressions"></a>Data Flow-Eigenschaften, die mithilfe von Ausdrücken festgelegt werden können
  Die Werte mancher Eigenschaften von Datenflussobjekten können mithilfe von Eigenschaftsausdrücken festgelegt werden, die im Datenflusstask-Container verfügbar sind.  
  
 Weitere Informationen zum Verwenden von Eigenschaftsausdrücken finden Sie unter [Verwenden von Eigenschaftsausdrücken in Paketen](expressions/use-property-expressions-in-packages.md).  
  
 Sie können Eigenschaftsausdrücke dazu verwenden, Konfigurationen für jede bereitgestellte Instanz eines Pakets anzupassen. Sie können Eigenschaftsausdrücke auch zur Festlegung von Laufzeiteinschränkungen für ein Paket nutzen, indem Sie die Option **/set** mit dem Eingabeaufforderungshilfsprogramm **dtexec** verwenden. Beispielsweise können Sie einschränken der `MaximumThreads` , die von der Transformation für Sortierung verwendet oder die `MaxMemoryUsage` der Transformationen für Fuzzygruppierung und Fuzzysuche. Wenn keine Einschränkungen bestehen, legen diese Transformationen möglicherweise große Datenmengen im Arbeitsspeicher ab.  
  
 Um einen Eigenschaftsausdruck für eine der Eigenschaften eines unter diesem Thema aufgelisteten Datenflussobjekts festzulegen, zeigen Sie das Fenster **Eigenschaften** für den Datenflusstask an, indem Sie den Datenflusstask auf der Oberfläche **Ablaufsteuerung** des Designers auswählen oder indem Sie die Registerkarte **Datenfluss** des Designers auswählen, ohne eine individuelle Komponente oder einen Pfad auszuwählen. Wählen Sie die **Ausdrücke** -Eigenschaft aus, und klicken Sie auf die Schaltfläche mit den drei Punkten, um das Dialogfeld **Eigenschaftsausdrucks-Editor** anzuzeigen. Öffnen Sie die Dropdownliste **Eigenschaft** , um eine Eigenschaft auszuwählen, und geben Sie dann einen Ausdruck in das Textfeld **Ausdruck** ein, oder klicken Sie auf die Schaltfläche mit den drei Punkten, um das Dialogfeld **Ausdrucks-Generator** anzuzeigen.  
  
 Die **Eigenschaft** -Liste zeigt nur die verfügbaren Eigenschaften der Datenflussobjekte an, die bereits in der **Datenfluss** -Oberfläche des Designers platziert wurden. Deshalb können Sie die **Eigenschaft** -Liste nicht dazu verwenden, alle möglichen Eigenschaften von Datenflussobjekten anzuzeigen, die Eigenschaftsausdrücke unterstützen. Wenn Sie eine ADO NET-Quelle auf die Designer-Oberfläche platziert haben z. B. die **Eigenschaft** Liste enthält einen Eintrag für die `[ADO NET Source].[SqlCommand]` Eigenschaft. Die Liste zeigt außerdem viele Eigenschaften des Datenflusstasks selbst an.  
  
## <a name="properties-of-data-flow-objects-that-support-property-expressions"></a>Eigenschaften von Datenflussobjekten, die Eigenschaftsausdrücke unterstützen  
 Die Werte der Eigenschaften in der folgenden Liste können über Eigenschaftsausdrücke angegeben werden.  
  
### <a name="data-flow-sources"></a>Datenflussquellen  
  
|Datenflussobjekt|Eigenschaft|  
|----------------------|--------------|  
|ADO NET-Quelle|TableOrViewName-Eigenschaft<br /><br /> SqlCommand-Eigenschaft|  
|XML-Quelle|XMLData-Eigenschaft<br /><br /> XMLSchemaDefinition-Eigenschaft|  
  
### <a name="data-flow-transformations"></a>Datenflusstransformationen  
 Weitere Informationen zu diesen benutzerdefinierten Eigenschaften finden Sie unter [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
|Datenflussobjekt|Eigenschaft|  
|----------------------|--------------|  
|Transformation für bedingtes Teilen|FriendlyExpression-Eigenschaft|  
|Transformation für abgeleitete Spalten|FriendlyExpression-Eigenschaft|  
|Transformation für Fuzzygruppierung|MaxMemoryUsage-Eigenschaft|  
|Transformation für Fuzzysuche|MaxMemoryUsage-Eigenschaft|  
|Transformation für Suche|SqlCommand-Eigenschaft<br /><br /> SqlCommandParam-Eigenschaft|  
|Transformation für OLE DB-Befehl|SqlCommand-Eigenschaft|  
|Transformation für Prozentwert-Stichproben|SamplingValue-Eigenschaft|  
|Transformation für Pivot|PivotKeyValue-Eigenschaft|  
|Transformation für Zeilenstichproben|SamplingValue-Eigenschaft|  
|Transformation zum Sortieren|MaximumThreads-Eigenschaft|  
|Entpivotierungstransformation|PivotKeyValue-Eigenschaft|  
  
### <a name="data-flow-destinations"></a>Datenflussziele  
  
|Datenflussobjekt|Eigenschaft|  
|----------------------|--------------|  
|ADO NET-Ziel|TableOrViewName-Eigenschaft<br /><br /> BatchSize-Eigenschaft<br /><br /> CommandTimeout-Eigenschaft|  
|Flatfileziel|Header-Eigenschaft|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Ziel|TableName-Eigenschaft|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Ziel|BulkInsertTableName-Eigenschaft<br /><br /> BulkInsertFirstRow-Eigenschaft<br /><br /> BulkInsertLastRow-Eigenschaft<br /><br /> BulkInsertOrder-Eigenschaft<br /><br /> Timeout-Eigenschaft|  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Hinzufügen oder Ändern eines Eigenschaftsausdrucks](expressions/add-or-change-a-property-expression.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Technischer Artikel, [SSIS Expression Cheat Sheet](http://pragmaticworks.com/cheatsheet/), auf pragmaticworks.com  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Eigenschaftsausdrücken in Paketen](expressions/use-property-expressions-in-packages.md)   
 [Allgemeine Eigenschaften](../../2014/integration-services/common-properties.md)   
 [Benutzerdefinierte Eigenschaften der Transformation](data-flow/transformations/transformation-custom-properties.md)   
 [Pfadeigenschaften](../../2014/integration-services/path-properties.md)  
  
  
