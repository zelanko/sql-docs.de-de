---
title: Server-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f6c73db809e81cc9b6d1ee182227078a83688384
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63273431"
---
# <a name="server-element-dta"></a>Server-Element (DTA)
  Enthält die Identifikationsinformationen für den Server, auf dem sich die zu optimierenden Datenbanken befinden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmal pro `DTAInput`-Element erforderlich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[DTAInput-Element &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Untergeordnete Elemente**|[Name-Element für Server &#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Database-Element für Server &#40;DTA&#41;](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>Hinweise  
 Geben Sie nur einen `Server` -Element für die `DTAInput` Element. Dieses Element hat im DTA-XML-Schema den Namen **ServerDetailsTypecomplexType** . Dieses `Server`-Element ist nicht mit dem untergeordneten Element für das `Configuration`-Element identisch. Weitere Informationen finden Sie unter [Server-Element für Konfiguration &#40;DTA&#41;](server-element-for-configuration-dta.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie die **Sales.SalesPerson** -Tabelle in der **AdventureWorks** -Datenbank auf SERVER001 angegeben wird:  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
