---
description: Append-Methode (ADOX-Schlüssel)
title: Append-Methode (ADOX-Schlüssel) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Keys::Append
- Keys::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 215a5391-f422-42ec-99ea-4e6fbb5d3d64
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ae3ef035594b696b829f0f1898e1749a2c33f11
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440532"
---
# <a name="append-method-adox-keys"></a>Append-Methode (ADOX-Schlüssel)
Fügt der [Keys](../../../ado/reference/adox-api/keys-collection-adox.md) -Auflistung ein neues [Schlüssel](../../../ado/reference/adox-api/key-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Schlüssel*  
 Das anzufügende **Schlüssel** Objekt oder der Name des Schlüssels, der erstellt und angefügt werden soll.  
  
 *KeyType*  
 Optional. Ein **Long** -Wert, der den Typ des Schlüssels angibt. Der *Key* -Parameter entspricht der [Type](../../../ado/reference/adox-api/type-property-key-adox.md) -Eigenschaft eines **Key** -Objekts.  
  
 *Spalte*  
 Optional. Ein **Zeichen** folgen Wert, der den Namen der zu indizierenden Spalte angibt. Der *Columns* -Parameter entspricht dem Wert der [Name](../../../ado/reference/adox-api/name-property-adox.md) -Eigenschaft eines [Column](../../../ado/reference/adox-api/column-object-adox.md) -Objekts.  
  
 *RelatedTable*  
 Optional. Ein **Zeichen** folgen Wert, der den Namen der verknüpften Tabelle angibt. Der *RelatedTable* -Parameter entspricht dem Wert der **Name** -Eigenschaft eines [Table](../../../ado/reference/adox-api/table-object-adox.md) -Objekts.  
  
 *RelatedColumn*  
 Optional. Ein **Zeichen** folgen Wert, der den Namen der verknüpften Spalte für einen Fremdschlüssel angibt. Der *RelatedColumn* -Parameter entspricht dem Wert der **Name** -Eigenschaft eines [Column](../../../ado/reference/adox-api/column-object-adox.md) -Objekts.  
  
## <a name="remarks"></a>Bemerkungen  
 Der *Columns* -Parameter kann entweder den Namen einer Spalte oder ein Array mit Spaltennamen annehmen.  
  
## <a name="applies-to"></a>Gilt für  
 [Keys Collection (ADOX) (Keys-Auflistung (ADOX))](../../../ado/reference/adox-api/keys-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-Methode (ADOX-Indizes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Prozeduren)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-Methode (ADOX-Ansichten)](../../../ado/reference/adox-api/append-method-adox-views.md)
