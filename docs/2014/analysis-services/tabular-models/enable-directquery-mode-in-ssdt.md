---
title: Aktivieren des DirectQuery-Entwurfsmodus (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: da44ae47d7e6eaea78a1d14736367ed5cc41d311
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172580"
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
  
3.  In der **Eigenschaften** Bereich ändern Sie die Eigenschaft, **DirectQueryMode**zu **auf**.  
  
4.  Wenn Fehler, in Visual Studio vorliegen, öffnen Sie die **Fehlerliste** und beheben Sie alle Probleme, die das Modell für die in den DirectQuery-Modus wechselt verhindern würden.  
  
## <a name="see-also"></a>Siehe auch  
 [DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](directquery-mode-ssas-tabular.md)  
  
  
