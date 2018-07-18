---
title: Verwalten von Caches (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a6644b7caff5da31261b115bfc5608823622260a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022767"
---
# <a name="managing-caches-xmla"></a>Verwalten von Caches (XMLA)
  Sie können die [ClearCache](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md) -Befehl in XML for Analysis (XMLA) auf den Cache einer angegebenen Dimension oder Partition zu löschen. Das Löschen des Cache zwingt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] den Cache für dieses Objekt neu erstellen.  
  
## <a name="specifying-objects"></a>Angeben von Objekten  
 Die [Objekt](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) Eigenschaft von der **ClearCache** Befehl einen Objektverweis nur für eines der folgenden Objekte enthalten kann. Bei einem Objektverweis, der sich nicht auf eines der folgenden Objekte bezieht, tritt ein Fehler auf:  
  
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
  
  
