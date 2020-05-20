---
title: Direction-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Direction
helpviewer_keywords:
- Direction property
ms.assetid: d5732578-3434-4dcd-a9f7-db1abd1b3b94
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e3f098c0f0351a4439b9bb6fb6256209ea3e1ad
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82757176"
---
# <a name="direction-property"></a>Direction-Eigenschaft
Gibt an, ob der [Parameter](../../../ado/reference/ado-api/parameter-object.md) einen Eingabeparameter, einen Ausgabeparameter, eine Eingabe und einen Ausgabeparameter darstellt oder ob der Parameter der Rückgabewert einer gespeicherten Prozedur ist.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) -Wert fest oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die Eigenschaft **Richtung** , um anzugeben, wie ein Parameter an eine oder aus einer Prozedur übergeben wird. Die **Direction** -Eigenschaft ist Lese-/Schreibzugriff. Dies ermöglicht es Ihnen, mit Anbietern zu arbeiten, die diese Informationen nicht zurückgeben, oder diese Informationen festzulegen, wenn ADO keinen zusätzlichen Abruf an den Anbieter durchführen soll, um Parameterinformationen abzurufen.  
  
 Nicht alle Anbieter können die Richtung der Parameter in Ihren gespeicherten Prozeduren bestimmen. In diesen Fällen müssen Sie die **Direction** -Eigenschaft festlegen, bevor Sie die Abfrage ausführen.  
  
## <a name="applies-to"></a>Gilt für  
 [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
