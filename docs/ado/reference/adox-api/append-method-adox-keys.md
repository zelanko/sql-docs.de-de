---
description: Append-Methode (ADOX-Schlüssel)
title: Append-Methode (ADOX-Schlüssel) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 2531031808c16db4892fb0b759a8a8d819a2222d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985481"
---
# <a name="append-method-adox-keys"></a>Append-Methode (ADOX-Schlüssel)
Fügt der [Keys](./keys-collection-adox.md) -Auflistung ein neues [Schlüssel](./key-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Schlüssel*  
 Das anzufügende **Schlüssel** Objekt oder der Name des Schlüssels, der erstellt und angefügt werden soll.  
  
 *KeyType*  
 Optional. Ein **Long** -Wert, der den Typ des Schlüssels angibt. Der *Key* -Parameter entspricht der [Type](./type-property-key-adox.md) -Eigenschaft eines **Key** -Objekts.  
  
 *Spalte*  
 Optional. Ein **Zeichen** folgen Wert, der den Namen der zu indizierenden Spalte angibt. Der *Columns* -Parameter entspricht dem Wert der [Name](./name-property-adox.md) -Eigenschaft eines [Column](./column-object-adox.md) -Objekts.  
  
 *RelatedTable*  
 Optional. Ein **Zeichen** folgen Wert, der den Namen der verknüpften Tabelle angibt. Der *RelatedTable* -Parameter entspricht dem Wert der **Name** -Eigenschaft eines [Table](./table-object-adox.md) -Objekts.  
  
 *RelatedColumn*  
 Optional. Ein **Zeichen** folgen Wert, der den Namen der verknüpften Spalte für einen Fremdschlüssel angibt. Der *RelatedColumn* -Parameter entspricht dem Wert der **Name** -Eigenschaft eines [Column](./column-object-adox.md) -Objekts.  
  
## <a name="remarks"></a>Bemerkungen  
 Der *Columns* -Parameter kann entweder den Namen einer Spalte oder ein Array mit Spaltennamen annehmen.  
  
## <a name="applies-to"></a>Gilt für  
 [Keys-Collection (ADOX)](./keys-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](./append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](./append-method-adox-groups.md)   
 [Append-Methode (ADOX-Indizes)](./append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Prozeduren)](./append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](./append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](./append-method-adox-users.md)   
 [Append-Methode (ADOX-Sichten)](./append-method-adox-views.md)