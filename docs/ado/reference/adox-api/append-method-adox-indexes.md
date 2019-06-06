---
title: Append-Methode (ADOX Indizes) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Indexes::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6695769f-275b-4b70-81bd-1a5f7d74926c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7190fa68b8204e6b1cfea68a6571e07fd78a9bbc
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718956"
---
# <a name="append-method-adox-indexes"></a>Append-Methode (ADOX-Indizes)
Fügt ein neues [Index](../../../ado/reference/adox-api/index-object-adox.md) -Objekt an die [Indizes](../../../ado/reference/adox-api/indexes-collection-adox.md) Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
 Die **Index** anzufügende Objekt oder den Namen des Indexes zum Erstellen und anfügen.  
  
 *Spalten*  
 Optional. Ein **Variant** Wert, der die Namen der zu indizierenden Spalten angibt. Die *Spalten* Parameter entspricht den Werten der der [Namen](../../../ado/reference/adox-api/name-property-adox.md) Eigenschaft eine [Spalte](../../../ado/reference/adox-api/column-object-adox.md) Objekte.  
  
## <a name="remarks"></a>Hinweise  
 Die *Spalten* Parameter kann entweder der Name einer Spalte oder ein Array von Spaltennamen haben.  
  
 Wenn der Anbieter das Erstellen von Indizes nicht unterstützt wird, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Auflistung von Indizes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Indizes Append-Methode – Beispiel (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-Methode (ADOX Prozeduren)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-Methode (ADOX-Ansichten)](../../../ado/reference/adox-api/append-method-adox-views.md)
