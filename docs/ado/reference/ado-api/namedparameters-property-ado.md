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
ms.openlocfilehash: ff11a0f5211c0f77ccd36b58ea6b8a5699a390cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443182"
---
# <a name="namedparameters-property-ado"></a>NamedParameters-Eigenschaft (ADO)
Gibt an, ob Parameternamen an den Anbieter übergeben werden sollen.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn diese Eigenschaft den Wert true hat, übergibt ADO den Wert der **Name** -Eigenschaft jedes Parameters in der **Parameter** Auflistung für das [Command-Objekt](../../../ado/reference/ado-api/command-object-ado.md). Der Anbieter verwendet einen Parameternamen, um die Parameter in den **CommandText** -oder **CommandStream** -Eigenschaften zu vergleichen. Wenn diese Eigenschaft false (Standardeinstellung) ist, werden Parameternamen ignoriert, und der Anbieter verwendet die Reihenfolge der Parameter, um Werte in den **CommandText** -oder **CommandStream** -Eigenschaften mit Parametern zu vergleichen.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CommandText-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandStream-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Parameters-Collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
