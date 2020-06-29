---
title: Rang folgen Einschränkungs-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba2c9c0c870294069dd1feb4eaabb72211877cc4
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423197"
---
# <a name="precedence-constraint-editor"></a>Rangfolgeneinschränkungs-Editor
  Verwenden Sie das Dialogfeld **Rangfolgeneinschränkungs-Editor** , um Rangfolgeneinschränkungen zu konfigurieren.  
  
## <a name="options"></a>Optionen  
 **Auswertungsvorgang**  
 Geben Sie den Auswertungsvorgang an, den die Rangfolgeneinschränkung verwendet. Dazu zählen die folgenden Vorgänge: **Einschränkung**, **Ausdruck**, **Ausdruck und Einschränkung**und **Ausdruck oder Einschränkung**.  
  
 **Wert**  
 Geben Sie den Einschränkungswert an: **Erfolg**, **Fehler**oder **Beendigung**.  
  
> [!NOTE]  
>   Die Rangfolgeneinschränkungslinie wird für **Erfolg**grün, für **Fehler**hervorgehoben und für **Beendigung**blau dargestellt.  
  
 **expression**  
 Wenn Sie den Vorgang **Ausdruck**, **Ausdruck und Einschränkung**oder **Ausdruck oder Einschränkung**verwenden, geben Sie einen Ausdruck ein, oder starten Sie den Ausdrucks-Generator, um einen Ausdruck zu erstellen. Der Ausdruck muss zu einem booleschen Wert ausgewertet werden.  
  
 **Test**  
 Überprüfen Sie den Ausdruck.  
  
 **Logisches and**  
 Damit geben Sie an, dass für die ausführbare Datei mehrere Rangfolgeneinschränkungen gemeinsam überprüft werden müssen. Sämtliche Einschränkungen müssen mit `True` ausgewertet werden.  
  
> [!NOTE]  
>  Dieser Typ der Rangfolgeneinschränkung wird als durchgehende grüne, hervorgehobene oder blaue Linie dargestellt.  
  
 **Logisches OR**  
 Damit geben Sie an, dass für die ausführbare Datei mehrere Rangfolgeneinschränkungen gemeinsam überprüft werden müssen. Mindestens eine Einschränkung muss mit `True` ausgewertet werden.  
  
> [!NOTE]  
>  Dieser Typ der Rangfolgeneinschränkung wird als gepunktete grüne, hervorgehobene oder blaue Linie dargestellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rang folgen Einschränkungen](control-flow/precedence-constraints.md)   
 [Aufgaben Integration Services](control-flow/integration-services-tasks.md)   
 [Integration Services Container](control-flow/integration-services-containers.md)   
 [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)  
  
  
