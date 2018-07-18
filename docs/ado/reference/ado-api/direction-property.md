---
title: Richtungseigenschaft | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Direction
helpviewer_keywords:
- Direction property
ms.assetid: d5732578-3434-4dcd-a9f7-db1abd1b3b94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab3eecc4e1d4ec0f14634d9c5ce77375f7432231
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277899"
---
# <a name="direction-property"></a>Direction-Eigenschaft
Gibt an, ob die [Parameter](../../../ado/reference/ado-api/parameter-object.md) Eingabeparameter, Ausgabeparameter, Eingabe und ein Output-Parameter darstellt oder wenn der Parameter der Rückgabewert einer gespeicherten Prozedur ist.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) Wert.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Richtung** Eigenschaft, um anzugeben, wie ein Parameter oder an eine Prozedur übergeben wird. Die **Richtung** Eigenschaft gilt Lese-/Schreibzugriff, daher können Sie mit Anbietern arbeiten, die keine dieser Informationen zurückgeben oder diese Informationen festgelegt, wenn Sie nicht, dass die ADO stellen einen zusätzlichen Aufruf an den Anbieter, um Parameterinformationen abzurufen möchten.  
  
 Nicht alle Anbieter können die Richtung von Parametern in ihren gespeicherten Prozeduren bestimmen. In diesen Fällen müssen Sie festlegen der **Richtung** Eigenschaft, bevor Sie die Abfrage ausführen.  
  
## <a name="applies-to"></a>Gilt für  
 [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveConnection, CommandText CommandTimeout, Befehlstyp (CommandType), Größe und Eigenschaften Beispiel für die Richtung (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText CommandTimeout, Befehlstyp (CommandType), Größe und Richtung Eigenschaften (VC++-Beispiel)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText CommandTimeout, Befehlstyp (CommandType), Größe und Eigenschaften Beispiel für die Richtung (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
