---
title: Verwalten von Caches (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1080db165770b414d15e4ffb43daf5466021a71a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63262079"
---
# <a name="managing-caches-xmla"></a>Verwalten von Caches (XMLA)
  Sie können die [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) -Befehl in XML for Analysis (XMLA) zum Löschen des Caches von einer angegebenen Dimension oder Partition. Das Löschen des Cache zwingt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] den Cache für dieses Objekt neu erstellen.  
  
## <a name="specifying-objects"></a>Angeben von Objekten  
 Die [Objekt](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) Eigenschaft der **ClearCache** Befehl kann einen Objektverweis nur für eine der folgenden Objekte enthalten. Bei einem Objektverweis, der sich nicht auf eines der folgenden Objekte bezieht, tritt ein Fehler auf:  
  
 Datenbank  
 Löscht den Cache für alle Dimensionen und Partitionen, die in der Datenbank enthalten sind.  
  
 Dimension  
 Löscht den Cache für die angegebene Dimension.  
  
 Cube  
 Löscht den Cache für alle Partitionen, die in den Measuregruppen für den Cube enthalten sind.  
  
 Measuregruppe  
 Löscht den Cache für alle Partitionen, die in der Measuregruppe enthalten sind.  
  
 Partition  
 Löscht den Cache für die angegebene Partition.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
