---
title: Hinzufügen eine benutzerdefinierte Aggregation zu einer Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], custom aggregations
- aggregations [Analysis Services], custom
- unary operators
- custom aggregations [Analysis Services]
ms.assetid: 3199a6c2-a06d-47b9-bd1c-604dbb085318
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 15c37f8fa070c3faf3d8fe5bc86213e90519cf54
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48167380"
---
# <a name="add-a-custom-aggregation-to-a-dimension"></a>Hinzufügen einer benutzerdefinierten Aggregation zu einer Dimension
  Durch das Hinzufügen einer benutzerdefinierten Aggregationserweiterung zu einem Cube oder einer Dimension werden die Standardaggregationen entfernt, die einem Dimensionselement mit einem anderen unären Operator zugeordnet sind. Die Erweiterung legt eine Spalte für unären Operator in der Dimensionstabelle fest, die das Rollup für Elemente in einer Über-/Unterordnungshierarchie definiert. Der unäre Operator bezieht sich auf das übergeordnete Attribut in einer Über-/Unterordnungshierarchie.  
  
> [!NOTE]  
>  Eine benutzerdefinierte Aggregation ist nur für Dimensionen verfügbar, die auf vorhandenen Datenquellen basieren. Für Dimensionen, die ohne Datenquelle erstellt wurden, müssen Sie den Schemagenerierungs-Assistenten ausführen, um vor dem Hinzufügen der benutzerdefinierten Aggregation eine Datenquellensicht zu erstellen.  
  
 Verwenden Sie zum Hinzufügen einer benutzerdefinierten Aggregation den Business Intelligence-Assistenten, und wählen Sie die Option **Unären Operator angeben** auf der Seite **Erweiterung auswählen** aus. Der Assistent leitet Sie dann durch die Schritte zum Auswählen einer Dimension, auf die Sie eine benutzerdefinierte Aggregation anwenden, und zum Identifizieren der benutzerdefinierten Aggregation.  
  
> [!NOTE]  
>  Vor dem Ausführen des Business Intelligence-Assistenten zum Hinzufügen einer benutzerdefinierten Aggregation stellen Sie sicher, dass die Dimension, die Sie erweitern wollen, eine Über-/Unterordnungsattributhierarchie enthält. Weitere Informationen finden Sie unter [über-/ Unterordnungshierarchie](parent-child-dimension.md).  
  
## <a name="selecting-a-dimension"></a>Auswählen einer Dimension  
 Auf der ersten Seite **Unären Operator angeben** des Assistenten geben Sie die Dimension an, der Sie eine benutzerdefinierte Aggregation hinzufügen möchten. Die der ausgewählten Dimension hinzugefügte benutzerdefinierte Aggregation führt zu Änderungen an der Dimension. Diese Änderungen werden an alle Cubes vererbt, die die ausgewählte Dimension enthalten.  
  
## <a name="adding-custom-aggregation-unary-operator"></a>Hinzufügen einer benutzerdefinierten Aggregation (unärer Operator)  
 Geben Sie auf der zweiten Seite **Unären Operator angeben** das für die benutzerdefinierte Aggregation gewünschte übergeordnete Attribut und die Quellspalte in der Dimensionstabelle für den unären Operator an. **Übergeordnetes Attribut** enthält Attribute, verfügen ihre `Usage` -Eigenschaftensatz auf `Parent`. Sind mehrere übergeordnete Attribute vorhanden, wählen Sie das übergeordnete Attribut aus, das der gewünschten Über-/Unterordnungsbeziehung entspricht. Ist kein übergeordnetes Attribut aufgelistet, besitzt die Dimension keine gültige Über-/Unterordnungshierarchie.  
  
 Wählen Sie in **Quellspalte**die Zeichenfolgenspalte mit den unären Operatoren aus. (Diese Auswahl wird die `UnaryOperatorColumn` Eigenschaft für das übergeordnete Attribut.) Die Dimensionstabelle sollte auch über eine Zeichenfolgenspalte verfügen, die den unären Rollup-Operator festlegt. Die Zeichenfolgenwerte in dieser Spalte sollten gültige Aggregationsoperatoren enthalten. Ist die Zeile leer, wird das entsprechende Element normal berechnet. Ist die Formel in der Spalte nicht gültig, gibt es einen Laufzeitfehler, sobald ein Zellwert abgerufen wird, der das Element verwendet. Weitere Informationen finden Sie unter [Unäre Operatoren in über- und untergeordneten Dimensionen](parent-child-dimension-attributes-unary-operators.md).  
  
  
