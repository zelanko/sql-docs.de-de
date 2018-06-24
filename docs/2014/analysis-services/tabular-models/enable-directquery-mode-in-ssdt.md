---
title: Aktivieren von DirectQuery-Entwurfsmodus (SSAS – tabellarisch) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1ba954a8f296200070493625803aad263fa71520
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050657"
---
# <a name="enable-directquery-design-mode-ssas-tabular"></a>Aktivieren des DirectQuery-Entwurfsmodus (SSAS – tabellarisch)
  Um im DirectQuery-Modus ein Modell zu erstellen, müssen Sie zuerst die Entwurfszeitumgebung ändern, damit sie den Benutzer des DirectQuery-Modus unterstützt. Wenn Sie so vorgehen, führt der Designer ebenfalls die folgenden Schritte aus:  
  
-   Aktivieren der Verwendung der DirectQuery-Bereitstellungseigenschaften.  
  
-   Ändern der Arbeitsbereichsdatenbank für die Ausführung in einem Hybridmodus, der den Cache für Entwürfe verwendet. Wenn Sie das Modell tatsächlich bereitstellen, wird der Modus wieder in den Wert geändert, der in den Projektbereitstellungseigenschaften angegeben wurde.  
  
-   Deaktivieren der Entwurfsfunktionen, die mit dem DirectQuery-Modus nicht kompatibel sind.  
  
-   Validieren des vorhandenen Modells.  
  
 Diese Prozedur beschreibt, wie der DirectQuery-Modus im Designer aktiviert wird.  
  
### <a name="to-enable-use-of-directquery-in-a-model"></a>So aktivieren Sie die Verwendung von DirectQuery in einem Modell  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], öffnen Sie die Projektmappendatei.  
  
2.  Doppelklicken Sie in Objekt-Explorer auf die Datei "Model.bim".  
  
3.  In der **Eigenschaften** Bereich, ändern Sie die Eigenschaft **DirectQueryMode**in **auf**.  
  
4.  Wenn Fehler vorhanden, in Visual Studio sind, öffnen Sie die **Fehlerliste** und beheben Sie alle Probleme, die das Modell in den DirectQuery-Modus wechselt verhindern würden.  
  
## <a name="see-also"></a>Siehe auch  
 [DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](directquery-mode-ssas-tabular.md)  
  
  