---
title: CopyRecord-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_CopyRecord
- _Record::CopyRecord
helpviewer_keywords:
- CopyRecord method [ADO]
ms.assetid: b9bcf272-3c74-479f-95dd-0229a32e98fc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d70dcba3d373b195950f90b6ef82c3d670844bb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63309204"
---
# <a name="copyrecord-method-ado"></a>CopyRecord-Methode (ADO)
Kopiert eine Entität, dargestellt durch eine [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) an einen anderen Speicherort.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Record.CopyRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Optional. Ein **Zeichenfolge** -Wert, der eine URL, die Entität, die kopiert werden (z. B. eine Datei oder Verzeichnis) enthält. Wenn *Quelle* ausgelassen wird, oder gibt eine leere Zeichenfolge, die Datei oder das Verzeichnis, die vom aktuellen [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) kopiert werden.  
  
 *Ziel*  
 Optional. Ein **Zeichenfolge** -Wert, der eine URL, geben Sie den Speicherort enthält, in denen *Quelle* kopiert werden.  
  
 *UserName*  
 Dies ist optional. Ein **Zeichenfolge** Wert, der die Benutzer-ID, die enthält bei Bedarf den Zugriff auf gewährt *Ziel*.  
  
 *Kennwort*  
 Optional. Ein **Zeichenfolge** Wert, der das Kennwort, die enthält bei Bedarf überprüft *Benutzername*.  
  
 *Optionen*  
 Dies ist optional. Ein [CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md) Wert mit Standardwert **AdCopyUnspecified**. Gibt das Verhalten dieser Methode.  
  
 *Async*  
 Dies ist optional. Ein **booleschen** -Wert, wenn **"true"**, gibt an, dass dieser Vorgang asynchron sein sollte.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Zeichenfolge** -Wert, der in der Regel den Wert zurückgibt *Ziel*. Der genaue zurückgegebene Wert ist jedoch vom Anbieter abhängig.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte der *Quelle* und *Ziel* müssen nicht übereinstimmen, andernfalls ein Laufzeitfehler auftritt. Mindestens eine der Namen der Server, Pfad oder Ressourcen muss sich unterscheiden.  
  
 Alle untergeordneten Elemente (z. B. Unterverzeichnissen) des *Quelle* rekursiv kopiert werden, es sei denn, **AdCopyNonRecursive** angegeben ist. In einem rekursiven Vorgang *Ziel* muss sich nicht auf einem Unterverzeichnis des *Quelle*ist, andernfalls der Vorgang wird nicht abgeschlossen.  
  
 Diese Methode schlägt fehl, wenn *Ziel* identifiziert eine vorhandene Entität (z. B. eine Datei oder ein Verzeichnis), es sei denn, **AdCopyOverWrite** angegeben ist.  
  
> [!IMPORTANT]
>  Verwenden der **AdCopyOverWrite** option mit Umsicht. Beispielsweise wird diese Option angeben, wenn eine Datei in ein Verzeichnis kopiert *löschen* das Verzeichnis, und Ersetzen Sie sie mit der Datei.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
