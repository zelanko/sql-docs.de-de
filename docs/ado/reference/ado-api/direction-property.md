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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6135650d3b5cb015fad21d1eac7b350827965ca1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933076"
---
# <a name="direction-property"></a>Direction-Eigenschaft
Gibt an, ob die [Parameter](../../../ado/reference/ado-api/parameter-object.md) stellt einen Eingabeparameter, Ausgabeparameter, eine Eingabe und ein Output-Parameter, oder wenn der Parameter den Rückgabewert einer gespeicherten Prozedur ist.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) Wert.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Richtung** Eigenschaft, um anzugeben, wie ein Parameter in oder aus einer Prozedur übergeben wird. Die **Richtung** Eigenschaft schreibgeschützt ist; dies können Sie mit Anbietern arbeiten, die keine dieser Informationen zurückgeben oder diese Informationen fest, wenn Sie nicht, ADO, um einen zusätzlichen Aufruf an den Anbieter zum Abrufen von Informationen zu den Parametern zu machen möchten.  
  
 Nicht alle Anbieter können die Richtung der Parameter in ihre gespeicherten Prozeduren ermitteln. In diesen Fällen müssen Sie festlegen der **Richtung** Eigenschaft vor der Ausführung der Abfrage.  
  
## <a name="applies-to"></a>Gilt für  
 [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
