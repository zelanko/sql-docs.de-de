---
title: Append-Methode (ADOX-Indizes) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6996f3a0a3ad9f2ffa727a6cbd7b48d3fbf32777
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764061"
---
# <a name="append-method-adox-indexes"></a>Append-Methode (ADOX-Indizes)
Fügt [der](../../../ado/reference/adox-api/indexes-collection-adox.md) Index Auflistung ein neues [Index](../../../ado/reference/adox-api/index-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Sin*  
 Das anzufügende **Index** Objekt oder der Name des Indexes, der erstellt und angefügt werden soll.  
  
 *Spalten*  
 Dies ist optional. Ein **Variant** -Wert, der die Namen der zu indizierenden Spalte (n) angibt. Der *Columns* -Parameter entspricht den Werten der [Name](../../../ado/reference/adox-api/name-property-adox.md) -Eigenschaft eines [Spalten](../../../ado/reference/adox-api/column-object-adox.md) Objekts oder von Objekten.  
  
## <a name="remarks"></a>Bemerkungen  
 Der *Columns* -Parameter kann entweder den Namen einer Spalte oder ein Array mit Spaltennamen annehmen.  
  
 Wenn der Anbieter das Erstellen von Indizes nicht unterstützt, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Auflistung von Indizes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Index Append-Methode (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-Methode (ADOX-Prozeduren)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-Methode (ADOX-Ansichten)](../../../ado/reference/adox-api/append-method-adox-views.md)
