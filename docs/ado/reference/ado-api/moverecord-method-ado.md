---
title: MoveRecord-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::MoveRecord
- _Record::raw_MoveRecord
helpviewer_keywords:
- MoveRecord method [ADO]
ms.assetid: 6d2807b0-b861-4583-bcaf-fb0b82e0f2d0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2deba8c745b29b5bd69432060debad2c585e31b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242752"
---
# <a name="moverecord-method-ado"></a>MoveRecord-Methode (ADO)
Verschiebt die Entität, dargestellt durch eine [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) an einen anderen Speicherort.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Record.MoveRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Dies ist optional. Ein **Zeichenfolge** -Wert, eine URL identifiziert enthält, die **Datensatz** verschoben werden soll. Wenn *Quelle* ausgelassen wird, oder gibt eine leere Zeichenfolge und das Objekt, das dargestellt durch diese **Datensatz** verschoben wird. Z. B. wenn die **Datensatz** stellt eine Datei, die den Inhalt der Datei werden in den vom angegebenen Speicherort verschoben *Ziel*.  
  
 *Ziel*  
 Dies ist optional. Ein **Zeichenfolge** -Wert, der eine URL, geben Sie den Speicherort enthält, in denen *Quelle* verschoben werden.  
  
 *UserName*  
 Dies ist optional. Ein **Zeichenfolge** Wert, der die Benutzer-ID, die enthält bei Bedarf den Zugriff auf gewährt *Ziel*.  
  
 *Kennwort*  
 Optional. Ein **Zeichenfolge** , enthält das Kennwort, das bei Bedarf bestätigt *Benutzername*.  
  
 *Optionen*  
 Dies ist optional. Ein [MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md) Wert, dessen Standardwert **AdMoveUnspecified**. Gibt das Verhalten dieser Methode.  
  
 *Async*  
 Optional. Ein **booleschen** -Wert, wenn **"true"**, gibt dieser Vorgang muss asynchron sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **String-Wert**. In der Regel den Wert der *Ziel* zurückgegeben wird. Der genaue zurückgegebene Wert ist jedoch vom Anbieter abhängig.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte der *Quelle* und *Ziel* müssen nicht übereinstimmen, andernfalls ein Laufzeitfehler auftritt. Mindestens die Server, Pfad und Ressource müssen unterschiedlich sein.  
  
 Für Dateien, die unter Verwendung der Internet-Publishing-Anbieter verschoben werden, aktualisiert diese Methode alle Hypertextlinks in Dateien, die verschoben werden, sofern nicht anders angegeben von *Optionen*. Diese Methode schlägt fehl, wenn *Ziel* identifiziert Sie ein vorhandenes Objekt (z. B. eine Datei oder Verzeichnis), es sei denn, **adMoveOverWrite an** angegeben ist.  
  
> [!NOTE]
>  Verwenden der **adMoveOverWrite an** option mit Umsicht. Beispielsweise wird Angabe dieser Option aus, wenn eine Datei in ein Verzeichnis zu verschieben das Verzeichnis zu löschen und Ersetzen Sie sie mit der Datei.  
  
 Bestimmte Attribute der **Datensatz** Objekt, z. B. die [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md) -Eigenschaft wird nicht aktualisiert werden, nachdem dieser Vorgang abgeschlossen ist. Aktualisieren der **Datensatz** Eigenschaften des Objekts durch Schließen der **Datensatz**, und klicken Sie dann erneut mit der URL des Speicherorts öffnen, in dem die Datei oder das Verzeichnis verschoben wurde.  
  
 Wenn diese **Datensatz** aus abgerufen wurde eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), der neue Speicherort der verschobene Datei bzw. des Verzeichnisses werden nicht wiedergegeben sofort in die **Recordset**. Aktualisieren Sie die **Recordset** durch Schließen und erneut öffnen.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Move-Methode (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext und MovePrevious-Methode (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveFirst-, MoveLast-, MoveNext- und MovePrevious-Methode (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)
