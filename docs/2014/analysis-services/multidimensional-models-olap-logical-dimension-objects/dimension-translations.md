---
title: Dimensions Übersetzungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], translations
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- LCIDs
- translations [Analysis Services], dimensions
ms.assetid: 38fc1e05-2ac9-4816-b52b-dfd19c3a43a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f31773ad871ef7e3fc8f99d57e7a9099335b899
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545155"
---
# <a name="dimension-translations"></a>Dimensionsübersetzungen
  Eine Übersetzung ist ein einfaches Verfahren, um die angezeigten Bezeichnungen und Beschriftungen von einer Sprache in eine andere zu ändern. Jede Übersetzung ist als Wertepaar definiert: eine Zeichenfolge mit dem übersetzten Text und eine Zahl mit der Sprach-ID. Übersetzungen sind für alle Objekte in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügbar. In Dimensionen können auch die Attributwerte übersetzt werden. Die Clientanwendung ist verantwortlich dafür, dass die vom Benutzer definierte Spracheinstellung gefunden wird und alle Bezeichnungen und Beschriftungen in der entsprechenden Sprache angezeigt werden. Ein Objekt kann so viele Übersetzungen haben, wie Sie möchten.  
  
 Ein einfaches <xref:Microsoft.AnalysisServices.Translation>-Objekt besteht aus: Sprach-ID-Nummer und übersetzter Beschriftung. Die Sprach-ID-Nummer ist eine `Integer`, die die Sprach-ID enthält. Die übersetzte Beschriftung ist der übersetzte Text.  
  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist eine Dimensions Übersetzung eine sprachspezifische Darstellung des Namens einer Dimension, des Namens eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Objekts oder eines seiner Member, z. b. eine Beschriftung, ein Element oder eine Hierarchieebene. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]unterstützt auch Übersetzungen von Cubeobjekten.  
  
 Übersetzungen bieten Serverunterstützung für Clientanwendungen, die mehrere Sprachen unterstützen können. Häufig werden ein Cube und seine Dimensionen von Benutzern aus verschiedenen Ländern angezeigt. Es ist nützlich, verschiedene Elemente eines Cubes und seiner Dimensionen in eine andere Sprache übersetzen zu können, damit diese Benutzer den Cube anzeigen und verstehen können. So kann z. b. ein Geschäfts Benutzer in Frankreich von einer Arbeitsstation mit einer französischen Gebiets Schema Einstellung auf einen Cube zugreifen und die Objekt Eigenschaftswerte in Französisch anzeigen. Ein Anwender des Produkts im geschäftlichen Bereich in Deutschland jedoch, der über eine Arbeitsstation mit einer deutschen Gebietsschemaeinstellung auf denselben Cube zugreift, sieht die gleichen Objekteigenschaftswerte auf Deutsch.  
  
 Die Sortierungs- und Sprachinformationen für den Clientcomputer werden in Form eines Gebietsschemabezeichners (LCID) gespeichert. Beim Herstellen der Verbindung übergibt der Client die LCID an die Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Die Instanz verwendet den LCID, um zu bestimmen, welche Übersetzungen bei der Bereitstellung von Metadaten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekte verwendet werden sollen. Wenn ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekt die angegebene Übersetzung nicht enthält, wird die Standardsprache verwendet, um den Kontext an den Client zurückzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cubeübersetzungen](../multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [Übersetzungen &#40;Analysis Services&#41;](../translations-analysis-services.md)   
 [Tipps und Best Practices für die Globalisierung &#40;Analysis Services&#41;](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
