---
title: Database-Element für Server (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
author: stevestein
ms.author: sstein
ms.openlocfilehash: 87df538858c9294cb8986da3df0d2b3814411326
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85057763"
---
# <a name="database-element-for-server-dta"></a>Database-Element für Server (DTA)
  Gibt die Datenbank an, die Sie auf einem bestimmten Server optimieren möchten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine.|  
|Standardwert|Keine.|  
|Vorkommen|Einmal oder mehrfach pro `Server`-Element erforderlich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|Übergeordnetes Element|[Server-Element &#40;DTA&#41;](server-element-dta.md)|  
|Untergeordnete Elemente|[Name-Element für Datenbank &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Schema-Element für Datenbank &#40;DTA&#41;](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Bemerkungen  
 Dieses Element hat den Namen **DatabaseDetailsTypecomplexType** im XML-Schema des Datenbankoptimierungsratgebers. Dieses `Database`-Element ist nicht mit dem identisch, dessen übergeordnetes Stammelement das `Configuration`-Element ist. Weitere Informationen finden Sie unter [Database-Element für Konfiguration &#40;DTA&#41;](database-element-for-configuration-dta.md).  
  
## <a name="example"></a>Beispiel  
 Ein Verwendungs Beispiel für das- `Database` Element finden Sie unter [Server-Element &#40;DTA&#41;](server-element-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
