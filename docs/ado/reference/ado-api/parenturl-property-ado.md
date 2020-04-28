---
title: Eigenschaft "para URL" (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::ParentURL
helpviewer_keywords:
- ParentURL property [ADO]
ms.assetid: 65120ce6-3900-4cd4-b322-3b9816d74737
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 54b2db44fe2e1971356f96d33aa8de0b02781b1e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931641"
---
# <a name="parenturl-property-ado"></a>ParentURL-Eigenschaft (ADO)
Gibt eine absolute URL Zeichenfolge an, die auf den übergeordneten [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) des aktuellen **Daten Satz** Objekts zeigt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Zeichen** folgen Wert zurück, der die URL des übergeordneten **Datensatzes**angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaft " **parametriurl** " hängt von der Quelle ab, die zum Öffnen des **Datensatz** -Objekts verwendet wird. Der **Datensatz** kann z. b. mit einer Quelle geöffnet werden, die einen relativen Pfadnamen eines Verzeichnisses enthält, auf das von der [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) -Eigenschaft verwiesen wird.  
  
 Angenommen, "Second" ist ein Ordner, der unter "First" enthalten ist. Öffnen Sie das **Datensatz** -Objekt, indem Sie die folgende Syntax verwenden:  
  
```  
record.ActiveConnection = "https://first"  
record.Open "second"  
```  
  
 Nun lautet `"https://first"`der Wert der `the` Eigenschaft "Parser- **URL** " identisch mit " **ActiveConnection**".  
  
 Die Quelle kann auch eine absolute URL sein, `"https://first/second"`z. b.. Die Eigenschaft " **Parser-URL** " `"https://first"`ist dann die Ebene `"second"`oberhalb von.  
  
 Diese Eigenschaft ist möglicherweise ein NULL-Wert, wenn Folgendes gilt:  
  
-   Es ist kein übergeordnetes Element für das aktuelle Objekt vorhanden. beispielsweise, wenn das **Datensatz** -Objekt den Stamm eines Verzeichnisses darstellt.  
  
-   Das **Datensatz** -Objekt stellt eine Entität dar, die nicht mit einer URL angegeben werden kann.  
  
 Diese Eigenschaft ist schreibgeschützt.  
  
> [!NOTE]
>  Diese Eigenschaft wird nur von Dokument Quellen Anbietern unterstützt, wie z. b. der [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Datensätze und vom Anbieter bereitgestellte Felder](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
> [!NOTE]
>  Wenn der aktuelle Datensatz einen Datensatz aus einem ADO- **Recordset**enthält, verursacht der Zugriff auf die Eigenschaft " **parametriurl** " einen Laufzeitfehler, der angibt, dass keine URL möglich ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
