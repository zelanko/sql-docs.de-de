---
title: CopyRecordOptionsEnum | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: fe0b12053b9ac7203253e81fa3300d2e4109a129
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681564"
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
Gibt das Verhalten der [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) Methode.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|Gibt an, dass die *Quelle* -Anbieter versucht, simulieren die Kopie über herunterladen und Hochladen Vorgänge aus, wenn diese Methode schlägt, da fehl *Ziel*wird auf einem anderen Server oder von einem anderen gewartet wird -Anbieter als *Quelle*. Beachten Sie, dass unterschiedliche Anbieter möglicherweise behindern die Leistung oder Daten verloren gehen.|  
|**adCopyNonRecursive**|2|Kopiert das aktuelle Verzeichnis, aber keines seiner Unterverzeichnisse an das Ziel an. Der Kopiervorgang ist nicht rekursiv.|  
|**adCopyOverWrite**|1|Überschreibt die Datei oder das Verzeichnis, wenn die *Ziel* verweist auf eine vorhandene Datei oder ein Verzeichnis.|  
|**adCopyUnspecified**|-1|Standard. Die Standard-Kopie durchführt: der Vorgang fehl, wenn die Zieldatei oder das Verzeichnis bereits vorhanden ist, und der Vorgang rekursiv kopiert.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [CopyRecord-Methode (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
