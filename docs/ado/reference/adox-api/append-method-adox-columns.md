---
description: Append-Methode (ADOX-Spalten)
title: Append-Methode (ADOX-Spalten) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Columns::raw_Append
- Columns::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c959f6d822724ee6e7480cf00941aaa1fc8012a
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985501"
---
# <a name="append-method-adox-columns"></a>Append-Methode (ADOX-Spalten)
Fügt der [Columns](./columns-collection-adox.md) -Auflistung ein neues [Spalten](./column-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Spalte*  
 Das anzufügende **Spalten** Objekt oder der Name der Spalte, die erstellt und angefügt werden soll.  
  
 *Type*  
 Optional. Ein **Long** -Wert, der den Datentyp der Spalte angibt. Der *Typparameter* entspricht der [Type](./type-property-column-adox.md) -Eigenschaft eines **Column** -Objekts.  
  
 *DefinedSize*  
 Optional. Ein **Long** -Wert, der die Größe der Spalte angibt. Der *DefinedSize* -Parameter entspricht der [DefinedSize](./definedsize-property-adox.md) -Eigenschaft eines **Column** -Objekts.  
  
> [!NOTE]
>  Wenn eine **Spalte** an die **Columns** -Auflistung eines [Indexes](./index-object-adox.md) angefügt wird, tritt ein Fehler auf, wenn die **Spalte** nicht in einer [Tabelle](./table-object-adox.md) vorhanden ist, die bereits an die [Tabellen](./tables-collection-adox.md) Auflistung angehängt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Columns-Collection (ADOX)](./columns-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Methoden und Tabellen Append-Methoden, Name Property example (VB)](./columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Beispiel für eine Beispiel Katalog Eigenschaft (VB)](./parentcatalog-property-example-vb.md)   
 [Append-Methode (ADOX-Gruppen)](./append-method-adox-groups.md)   
 [Append-Methode (ADOX-Indizes)](./append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](./append-method-adox-keys.md)   
 [Append-Methode (ADOX-Prozeduren)](./append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](./append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](./append-method-adox-users.md)   
 [Append-Methode (ADOX-Sichten)](./append-method-adox-views.md)