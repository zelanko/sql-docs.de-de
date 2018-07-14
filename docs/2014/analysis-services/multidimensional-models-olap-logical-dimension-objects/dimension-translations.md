---
title: Dimension Übersetzungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], translations
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- LCIDs
- translations [Analysis Services], dimensions
ms.assetid: 38fc1e05-2ac9-4816-b52b-dfd19c3a43a2
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6ad366e146a52eacbad63e5fb3eac71418fd5d34
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243450"
---
# <a name="dimension-translations"></a>Dimensionsübersetzungen
  Eine Übersetzung ist ein einfaches Verfahren, um die angezeigten Bezeichnungen und Beschriftungen von einer Sprache in eine andere zu ändern. Jede Übersetzung ist als Wertepaar definiert: eine Zeichenfolge mit dem übersetzten Text und eine Zahl mit der Sprach-ID. Übersetzungen sind für alle Objekte in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügbar. In Dimensionen können auch die Attributwerte übersetzt werden. Die Clientanwendung ist verantwortlich dafür, dass die vom Benutzer definierte Spracheinstellung gefunden wird und alle Bezeichnungen und Beschriftungen in der entsprechenden Sprache angezeigt werden. Ein Objekt kann so viele Übersetzungen haben, wie Sie möchten.  
  
 Ein einfaches <xref:Microsoft.AnalysisServices.Translation>-Objekt besteht aus: Sprach-ID-Nummer und übersetzter Beschriftung. Die Sprach-ID-Nummer ist eine `Integer`, die die Sprach-ID enthält. Die übersetzte Beschriftung ist der übersetzte Text.  
  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], eine dimensionsübersetzung ist eine sprachspezifische Darstellung des Namens einer Dimension, die den Namen des ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Objekt oder eine seiner Elemente, z. B. eine Beschriftung, ein Element oder Hierarchie-Ebene. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt auch Übersetzungen von Cubeobjekten.  
  
 Übersetzungen bieten Serverunterstützung für Clientanwendungen, die mehrere Sprachen unterstützen können. Häufig werden ein Cube und seine Dimensionen von Benutzern aus verschiedenen Ländern angezeigt. Es ist nützlich, verschiedene Elemente eines Cubes und seiner Dimensionen in eine andere Sprache übersetzen zu können, damit diese Benutzer den Cube anzeigen und verstehen können. Ein Geschäftsbenutzer in Frankreich kann z. B. auf einen Cube auf einer Arbeitsstation mit einer französischen gebietsschemaeinstellung zugreifen und die objekteigenschaftswerte auf Französisch angezeigt. Ein Anwender des Produkts im geschäftlichen Bereich in Deutschland jedoch, der über eine Arbeitsstation mit einer deutschen Gebietsschemaeinstellung auf denselben Cube zugreift, sieht die gleichen Objekteigenschaftswerte auf Deutsch.  
  
 Die Sortierungs- und Sprachinformationen für den Clientcomputer werden in Form eines Gebietsschemabezeichners (LCID) gespeichert. Beim Herstellen der Verbindung übergibt der Client die LCID an die Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Die Instanz verwendet den LCID, um zu bestimmen, welche Übersetzungen bei der Bereitstellung von Metadaten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekte verwendet werden sollen. Wenn ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekt die angegebene Übersetzung nicht enthält, wird die Standardsprache verwendet, um den Kontext an den Client zurückzugeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Cubeübersetzungen](../multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [Übersetzungen &#40;Analysis Services&#41;](../translations-analysis-services.md)   
 [Globalisierung, Tipps und Best Practices &#40;Analysis Services&#41;](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
