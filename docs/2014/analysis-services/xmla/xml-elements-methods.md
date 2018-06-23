---
title: Methoden (XMLA) | Microsoft Docs
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
topic_type:
- apiref
- apinav
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#
helpviewer_keywords:
- methods [XML for Analysis]
- XML for Analysis, methods
- XMLA, methods
ms.assetid: c6768dd4-ca06-4a85-93b7-5fd5700886ad
caps.latest.revision: 30
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: fe42e2330e3e108ad1ee0e09d1e1e1007eda9102
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163196"
---
# <a name="methods-xmla"></a>Methoden (XMLA)
  Die XML for Analysis (XMLA)-Protokoll verwendet zwei Methoden, `Discover` und `Execute`, um ein gängiges Verfahren für Anwendungen, um den Zugriff auf Informationen in einer Instanz von bieten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Da diese Methoden mit Simple Object Access-Protokoll (SOAP) aufgerufen werden, akzeptieren Sie Eingaben und übermitteln Ausgaben in XML. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementiert beide Methoden gemäß der XML for Analysis 1.1-Spezifikation.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In den folgenden Themen werden die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementierten XMLA-Methoden beschrieben.  
  
|Methode|Description|  
|------------|-----------------|  
|[Discover-Methode &#40;XMLA&#41;](xml-elements-methods-discover.md)|Ruft Informationen wie die Liste der verfügbaren Datenbanken oder die Details zu einem bestimmten Objekt von einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ab. Die Daten abgerufen werden, mit der `Discover` Methode hängt von den Werten der Parameter übergeben wird.|  
|[Execute-Methode &#40;XMLA&#41;](xml-elements-methods-execute.md)|Sendet XMLA-Befehle an eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Dies schließt Anforderungen im Zusammenhang mit Datenübertragung ein, z. B. das Abrufen oder Aktualisieren von Daten auf dem Server.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Elemente &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [XML-Datentypen &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [XML-Elemente &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)  
  
  