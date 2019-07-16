---
title: Dimension Übersetzungen | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b58303abfd94710452143e014fee0019826a2a97
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68180767"
---
# <a name="dimension-translations"></a>Dimensionsübersetzungen
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Eine Übersetzung ist ein einfaches Verfahren, um die angezeigten Bezeichnungen und Beschriftungen von einer Sprache in eine andere zu ändern. Jede Übersetzung ist als Wertepaar definiert: eine Zeichenfolge mit dem übersetzten Text und eine Zahl mit der Sprach-ID. Übersetzungen sind für alle Objekte in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügbar. In Dimensionen können auch die Attributwerte übersetzt werden. Die Clientanwendung ist verantwortlich dafür, dass die vom Benutzer definierte Spracheinstellung gefunden wird und alle Bezeichnungen und Beschriftungen in der entsprechenden Sprache angezeigt werden. Ein Objekt kann so viele Übersetzungen haben, wie Sie möchten.  
  
 Ein einfaches <xref:Microsoft.AnalysisServices.Translation>-Objekt besteht aus: Sprach-ID-Nummer und übersetzter Beschriftung. Die Sprach-ID-Nummer ist eine **Ganzzahl** mit der Sprach-ID. Die übersetzte Beschriftung ist der übersetzte Text.  
  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], eine dimensionsübersetzung ist eine sprachspezifische Darstellung des Namens einer Dimension, die den Namen des ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Objekt oder eine seiner Elemente, z. B. eine Beschriftung, ein Element oder Hierarchie-Ebene. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt auch Übersetzungen von Cubeobjekten.  
  
 Übersetzungen bieten Serverunterstützung für Clientanwendungen, die mehrere Sprachen unterstützen können. Häufig werden ein Cube und seine Dimensionen von Benutzern aus verschiedenen Ländern angezeigt. Es ist nützlich, verschiedene Elemente eines Cubes und seiner Dimensionen in eine andere Sprache übersetzen zu können, damit diese Benutzer den Cube anzeigen und verstehen können. Ein Geschäftsbenutzer in Frankreich kann z. B. auf einen Cube auf einer Arbeitsstation mit einer französischen gebietsschemaeinstellung zugreifen und die objekteigenschaftswerte auf Französisch angezeigt. Ein Anwender des Produkts im geschäftlichen Bereich in Deutschland jedoch, der über eine Arbeitsstation mit einer deutschen Gebietsschemaeinstellung auf denselben Cube zugreift, sieht die gleichen Objekteigenschaftswerte auf Deutsch.  
  
 Die Sortierungs- und Sprachinformationen für den Clientcomputer werden in Form eines Gebietsschemabezeichners (LCID) gespeichert. Beim Herstellen der Verbindung übergibt der Client die LCID an die Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Die Instanz verwendet den LCID, um zu bestimmen, welche Übersetzungen bei der Bereitstellung von Metadaten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekte verwendet werden sollen. Wenn ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekt die angegebene Übersetzung nicht enthält, wird die Standardsprache verwendet, um den Kontext an den Client zurückzugeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Cubeübersetzungen](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [Unterstützung für Übersetzungen in Analysis Services](../../analysis-services/translation-support-in-analysis-services.md)   
 [Tipps und Best Practices für die Globalisierung &#40;Analysis Services&#41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
