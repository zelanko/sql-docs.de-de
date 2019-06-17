---
title: ParentURL-Eigenschaft (ADO) | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: 65704cea2a396e0f03de4bbcdc9f031f4c9af583
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703468"
---
# <a name="parenturl-property-ado"></a>ParentURL-Eigenschaft (ADO)
Gibt eine absolute URL-Zeichenfolge, die auf das übergeordnete Element verweist [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) des aktuellen **Datensatz** Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Zeichenfolge** Wert, der die URL des übergeordneten Elements angibt **Datensatz**.  
  
## <a name="remarks"></a>Hinweise  
 Die **ParentURL** Eigenschaft hängt von der Quelle zum Öffnen der **Datensatz** Objekt. Z. B. die **Datensatz** geöffnet werden kann, mit der Quelle, der Name eines relativen Pfads, der ein Verzeichnis verweist enthält die [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) Eigenschaft.  
  
 Angenommen, "second" ein Ordner unter "First" enthalten ist. Öffnen der **Datensatz** Objekt mithilfe der folgenden Syntax:  
  
```  
record.ActiveConnection = "https://first"  
record.Open "second"  
```  
  
 Nun den Wert der `the` **ParentURL** Eigenschaft `"https://first"`, die identisch mit **ActiveConnection**.  
  
 Die Quelle kann auch eine absolute URL sein wie `"https://first/second"`. Die **ParentURL** Eigenschaft ist dann `"https://first"`, der darüber liegenden Ebene `"second"`.  
  
 Diese Eigenschaft kann ein null-Wert sein, wenn:  
  
-   Es ist kein übergeordnetes Element für das aktuelle Objekt. z. B. wenn die **Datensatz** Objekt stellt den Stamm eines Verzeichnisses dar.  
  
-   Die **Datensatz** Objekt eine Entität darstellt, die nicht mit einer URL angegeben werden kann.  
  
 Diese Eigenschaft ist schreibgeschützt.  
  
> [!NOTE]
>  Diese Eigenschaft wird nur unterstützt Dokument-Source-Anbietern, z. B. die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Datensätze und Felder der vom Anbieter bereitgestellte](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
> [!NOTE]
>  Wenn der aktuelle Datensatz einen Datensatz aus einer ADO enthält **Recordset**, den Zugriff auf die **ParentURL** -Eigenschaft bewirkt, dass ein Laufzeitfehler, gibt an, dass keine URL möglich ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
