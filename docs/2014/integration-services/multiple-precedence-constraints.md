---
title: Mehrere Rang folgen Einschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16fefbbf886818989131710876564fc9e147a56a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440137"
---
# <a name="multiple-precedence-constraints"></a>Mehrere Rangfolgeneinschränkungen
  Eine Rangfolgeneinschränkung verbindet zwei ausführbare Dateien: zwei Tasks, zwei Container oder einen Task und einen Container. Sie werden als ausführbare Datei der Rangfolge und als eingeschränkte ausführbare Datei bezeichnet. Eine eingeschränkte ausführbare Datei kann mehrere Rangfolgeneinschränkungen haben. Weitere Informationen finden Sie unter [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md).  
  
 Wenn Sie komplexe Einschränkungsszenarien durch Gruppieren von Einschränkungen zusammenfassen, können Sie eine komplexe Ablaufsteuerung in Paketen implementieren. Beispielsweise ist in der folgenden Abbildung der Task D mit dem Task A durch eine `Success`-Einschränkung verlinkt, der Task D ist mit dem Task B durch eine `Failure`-Einschränkung verlinkt, und der Task D ist mit dem Task C durch eine `Success`-Einschränkung verlinkt. Die Rangfolgeneinschränkungen zwischen Task D und Task A, zwischen Task D und Task B sowie zwischen Task D und Task C nehmen an einer logischen *AND* -Beziehung teil. Damit Task D ausgeführt wird, muss Task A erfolgreich ausgeführt werden, bei Task B muss ein Fehler auftreten, und Task C muss erfolgreich ausgeführt werden.  
  
 ![Durch Rangfolgeneinschränkungen verknüpfte Tasks](media/precedenceconstraints.gif "Durch Rangfolgeneinschränkungen verknüpfte Tasks")  
  
## <a name="logicaland-property"></a>LogicalAnd-Eigenschaft  
 Falls ein Task oder ein Container mehrere Einschränkungen aufweist, gibt die `LogicalAnd`-Eigenschaft an, ob eine Rangfolgeneinschränkung einzeln oder zusammen mit anderen Einschränkungen ausgewertet wird.  
  
 Sie können die- `LogicalAnd` Eigenschaft mithilfe des Rangfolgeneinschränkungs- **Editors** im- [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer oder in der Eigenschaftenfenster festlegen, die [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] bereitstellt.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Festlegen der Eigenschaften von Rangfolgeneinschränkungen](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
