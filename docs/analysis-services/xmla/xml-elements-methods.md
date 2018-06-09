---
title: Methoden (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 15f930695e13d824e70da748dad20cf574e9bc38
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34579142"
---
# <a name="xml-elements---methods"></a>XML-Elemente - Methoden
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Die XML for Analysis (XMLA)-Protokoll verwendet zwei Methoden, **Discover** und **Execute**, um ein gängiges Verfahren für den Zugriff auf Informationen in einer Instanz von Analysis Services-Anwendungen zu bieten. Da diese Methoden mit Simple Object Access-Protokoll (SOAP) aufgerufen werden, akzeptieren Sie Eingaben und übermitteln Ausgaben in XML. Analysis Services implementiert beide Methoden gemäß der XML for Analysis 1.1-Spezifikation.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Die folgenden Themen beschreiben die XMLA-Methoden, die von Analysis Services implementiert.  
  
|Methode|Description|  
|------------|-----------------|  
|[Discover-Methode &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)|Ruft die Informationen, z. B. die Liste der verfügbaren Datenbanken oder Details zu einem bestimmten Objekt von einer Instanz von Analysis Services ab. Die mit der **Discover** -Methode abgerufenen Daten hängen von den Werten der an sie übergebenen Parameter ab.|  
|[Execute-Methode &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)|Sendet XMLA-Befehle mit einer Instanz von Analysis Services. Dies schließt Anforderungen im Zusammenhang mit Datenübertragung ein, z. B. das Abrufen oder Aktualisieren von Daten auf dem Server.|  
  
## <a name="see-also"></a>Siehe auch
 [XML-Elemente &#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML-Datentypen &#40;XMLA&#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [XML-Elemente &#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
