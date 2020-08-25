---
description: NamedParameters-Eigenschaft (ADO)
title: NamedParameters-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::NamedParameters
helpviewer_keywords:
- NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
author: rothja
ms.author: jroth
ms.openlocfilehash: b520f60f9e08c5580e2f825a76d25c2cdcda6ae0
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774119"
---
# <a name="namedparameters-property-ado"></a>NamedParameters-Eigenschaft (ADO)
Gibt an, ob Parameternamen an den Anbieter übergeben werden sollen.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn diese Eigenschaft den Wert true hat, übergibt ADO den Wert der **Name** -Eigenschaft jedes Parameters in der **Parameter** Auflistung für das [Command-Objekt](./command-object-ado.md). Der Anbieter verwendet einen Parameternamen, um die Parameter in den **CommandText** -oder **CommandStream** -Eigenschaften zu vergleichen. Wenn diese Eigenschaft false (Standardeinstellung) ist, werden Parameternamen ignoriert, und der Anbieter verwendet die Reihenfolge der Parameter, um Werte in den **CommandText** -oder **CommandStream** -Eigenschaften mit Parametern zu vergleichen.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CommandText-Eigenschaft (ADO)](./commandtext-property-ado.md)   
 [CommandStream-Eigenschaft (ADO)](./commandstream-property-ado.md)   
 [Parameters-Collection (ADO)](./parameters-collection-ado.md)