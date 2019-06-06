---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bb835a84d83730e291afcfdf83910f9b520daea6
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696294"
---
# <a name="bookmark-property-ado"></a>Bookmark-Eigenschaft (ADO)
Gibt an, ein Lesezeichen, das den aktuellen Datensatz in eindeutig identifiziert einen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt, oder legt den aktuellen Datensatz einer **Recordset** Objekt, das den Datensatz, der durch ein gültiges Lesezeichen identifiziert wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Variant** Ausdruck, der ein gültiges Lesezeichen ergibt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Lesezeichen** Eigenschaft zu speichern, die Position des aktuellen Datensatzes an diesen Datensatz zu einem beliebigen Zeitpunkt zurück. Lesezeichen stehen nur in **Recordset** Objekte, die Lesezeichenfunktionalität unterstützen.  
  
 Beim Öffnen einer **Recordset** Objekt, jeder Datensatz hat ein eindeutiges Lesezeichen. Um das Lesezeichen für den aktuellen Datensatz speichern zu können, weisen Sie den Wert für die **Lesezeichen** Eigenschaft einer Variablen. Um schnell an diesen Datensatz zu einem beliebigen Zeitpunkt nach dem Wechsel zu einem anderen Datensatz zurückzugeben, legen die **Recordset** des Objekts **Lesezeichen** -Eigenschaft auf den Wert der Variablen.  
  
 Der Benutzer möglicherweise nicht den Wert des Lesezeichens anzeigen können. Darüber hinaus sollten Benutzer keine Lesezeichen direkt vergleichbar, da zwei Lesezeichen, die auf den gleichen Datensatz verweisen unterschiedliche Werte möglicherweise erwarten.  
  
 Bei Verwendung der [Klon](../../../ado/reference/ado-api/clone-method-ado.md) Methode, um eine Kopie erstellen eine **Recordset** Objekt die **Lesezeichen** -eigenschafteneinstellungen für die ursprüngliche und das Duplikat **Recordset**  Objekte identisch sind und Sie können diese austauschbar verwenden. Allerdings können keine Lesezeichen von anderen **Recordset** Objekte untereinander austauschen, auch wenn sie aus der gleichen Quelle oder der Befehl erstellt wurden.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** bei Verwendung für eine clientseitige **Recordset** -Objekt, das **Lesezeichen** Eigenschaft ist immer verfügbar.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [BOF-, EOF- und Bookmark Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF-, EOF- und Bookmark Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Supports-Methode](../../../ado/reference/ado-api/supports-method.md)
