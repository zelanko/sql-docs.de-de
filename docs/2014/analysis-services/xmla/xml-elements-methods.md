---
title: Methoden (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c1e073eae6637b726a473ea7bf95057ed1548982
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088590"
---
# <a name="methods-xmla"></a>Methoden (XMLA)
  Die XML for Analysis (XMLA)-Protokoll verwendet zwei Methoden, `Discover` und `Execute`, um eine Standardmethode für den Zugriff auf die Informationen in einer Instanz von bieten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Da diese Methoden mit Simple Object Access-Protokoll (SOAP) aufgerufen werden, akzeptieren Sie Eingaben und übermitteln Ausgaben in XML. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementiert beide Methoden gemäß der XML for Analysis 1.1-Spezifikation.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In den folgenden Themen werden die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementierten XMLA-Methoden beschrieben.  
  
|Methode|Description|  
|------------|-----------------|  
|[Discover-Methode &#40;XMLA&#41;](xml-elements-methods-discover.md)|Ruft Informationen wie die Liste der verfügbaren Datenbanken oder die Details zu einem bestimmten Objekt von einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ab. Die Daten abgerufen werden, mit der `Discover` Methode hängt von der Werte der Parameter übergeben.|  
|[Execute-Methode &#40;XMLA&#41;](xml-elements-methods-execute.md)|Sendet XMLA-Befehle an eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Dies schließt Anforderungen im Zusammenhang mit Datenübertragung ein, z. B. das Abrufen oder Aktualisieren von Daten auf dem Server.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Elemente &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [XML-Datentypen &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [XML-Elemente &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)  
  
  
