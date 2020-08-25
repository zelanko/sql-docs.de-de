---
description: Append-Methode (ADOX-Indizes)
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
ms.openlocfilehash: 28e396e85dc68a3d622a173dad440c5dff68dea1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771459"
---
# <a name="append-method-adox-indexes"></a>Append-Methode (ADOX-Indizes)
Fügt [der](./indexes-collection-adox.md) Index Auflistung ein neues [Index](./index-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Index*  
 Das anzufügende **Index** Objekt oder der Name des Indexes, der erstellt und angefügt werden soll.  
  
 *Spalten*  
 Optional. Ein **Variant** -Wert, der die Namen der zu indizierenden Spalte (n) angibt. Der *Columns* -Parameter entspricht den Werten der [Name](./name-property-adox.md) -Eigenschaft eines [Spalten](./column-object-adox.md) Objekts oder von Objekten.  
  
## <a name="remarks"></a>Bemerkungen  
 Der *Columns* -Parameter kann entweder den Namen einer Spalte oder ein Array mit Spaltennamen annehmen.  
  
 Wenn der Anbieter das Erstellen von Indizes nicht unterstützt, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Indexes-Collection (ADOX)](./indexes-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Index Append-Methode (VB)](./indexes-append-method-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](./append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](./append-method-adox-groups.md)   
 [Append-Methode (ADOX-Schlüssel)](./append-method-adox-keys.md)   
 [Append-Methode (ADOX-Prozeduren)](./append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](./append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](./append-method-adox-users.md)   
 [Append-Methode (ADOX-Sichten)](./append-method-adox-views.md)