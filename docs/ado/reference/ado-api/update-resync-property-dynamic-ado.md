---
title: Aktualisieren Sie die erneute Synchronisierung dynamische Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Update Resync property [ADO]
ms.assetid: 8a3bb608-66d7-4128-a3ef-84cb0556de0d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43b8864d03e3ec2e563984e203779e5905a15813
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63042571"
---
# <a name="update-resync-property-dynamic-ado"></a>Update Resync – dynamische Eigenschaft (ADO)
Gibt an, ob die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Methode einen impliziten folgt [Resync](../../../ado/reference/ado-api/resync-method.md) Vorgangs-Methode, und wenn Ja, im Rahmen dieses Vorgangs.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt eine oder mehrere der der [ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md) Werte.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte der ADCPROP_UPDATERESYNC_ENUM können kombiniert werden, mit Ausnahme von AdResyncAll, die bereits die Kombination aus den restlichen Werten darstellt.  
  
 Die Konstante **AdResyncConflicts** speichert die Werte für die erneute Synchronisierung als zugrunde liegenden Werte, aber überschreibt nicht die ausstehenden Änderungen.  
  
 **Aktualisieren Sie die erneute Synchronisierung** wird eine dynamische Eigenschaft angefügt der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung bei der [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaftensatz auf **AdUseClient**.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
