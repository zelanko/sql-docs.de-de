---
title: Database-Element für Server (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5817a6d32ff94aaba7e4c0a573e6cd6a5fd586dc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68116932"
---
# <a name="database-element-for-server-dta"></a>Database-Element für Server (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Gibt die Datenbank an, die Sie auf einem bestimmten Server optimieren möchten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|und Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine.|  
|Standardwert|Keine.|  
|Vorkommen|Einmal oder mehrfach pro **Server** -Element erforderlich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|Übergeordnetes Element|[Server-Element &#40;DTA&#41;](../../tools/dta/server-element-dta.md)|  
|Untergeordnete Elemente|[Name-Element für Datenbank &#40;DTA&#41;](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [Schema-Element für Datenbank &#40;DTA&#41;](../../tools/dta/schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Bemerkungen  
 Dieses Element hat den Namen **DatabaseDetailsTypecomplexType** im XML-Schema des Datenbankoptimierungsratgebers. Dieses **Database** -Element ist nicht mit dem identisch, dessen übergeordnetes Stammelement das **Configuration** -Element ist. Weitere Informationen finden Sie unter [Database-Element für Konfiguration &#40;DTA&#41;](../../tools/dta/database-element-for-configuration-dta.md).  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung des **Database** -Elements finden Sie unter [Server-Element &#40;DTA&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
