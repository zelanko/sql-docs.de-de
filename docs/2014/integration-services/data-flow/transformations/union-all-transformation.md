---
title: Transformation für UNION ALL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.unionalltrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 27547f95d50bd4552e766184f163dcd3b94a3bb8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162965"
---
# <a name="union-all-transformation"></a>Transformation für UNION ALL
  Die Transformation für UNION ALL kombiniert mehrere Eingaben zu einer einzigen Ausgabe. Beispielsweise können die Ausgaben von fünf verschiedenen Flatfilequellen Eingaben für die Transformation für UNION ALL sein und zu einer einzigen Ausgabe kombiniert werden.  
  
## <a name="inputs-and-outputs"></a>Eingaben und Ausgaben  
 Die Transformationseingaben werden der Transformationsausgabe nacheinander hinzugefügt. Die Zeilen werden nicht neu angeordnet. Falls das Paket eine sortierte Ausgabe erfordert, sollten Sie anstelle der Transformation für UNION ALL die Transformation für Zusammenführen verwenden.  
  
 Die erste Eingabe, die Sie mit der Transformation für UNION ALL verbinden, ist die Eingabe, von der die Transformation die Transformationsausgabe erstellt. Die Spalten in den Eingaben, die Sie anschließend mit der Transformation verbinden, werden den Spalten in der Transformationsausgabe zugeordnet.  
  
 Um Eingaben zusammenzuführen, ordnen Sie Eingabespalten Ausgabespalten zu. Eine Spalte von mindestens einer Eingabe muss jeder Ausgabespalte zugeordnet werden. Für die Zuordnung von zwei Spalten müssen die Metadaten der Spalten übereinstimmen. Beispielsweise müssen die zugeordneten Spalten denselben Datentyp aufweisen.  
  
 Wenn die zugeordneten Spalten Zeichenfolgendaten enthalten und die Ausgabespalte kürzer als die Eingabespalte ist, wird die Ausgabespalte automatisch verlängert, damit die Eingabespalten Platz haben. Für Eingabespalten, die keinen Ausgabespalten zugeordnet werden, werden in den Ausgabespalten NULL-Werte festgelegt.  
  
 Diese Transformation weist mehrere Eingaben und eine Ausgabe auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
## <a name="configuration-of-the-union-all-transformation"></a>Konfiguration der Transformation für UNION ALL  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Transformations-Editor für UNION ALL** festlegen können, finden Sie unter [Union All Transformation Editor](../../union-all-transformation-editor.md).  
  
 Weitere Informationen zu den Eigenschaften, die Sie programmgesteuert festlegen können, finden Sie unter [Common Properties](../../common-properties.md).  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zum Festlegen von Eigenschaften anzuzeigen:  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 [Zusammenführen von Daten mithilfe der Transformation für UNION ALL](union-all-transformation.md)  
  
  