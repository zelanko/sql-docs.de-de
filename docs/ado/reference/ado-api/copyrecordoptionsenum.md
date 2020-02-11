---
title: Copyrecordoptionsenum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CopyRecordOptionsEnum
helpviewer_keywords:
- CopyRecordOptionsEnum enumeration [ADO]
ms.assetid: 2fa4eec5-d50b-4fd3-8ae7-40af441ba12b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6692125b7323bedc7a416e51555c373ef850ce0a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919372"
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
Gibt das Verhalten der [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) -Methode an.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adcopyzuwemulations**|4|Gibt an, dass der *Quell* Anbieter versucht, die Kopie mithilfe von Download-und Uploadvorgängen zu simulieren, wenn diese Methode fehlschlägt, weil das *Ziel*auf einem anderen Server ausgeführt wird oder von einem anderen Anbieter als *Quelle*bedient wird. Beachten Sie, dass unterschiedliche Anbieter Funktionen die Leistung beeinträchtigen oder Daten verlieren können.|  
|**adCopyNonRecursive**|2|Kopiert das aktuelle Verzeichnis, aber keines seiner Unterverzeichnisse, in das Ziel. Der Kopiervorgang ist nicht rekursiv.|  
|**adCopyOverwrite**|1|Überschreibt die Datei oder das Verzeichnis, wenn das *Ziel* auf eine vorhandene Datei oder ein vorhandenes Verzeichnis verweist.|  
|**adcopyunspezifiziert**|-1|Default. Führt den Standard Kopiervorgang aus: der Vorgang schlägt fehl, wenn die Zieldatei oder das Verzeichnis bereits vorhanden ist, und der Vorgang wird rekursiv kopiert.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [CopyRecord-Methode (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
