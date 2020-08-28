---
description: ParentURL-Eigenschaft (ADO)
title: Eigenschaft "para URL" (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e3a8323223f97034750c7e6bf7927ac87aefd3bd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990111"
---
# <a name="parenturl-property-ado"></a>ParentURL-Eigenschaft (ADO)
Gibt eine absolute URL Zeichenfolge an, die auf den übergeordneten [Datensatz](./record-object-ado.md) des aktuellen **Daten Satz** Objekts zeigt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Zeichen** folgen Wert zurück, der die URL des übergeordneten **Datensatzes**angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaft " **parametriurl** " hängt von der Quelle ab, die zum Öffnen des **Datensatz** -Objekts verwendet wird. Der **Datensatz** kann z. b. mit einer Quelle geöffnet werden, die einen relativen Pfadnamen eines Verzeichnisses enthält, auf das von der [ActiveConnection](./activeconnection-property-ado.md) -Eigenschaft verwiesen wird.  
  
 Angenommen, "Second" ist ein Ordner, der unter "First" enthalten ist. Öffnen Sie das **Datensatz** -Objekt, indem Sie die folgende Syntax verwenden:  
  
```  
record.ActiveConnection = "https://first"  
record.Open "second"  
```  
  
 Nun lautet der Wert der `the` Eigenschaft " **Parser-URL** " identisch mit " `"https://first"` **ActiveConnection**".  
  
 Die Quelle kann auch eine absolute URL sein, z `"https://first/second"` . b.. Die Eigenschaft " **Parser-URL** " ist dann `"https://first"` die Ebene oberhalb von `"second"` .  
  
 Diese Eigenschaft ist möglicherweise ein NULL-Wert, wenn Folgendes gilt:  
  
-   Es ist kein übergeordnetes Element für das aktuelle Objekt vorhanden. beispielsweise, wenn das **Datensatz** -Objekt den Stamm eines Verzeichnisses darstellt.  
  
-   Das **Datensatz** -Objekt stellt eine Entität dar, die nicht mit einer URL angegeben werden kann.  
  
 Diese Eigenschaft ist schreibgeschützt.  
  
> [!NOTE]
>  Diese Eigenschaft wird nur von Dokument Quellen Anbietern unterstützt, wie z. b. der [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Datensätze und vom Anbieter bereitgestellte Felder](../../guide/data/records-and-provider-supplied-fields.md).  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../guide/data/absolute-and-relative-urls.md).  
  
> [!NOTE]
>  Wenn der aktuelle Datensatz einen Datensatz aus einem ADO- **Recordset**enthält, verursacht der Zugriff auf die Eigenschaft " **parametriurl** " einen Laufzeitfehler, der angibt, dass keine URL möglich ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](./record-object-ado.md)