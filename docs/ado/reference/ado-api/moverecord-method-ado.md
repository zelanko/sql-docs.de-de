---
title: "\"Muecord\"-Methode (ADO) | Microsoft-Dokumentation"
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e5c63bbd29bef1d7b0b7d7650c32fcfe2245f7a
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762431"
---
# <a name="moverecord-method-ado"></a>MoveRecord-Methode (ADO)
Verschiebt die durch einen [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) dargestellte Entität an einen anderen Speicherort.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Record.MoveRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Dies ist optional. Ein **Zeichen** folgen Wert, der eine URL enthält, die den zu verschoden **Datensatz** identifiziert. Wenn die *Quelle* weggelassen wird oder eine leere Zeichenfolge angibt, wird das durch diesen **Datensatz** dargestellte Objekt verschoben. Wenn der **Datensatz** z. b. eine Datei darstellt, wird der Inhalt der Datei an den Speicherort verschoben, der vom *Ziel*angegeben wird.  
  
 *Ziel*  
 Dies ist optional. Ein **Zeichen** folgen Wert, der eine URL enthält, die den Speicherort angibt, an den die *Quelle* verschoben wird.  
  
 *User*  
 Dies ist optional. Ein **Zeichen** folgen Wert, der die Benutzer-ID enthält, die bei Bedarf den Zugriff auf das *Ziel*autorisiert.  
  
 *Kennwort*  
 Dies ist optional. Eine **Zeichenfolge** , die das Kennwort enthält, das bei Bedarf den *Benutzernamen*überprüft.  
  
 *Optionen*  
 Dies ist optional. Ein Wert vom Typ "", dessen [Standardwert "](../../../ado/reference/ado-api/moverecordoptionsenum.md) **admuveunspezifiziert**" ist. Gibt das Verhalten dieser Methode an.  
  
 *Async*  
 Dies ist optional. Ein **boolescher** Wert, der angibt, dass dieser Vorgang bei " **true**" asynchron erfolgen soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Zeichen** folgen Wert. In der Regel wird der Wert des *Ziels* zurückgegeben. Der genaue zurückgegebene Wert ist jedoch vom Anbieter abhängig.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Werte von *Quelle* und *Ziel* dürfen nicht identisch sein. Andernfalls tritt ein Laufzeitfehler auf. Mindestens der Server-, der Pfad-und der Ressourcen Name müssen unterschiedlich sein.  
  
 Bei Dateien, die mithilfe des Internet Publishing Anbieters verschoben werden, aktualisiert diese Methode alle Hypertext Links in Dateien, die verschoben werden, sofern nicht anders durch *Optionen*angegeben. Diese Methode schlägt fehl, wenn das *Ziel* ein vorhandenes Objekt (z. b. eine Datei oder ein Verzeichnis) identifiziert, es sei denn, **admuveüberschreibung** ist angegeben  
  
> [!NOTE]
>  Verwenden Sie die Option **admuveüberschreibung** mit Bedacht. Wenn Sie diese Option z. b. beim Verschieben einer Datei in ein Verzeichnis angeben, wird das Verzeichnis gelöscht und durch die Datei ersetzt.  
  
 Bestimmte Attribute des **Datensatz** -Objekts, z. b. die Eigenschaft " [parametriurl](../../../ado/reference/ado-api/parenturl-property-ado.md) ", werden nach Abschluss dieses Vorgangs nicht aktualisiert. Aktualisieren Sie die Eigenschaften des **Daten Satz** Objekts, indem Sie den **Datensatz**schließen, und öffnen Sie ihn dann erneut mit der URL des Speicher Orts, an den die Datei oder das Verzeichnis verschoben wurde.  
  
 Wenn dieser **Datensatz** von einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)abgerufen wurde, wird der neue Speicherort der verschostellten Datei oder des verschobenes Verzeichnisses nicht sofort in das **Recordset**reflektiert. Aktualisieren Sie das **Recordset** , indem Sie es schließen und erneut öffnen.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Move-Methode (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [Muvefirst-, muvelast-, muvenext-und muveprevious-Methode (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveFirst-, MoveLast-, MoveNext- und MovePrevious-Methode (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)
