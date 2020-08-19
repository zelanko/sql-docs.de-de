---
description: Bookmark-Eigenschaft (ADO)
title: Bookmark-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Bookmark
helpviewer_keywords:
- Bookmark property [ADO]
ms.assetid: 481dcc93-487b-490e-ac58-a1e9b2ebfd43
author: rothja
ms.author: jroth
ms.openlocfilehash: b3ab83bb44bca7598074eb81d832ca9ed9b954d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451112"
---
# <a name="bookmark-property-ado"></a>Bookmark-Eigenschaft (ADO)
Gibt ein Lesezeichen an, das den aktuellen Datensatz in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt eindeutig identifiziert, oder legt den aktuellen Datensatz in einem **Recordset** -Objekt auf den Datensatz fest, der durch ein gültiges Lesezeichen identifiziert wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Variant** -Ausdruck fest, der ein gültiges Lesezeichen ergibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Bookmark** -Eigenschaft, um die Position des aktuellen Datensatzes zu speichern und jederzeit zu diesem Datensatz zurückzukehren. Lesezeichen sind nur in **Recordset** -Objekten verfügbar, die Lesezeichen Funktionen unterstützen.  
  
 Wenn Sie ein **Recordset** -Objekt öffnen, verfügt jeder seiner Datensätze über ein eindeutiges Lesezeichen. Um das Lesezeichen für den aktuellen Datensatz zu speichern, weisen Sie den Wert der **Bookmark** -Eigenschaft einer Variablen zu. Wenn Sie nach dem Wechsel zu einem anderen Datensatz jederzeit zu diesem Datensatz zurückkehren möchten, legen Sie die **Bookmark** -Eigenschaft des **Recordset** -Objekts auf den Wert dieser Variablen fest.  
  
 Der Benutzer ist möglicherweise nicht in der Lage, den Wert des Lesezeichens anzuzeigen. Außerdem sollten die Benutzer nicht erwarten, dass Lesezeichen direkt vergleichbar sind, da zwei Lesezeichen, die auf denselben Datensatz verweisen, möglicherweise unterschiedliche Werte aufweisen.  
  
 Wenn Sie die [Clone](../../../ado/reference/ado-api/clone-method-ado.md) -Methode verwenden, um eine Kopie eines **Recordset** -Objekts zu erstellen, sind die **Lesezeichen** Eigenschafts Einstellungen für das ursprüngliche und das doppelte Recordsetobjekt identisch, und Sie können Sie austauschbar verwenden. **Recordset** Es ist jedoch nicht möglich, Lesezeichen aus unterschiedlichen **Recordset** -Objekten austauschbar zu verwenden, auch wenn Sie aus derselben Quelle oder demselben Befehl erstellt wurden.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Bei Verwendung auf einem Client seitigen **Recordset** -Objekt ist die **Bookmark** -Eigenschaft immer verfügbar.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [BOF-, EOF-und Bookmark Properties-Beispiel (VB)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF-, EOF-und Bookmark-Eigenschaften Beispiel (VC + +)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Supports-Methode](../../../ado/reference/ado-api/supports-method.md)
