---
description: Update Resync – dynamische Eigenschaft (ADO)
title: Aktualisieren Sie die Resync-Eigenschaft dynamisch (ADO) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 43657b3dddcf53f9aa9df507c646b7f23088f0ef
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441632"
---
# <a name="update-resync-property-dynamic-ado"></a>Update Resync – dynamische Eigenschaft (ADO)
Gibt an, ob auf die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Methode ein impliziter Vorgang zum [erneuten Synchronisieren](../../../ado/reference/ado-api/resync-method.md) der Methode folgt, und wenn ja, der Gültigkeitsbereich dieses Vorgangs.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen oder mehrere der [ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md) Werte fest oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Werte ADCPROP_UPDATERESYNC_ENUM können kombiniert werden, mit Ausnahme von adresyncall, das bereits die Kombination der restlichen Werte darstellt.  
  
 Die Konstante **adresyncconflicts** speichert die Werte für die erneute Synchronisierung als zugrunde liegende Werte, überschreibt jedoch ausstehende Änderungen nicht.  
  
 **Update Resync** ist eine dynamische Eigenschaft, die an die Auflistung der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) angehängt wird, wenn die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
