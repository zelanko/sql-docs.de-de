---
title: Hinzufügen einer benutzerdefinierten Aggregation zu einer Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: e647b32d8f94ebd545a9d8d85d066a25dde6e77c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66076913"
---
# <a name="add-a-custom-aggregation-to-a-dimension"></a>Hinzufügen einer benutzerdefinierten Aggregation zu einer Dimension
  Durch das Hinzufügen einer benutzerdefinierten Aggregationserweiterung zu einem Cube oder einer Dimension werden die Standardaggregationen entfernt, die einem Dimensionselement mit einem anderen unären Operator zugeordnet sind. Die Erweiterung legt eine Spalte für unären Operator in der Dimensionstabelle fest, die das Rollup für Elemente in einer Über-/Unterordnungshierarchie definiert. Der unäre Operator bezieht sich auf das übergeordnete Attribut in einer Über-/Unterordnungshierarchie.  
  
> [!NOTE]  
>  Eine benutzerdefinierte Aggregation ist nur für Dimensionen verfügbar, die auf vorhandenen Datenquellen basieren. Für Dimensionen, die ohne Datenquelle erstellt wurden, müssen Sie den Schemagenerierungs-Assistenten ausführen, um vor dem Hinzufügen der benutzerdefinierten Aggregation eine Datenquellensicht zu erstellen.  
  
 Verwenden Sie zum Hinzufügen einer benutzerdefinierten Aggregation den Business Intelligence-Assistenten, und wählen Sie die Option **Unären Operator angeben** auf der Seite **Erweiterung auswählen** aus. Der Assistent leitet Sie dann durch die Schritte zum Auswählen einer Dimension, auf die Sie eine benutzerdefinierte Aggregation anwenden, und zum Identifizieren der benutzerdefinierten Aggregation.  
  
> [!NOTE]  
>  Vor dem Ausführen des Business Intelligence-Assistenten zum Hinzufügen einer benutzerdefinierten Aggregation stellen Sie sicher, dass die Dimension, die Sie erweitern wollen, eine Über-/Unterordnungsattributhierarchie enthält. Weitere Informationen finden Sie unter über [-](parent-child-dimension.md)/unterordnungshierarchie.  
  
## <a name="selecting-a-dimension"></a>Auswählen einer Dimension  
 Auf der ersten Seite **Unären Operator angeben** des Assistenten geben Sie die Dimension an, der Sie eine benutzerdefinierte Aggregation hinzufügen möchten. Die der ausgewählten Dimension hinzugefügte benutzerdefinierte Aggregation führt zu Änderungen an der Dimension. Diese Änderungen werden an alle Cubes vererbt, die die ausgewählte Dimension enthalten.  
  
## <a name="adding-custom-aggregation-unary-operator"></a>Hinzufügen einer benutzerdefinierten Aggregation (unärer Operator)  
 Geben Sie auf der zweiten Seite **Unären Operator angeben** das für die benutzerdefinierte Aggregation gewünschte übergeordnete Attribut und die Quellspalte in der Dimensionstabelle für den unären Operator an. Über **geordnetes Attribut** listet Attribute auf, `Usage` deren-Eigenschaft `Parent`auf festgelegt ist. Sind mehrere übergeordnete Attribute vorhanden, wählen Sie das übergeordnete Attribut aus, das der gewünschten Über-/Unterordnungsbeziehung entspricht. Ist kein übergeordnetes Attribut aufgelistet, besitzt die Dimension keine gültige Über-/Unterordnungshierarchie.  
  
 Wählen Sie in **Quellspalte**die Zeichenfolgenspalte mit den unären Operatoren aus. (Durch diese Auswahl wird `UnaryOperatorColumn` die-Eigenschaft für das übergeordnete Attribut festgelegt.) Die Dimensions Tabelle sollte auch über eine Zeichen folgen Spalte verfügen, die den unären Rollup-Operator angibt. Die Zeichenfolgenwerte in dieser Spalte sollten gültige Aggregationsoperatoren enthalten. Ist die Zeile leer, wird das entsprechende Element normal berechnet. Ist die Formel in der Spalte nicht gültig, gibt es einen Laufzeitfehler, sobald ein Zellwert abgerufen wird, der das Element verwendet. Weitere Informationen finden Sie unter [Unäre Operatoren in über- und untergeordneten Dimensionen](parent-child-dimension-attributes-unary-operators.md).  
  
  
