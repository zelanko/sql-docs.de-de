---
title: Cubeübersetzungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- cubes [Analysis Services], translations
- OLAP objects [Analysis Services], translations
- translations [Analysis Services], cubes
ms.assetid: 4e4fd6a4-d324-4508-b75a-2a57de9ab8ff
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8cd4347baae8504ef5dd0f13a3adcca634c49ea2
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545272"
---
# <a name="cube-translations"></a>Cubeübersetzungen
  Eine Übersetzung ist ein einfaches Verfahren, um die angezeigten Bezeichnungen und Beschriftungen von einer Sprache in eine andere zu ändern. Jede Übersetzung ist als Wertepaar definiert: eine Zeichenfolge mit dem übersetzten Text und eine Zahl mit der Sprach-ID. Übersetzungen sind für alle Objekte in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügbar. In Dimensionen können auch die Attributwerte übersetzt werden. Die Clientanwendung ist verantwortlich dafür, dass die vom Benutzer definierte Spracheinstellung gefunden wird und alle Bezeichnungen und Beschriftungen in der entsprechenden Sprache angezeigt werden. Ein Objekt kann so viele Übersetzungen haben, wie Sie möchten.  
  
 Ein einfaches <xref:Microsoft.AnalysisServices.Translation>-Objekt besteht aus: Sprach-ID-Nummer und übersetzter Beschriftung. Die Sprach-ID-Nummer ist eine `Integer`, die die Sprach-ID enthält. Die übersetzte Beschriftung ist der übersetzte Text.  
  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist eine Cube-Übersetzung eine sprachspezifische Darstellung des Namens eines Cube-Objekts, z. b. eine Beschriftung oder ein Anzeige Ordner. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt auch Übersetzungen von Dimensions- und Elementnamen.  
  
 Übersetzungen bieten Serverunterstützung für Clientanwendungen, die mehrere Sprachen unterstützen können. Es kommt häufig vor, dass Cubedaten von Benutzern aus unterschiedlichen Ländern angezeigt werden. Es ist nützlich, verschiedene Elemente eines Cubes in eine andere Sprache übersetzen zu können, damit diese Benutzer die Metadaten des Cubes anzeigen und verstehen können. So kann beispielsweise ein Anwender des Produkts im geschäftlichen Bereich in Frankreich über eine Arbeitsstation mit einer französischen Gebietsschemaeinstellung auf einen Cube zugreifen und die Objekteigenschaftswerte auf Französisch anzeigen. Ein Anwender des Produkts im geschäftlichen Bereich in Deutschland wiederum kann über eine Arbeitsstation mit einer deutschen Gebietsschemaeinstellung auf denselben Cube zugreifen und die Objekteigenschaftswerte auf Deutsch anzeigen.  
  
 Die Sortierungs- und Sprachinformationen für den Clientcomputer werden in Form eines Gebietsschemabezeichners (LCID) gespeichert. Beim Herstellen der Verbindung übergibt der Client die LCID an die Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Die Instanz verwendet den LCID, um zu bestimmen, welche Übersetzungen bei der Bereitstellung von Metadaten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekte für die einzelnen Anwender des Produkts im geschäftlichen Bereich verwendet werden sollen. Wenn ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekt die angegebene Übersetzung nicht enthält, wird die Standardsprache verwendet, um den Kontext an den Client zurückzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions Übersetzungen](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Übersetzungen &#40;Analysis Services&#41;](../translations-analysis-services.md)   
 [Tipps und Best Practices für die Globalisierung &#40;Analysis Services&#41;](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
