---
title: File-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- File element
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1d74a576ea8d966d5c1a2c802eb42049c33a94b2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097710"
---
# <a name="file-element-dta"></a>File-Element (DTA)
  Gibt die Arbeitsauslastungsdatei an. Die Arbeitsauslastung besteht aus einer Reihe von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, die für eine oder mehrere Datenbanken ausgeführt werden, die Sie optimieren möchten. Arbeitsauslastungsdateien können [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts (SQL) oder Ablaufverfolgungsdateien (TRC) sein. Weitere Informationen finden Sie unter [Starten und Verwenden des Datenbankoptimierungsratgebers](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Mit dem `string`-Datentyp geben Sie den Verzeichnispfad zu der Arbeitsauslastungsdatei an. Zum Beispiel:<br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> Der Grenzwert für die Länge wird vom Server erzwungen.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich, wenn kein anderer Arbeitsauslastungstyp angegeben ist. Sie müssen ein untergeordnetes **EventString**-, **File**- oder **Database** -Element für das übergeordnete **Workload** -Element angeben. Es kann aber nur ein Typ verwendet werden. Wenn Sie beispielsweise eine Arbeitsauslastung mit dem **File** -Element angeben, können Sie in dieser XML-Eingabedatei keine Arbeitsauslastung mit dem **Database** -Element festlegen.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Workload-Element &#40;DTA&#41;](workload-element-dta.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine einfache XML-Eingabedatei &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
