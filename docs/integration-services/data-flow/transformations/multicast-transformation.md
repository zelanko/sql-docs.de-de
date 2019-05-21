---
title: Transformation für Multicast | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.multicasttrans.f1
- sql13.dts.designer.multicasttransformation.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d81de36b6d0e8df65e1b744b284d9c96dec5d9d0
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65725954"
---
# <a name="multicast-transformation"></a>Transformation für Multicast

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Die Multicasttransformation verteilt ihre Eingabe an mindestens eine Ausgabe. Diese Transformation ist mit der Transformation für bedingtes Teilen vergleichbar. Beide Transformationen leiten eine Ausgabe an mehrere Ausgaben weiter. Der Unterschied zwischen den beiden Transformationen besteht darin, dass die Multicasttransformation jede Zeile an jede Ausgabe weiterleitet, während die Transformation für bedingtes Teilen eine Zeile an eine einzelne Ausgabe weiterleitet. Weitere Informationen finden Sie unter [Conditional Split Transformation](../../../integration-services/data-flow/transformations/conditional-split-transformation.md).  
  
 Zum Konfigurieren der Multicasttransformation fügen Sie Ausgaben hinzu.  
  
 Mithilfe der Multicasttransformation kann ein Paket logische Kopien von Daten erstellen. Dies ist hilfreich, wenn das Paket mehrere Transformationen auf dieselben Daten anwenden muss. Angenommen, eine Kopie der Daten wird aggregiert und nur die Zusammenfassungsinformationen werden in das Ziel geladen, während die andere Kopie der Daten mit Nachschlagewerten und abgeleiteten Spalten erweitert wird, bevor sie in das Ziel geladen wird.  
  
 Diese Transformation weist eine Eingabe und mehrere Ausgaben auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
## <a name="configuration-of-the-multicast-transformation"></a>Konfiguration der Multicasttransformation  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie programmgesteuert festlegen können, finden Sie unter [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796).  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Festlegen der Eigenschaften dieser Komponente finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="multicast-transformation-editor"></a>Transformations-Editor für Multicast
  Mithilfe des Dialogfelds **Transformations-Editor für Multicast** können Sie die Eigenschaften für die einzelnen Transformationsausgaben anzeigen und festlegen.  
  
### <a name="options"></a>Optionen  
 **Ausgaben**  
 Wählen Sie auf der linken Seite eine Ausgabe, um die entsprechenden Eigenschaften in der Tabelle auf der rechten Seite anzuzeigen.  
  
 **Eigenschaften**  
 Bis auf die Ausnahmen **Name** und **Beschreibung**werden alle Ausgabeeigenschaften schreibgeschützt angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenfluss](../../../integration-services/data-flow/data-flow.md)   
 [SQL Server Integration Services-Transformationen](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
