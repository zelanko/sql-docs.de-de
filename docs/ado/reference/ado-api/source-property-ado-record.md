---
title: Source-Eigenschaft (ADO Record) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::Source
- _Record::PutRefSource
- _Record::GetSource
- _Record::put_Source
- _Record::putref_Source
- _Record::get_Source
helpviewer_keywords:
- Source property [ADO Record]
ms.assetid: 2c18279e-6f35-4af0-b12e-8f1543d9ed20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b053fdeae5016d7a1b489133b3a26067da7eab2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740400"
---
# <a name="source-property-ado-record"></a>Source-Eigenschaft (ADO-Datensatz)
Gibt an, die Datenquelle oder das Objekt dargestellt wird, durch die [Datensatz](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt eine **Variant** hodnota ukazuje, die Entität, dargestellt durch die **Datensatz**.  
  
## <a name="remarks"></a>Hinweise  
 Die **Quelle** -Eigenschaft gibt die *Quelle* Argument der **Datensatz** Objekt [öffnen](../../../ado/reference/ado-api/open-method-ado-record.md) Methode. Sie können eine absolute oder relative URL-Zeichenfolge enthalten. Eine absolute URL ohne Einstellung verwendet werden kann die [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) Eigenschaft direkt öffnen die **Datensatz** Objekt. Ein impliziter **Verbindung** Objekt wird in diesem Fall erstellt.  
  
 Die **Quelle** Eigenschaft kann auch einen Verweis auf ein bereits geöffnetes enthalten **Recordset**, daraufhin eine **Datensatz** Objekt, das in die aktuelle Zeile darstellt. die  **Recordset**.  
  
 Die **Quelle** Eigenschaft kann auch enthalten einen Verweis auf eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt, das eine einzelne Zeile mit Daten vom Anbieter zurückgegeben.  
  
 Wenn die **ActiveConnection** Eigenschaft auch festgelegt ist, und klicken Sie dann die **Quelle** -Eigenschaft muss auf ein Objekt, das innerhalb des Bereichs dieser Verbindung vorhanden ist, verweisen. Z. B. in einem strukturierten Namespaces Wenn die **Quelle** Eigenschaft eine absolute URL enthält, muss es zeigen Sie auf einen Knoten, der innerhalb des Bereichs des Knotens identifiziert werden, indem Sie die URL in der Verbindungszeichenfolge vorhanden ist. Wenn die **Quelle** Eigenschaft enthält eine relative URL, und klicken Sie dann im Kontext festlegen, indem überprüft wird die **ActiveConnection** Eigenschaft.  
  
 Die **Quelle** -Eigenschaft ist Lese-/Schreibzugriff, während die **Datensatz** -Objekt geschlossen ist, und ist schreibgeschützt, während die **Datensatz** -Objekts geöffnet ist.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Source-Eigenschaft (ADO-Fehler)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Source-Eigenschaft (ADO Recordset)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
