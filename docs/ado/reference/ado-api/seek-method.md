---
description: Seek-Methode
title: Seek-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b2058751177d0498e89d1f9bd631a3151490c9d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989161"
---
# <a name="seek-method"></a>Seek-Methode
Durchsucht den Index eines [Recordsets](./recordset-object-ado.md) , um die Zeile, die mit den angegebenen Werten übereinstimmt, schnell zu finden und die aktuelle Zeilen Position in diese Zeile zu ändern.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Parameter  
 *KeyValues*  
 Ein Array von **Variant** -Werten. Ein Index besteht aus einer oder mehreren Spalten, und das Array enthält einen Wert, der mit jeder entsprechenden Spalte verglichen werden soll.  
  
 *Seekoption*  
 Ein [seekenum](./seekenum.md) -Wert, der den Typ des Vergleichs angibt, der zwischen den Spalten des Indexes und den entsprechenden *KeyValues*vorgenommen werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Seek** -Methode in Verbindung mit der [Index](./index-property.md) -Eigenschaft, wenn der zugrunde liegende Anbieter Indizes für das **Recordset** -Objekt unterstützt. Verwenden Sie die [Unterstützung](./supports-method.md)**(adSeek)** -Methode, um zu bestimmen, ob der zugrunde liegende Anbieter **Seek**unterstützt, und die **unterstützte (adIndex)** -Methode, um zu bestimmen, ob der Anbieter Indizes (Beispielsweise unterstützt der [OLE DB Anbieter für Microsoft Jet](../../guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) **Seek** und **Index**.)  
  
 Wenn **Seek** die gewünschte Zeile nicht findet, tritt kein Fehler auf, und die Zeile wird am Ende des **Recordsets**positioniert. Legen Sie die **Index** -Eigenschaft auf den gewünschten Index fest, bevor Sie diese Methode ausführen.  
  
 Diese Methode wird nur mit serverseitigen Cursorn unterstützt. Seek wird nicht unterstützt, wenn der [Cursor Location](./cursorlocation-property-ado.md) -Eigenschafts Wert des **Recordset** -Objekts **adUseClient**ist.  
  
 Diese Methode kann nur verwendet werden, wenn das **Recordset** -Objekt mit einem [CommandTypeEnum](./commandtypeenum.md) -Wert von **adCmdTableDirect**geöffnet wurde.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die Seek-Methode und Index-Eigenschaft (VB)](./seek-method-and-index-property-example-vb.md)   
 [Beispiel für die Seek-Methode und Index-Eigenschaft (VC + +)](./seek-method-and-index-property-example-vc.md)   
 [Find-Methode (ADO)](./find-method-ado.md)   
 [Index-Eigenschaft](./index-property.md)