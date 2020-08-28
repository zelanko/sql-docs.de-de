---
description: NamedParameters-Eigenschaft (ADO)
title: NamedParameters-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 18552a7d15a5dbe36a05c7391d0fd7e2ab3a6d94
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990491"
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