---
title: Legen Sie Haltepunkte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
caps.latest.revision: 23
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 89517b3d1d8ac28db093cb32990f526b98cbf70e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260456"
---
# <a name="set-breakpoints"></a>Breakpoints festlegen
  Verwenden Sie das Dialogfeld **Breakpoints festlegen** , um die Ereignisse anzugeben, für die Breakpoints aktiviert werden sollen, sowie um das Verhalten der Breakpoints zu steuern.  
  
## <a name="options"></a>Tastatur  
 **Enabled**  
 Wählen Sie diese Option aus, um einen Breakpoint für ein Ergebnis zu aktivieren.  
  
 **Unterbrechungsbedingung**  
 Zeigen Sie eine Liste von verfügbaren Ereignissen an, für die Breakpoints festgelegt werden können.  
  
 **Typ der Trefferanzahl**  
 Geben Sie an, wann der Breakpoint wirksam werden soll.  
  
|value|Description|  
|-----------|-----------------|  
|**Always**|Die Ausführung wird immer angehalten, wenn der Breakpoint erreicht wird.|  
|**Trefferanzahl ist gleich**|Die Ausführung wird angehalten, wenn die Anzahl des Auftretens des Breakpoints der Trefferanzahl entspricht.|  
|**Trefferanzahl ist größer als oder gleich**|Die Ausführung wird angehalten, wenn die Anzahl des Auftretens des Breakpoints mindestens so groß wie die Trefferanzahl ist.|  
|**Trefferanzahl mehrfach**|Die Ausführung wird angehalten, wenn ein Mehrfaches der Trefferanzahl erreicht wird. Wenn Sie z. B. diese Option auf 5 festlegen, wird die Ausführung bei jedem fünften Mal angehalten.|  
  
 **Trefferanzahl**  
 Geben Sie die Anzahl der Treffer an, nach denen ein Breakpoint ausgelöst werden soll. Diese Option ist nicht verfügbar, wenn der Breakpoint immer wirksam ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen der Ablaufsteuerung](../../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  
