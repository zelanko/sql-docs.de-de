---
title: Transformation für Multicast | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multicasttrans.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b5c0a38c966c89f426a213f302b45c390b77cfe
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437607"
---
# <a name="multicast-transformation"></a>Transformation für Multicast
  Die Multicasttransformation verteilt ihre Eingabe an mindestens eine Ausgabe. Diese Transformation ist mit der Transformation für bedingtes Teilen vergleichbar. Beide Transformationen leiten eine Ausgabe an mehrere Ausgaben weiter. Der Unterschied zwischen den beiden Transformationen besteht darin, dass die Multicasttransformation jede Zeile an jede Ausgabe weiterleitet, während die Transformation für bedingtes Teilen eine Zeile an eine einzelne Ausgabe weiterleitet. Weitere Informationen finden Sie unter [Conditional Split Transformation](conditional-split-transformation.md).  
  
 Zum Konfigurieren der Multicasttransformation fügen Sie Ausgaben hinzu.  
  
 Mithilfe der Multicasttransformation kann ein Paket logische Kopien von Daten erstellen. Dies ist hilfreich, wenn das Paket mehrere Transformationen auf dieselben Daten anwenden muss. Angenommen, eine Kopie der Daten wird aggregiert und nur die Zusammenfassungsinformationen werden in das Ziel geladen, während die andere Kopie der Daten mit Nachschlagewerten und abgeleiteten Spalten erweitert wird, bevor sie in das Ziel geladen wird.  
  
 Diese Transformation weist eine Eingabe und mehrere Ausgaben auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
## <a name="configuration-of-the-multicast-transformation"></a>Konfiguration der Multicasttransformation  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Transformations-Editor für Multicast** festlegen können, finden Sie unter [Multicast Transformation Editor](../../multicast-transformation-editor.md).  
  
 Weitere Informationen zu den Eigenschaften, die Sie programmgesteuert festlegen können, finden Sie unter [Common Properties](../../common-properties.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Festlegen der Eigenschaften dieser Komponente finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenfluss](../data-flow.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)  
  
  
