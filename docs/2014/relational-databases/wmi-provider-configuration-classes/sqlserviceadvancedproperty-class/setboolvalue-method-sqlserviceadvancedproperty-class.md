---
title: Haltepunkte festlegen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 911e40506891894213040a02cb439daa6997701a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059683"
---
# <a name="set-breakpoints"></a>Breakpoints festlegen
  Verwenden Sie das Dialogfeld **Breakpoints festlegen** , um die Ereignisse anzugeben, für die Breakpoints aktiviert werden sollen, sowie um das Verhalten der Breakpoints zu steuern.  
  
## <a name="options"></a>Optionen  
 **Aktiviert**  
 Wählen Sie diese Option aus, um einen Breakpoint für ein Ergebnis zu aktivieren.  
  
 **Break Condition**  
 Zeigen Sie eine Liste von verfügbaren Ereignissen an, für die Breakpoints festgelegt werden können.  
  
 **Typ der Treffer Anzahl**  
 Geben Sie an, wann der Breakpoint wirksam werden soll.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Immer**|Die Ausführung wird immer angehalten, wenn der Breakpoint erreicht wird.|  
|**Trefferanzahl ist gleich**|Die Ausführung wird angehalten, wenn die Anzahl des Auftretens des Breakpoints der Trefferanzahl entspricht.|  
|**Trefferanzahl ist größer als oder gleich**|Die Ausführung wird angehalten, wenn die Anzahl des Auftretens des Breakpoints mindestens so groß wie die Trefferanzahl ist.|  
|**Trefferanzahl mehrfach**|Die Ausführung wird angehalten, wenn ein Mehrfaches der Trefferanzahl erreicht wird. Wenn Sie z. B. diese Option auf 5 festlegen, wird die Ausführung bei jedem fünften Mal angehalten.|  
  
 **Treffer Anzahl**  
 Geben Sie die Anzahl der Treffer an, nach denen ein Breakpoint ausgelöst werden soll. Diese Option ist nicht verfügbar, wenn der Breakpoint immer wirksam ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen der Ablaufsteuerung](../../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  
