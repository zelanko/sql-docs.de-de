---
title: DTAXML-Element (DTA)
description: Im dta-Hilfsprogramm enthält das DTAXML-Element alle Elemente, die die vom Datenbankoptimierungsratgeber generierte Optimierungseingabe und -ausgabe beschreiben.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 9dd7f40c3cfbac8739caacc10eb821fcd8b8845b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785996"
---
# <a name="dtaxml-element-dta"></a>DTAXML-Element (DTA)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Das Stammelement einer XML-Eingabe- oder -Ausgabedatei des Datenbankoptimierungsratgebers. **DTAXML** enthält alle Elemente, die die vom Datenbankoptimierungsratgeber generierte Optimierungseingabe und -ausgabe beschreiben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|**xmlns:xsi**|Erforderlich. Identifiziert den XML-Schemainstanzennamespace. Attribute aus diesem Namespace dienen zum Verweisen auf das Schema, das zum Überprüfen der XML-Datei des Datenbankoptimierungsratgebers verwendet wird.<br /><br /> Erforderlicher Wert: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|**xmlns**|Erforderlich. Identifiziert den Namespace des Datenbankoptimierungsratgebers.<br /><br /> Wenn Sie die XML-Datei des Datenbankoptimierungsratgebers mit dem XML-Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]bearbeiten, wird dieser Wert von der F1-Hilfe und der dynamischen Hilfe verwendet, um mögliche Referenzthemen in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation zu ermitteln.<br /><br /> Erforderlicher Wert:<br /><br /> für das[XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?LinkId=43100)|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmal pro DTA XML-Datei erforderlich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|Keine|  
|**Untergeordnete Elemente**|[DTAInput-Element &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)<br /><br /> **DTAOutput**-Element (weitere Informationen finden Sie im Thema zum [XML-Schema für den Datenbankoptimierungsratgeber](https://schemas.microsoft.com/sqlserver/))|  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen zu XML-Namespaces finden Sie unter [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) (in Englisch) in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="example"></a>Beispiel  
 Beispiele für typische **DTAXML**-Elemente finden Sie unter [Beispiele für XML-Eingabedateien &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)   
 [Starten und Verwenden des Datenbankoptimierungsratgebers](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
