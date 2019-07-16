---
title: Append-Methode (ADOX-Ansichten) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Views::raw_Append
- Views::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 637932fed7effb87705b3aa195578cfd506e1454
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67967151"
---
# <a name="append-method-adox-views"></a>Append-Methode (ADOX-Sichten)
Erstellt ein neues [Ansicht](../../../ado/reference/adox-api/view-object-adox.md) -Objekt und fügt es an der [Ansichten](../../../ado/reference/adox-api/views-collection-adox.md) Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Zeichenfolge** -Wert, der den Namen des zu erstellenden Ansicht angibt.  
  
 *Befehl*  
 Ein ADO [Befehl](../../../ado/reference/ado-api/command-object-ado.md) -Objekt, das die zu erstellende Sicht darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Erstellt eine neue Ansicht in der Datenquelle mit dem Namen und Attribute der **Befehl** Objekt.  
  
 Wenn der Befehlstext, den angibt, der Benutzer eine Ansicht, sondern eine Prozedur darstellt, ist das Verhalten vom Anbieter abhängig. **Fügen Sie** schlägt fehl, wenn der Anbieter keine persistenten Befehle unterstützt.  
  
> [!NOTE]
>  Bei Verwendung von OLE DB-Anbieter für Microsoft Jet, der **Ansichten** Auflistung **Anfügen** Methode ermöglicht Ihnen die Angabe einer **Prozedur** anstelle eines **anzeigen**  in die *Befehl* Parameter. Die **Prozedur** wird mit der Datenquelle hinzugefügt und wird hinzugefügt, die **Ansichten** Auflistung. Nach der **Append**, wenn die **Prozeduren** und **Ansichten** Sammlungen werden aktualisiert, die **Prozedur** werden nicht mehr in der **Ansichten** Auflistung und erscheint in der **Prozeduren** Auflistung.  
  
## <a name="applies-to"></a>Gilt für  
 [Views-Auflistung (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Ansichten Append-Methode – Beispiel (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-Methode (ADOX Indizes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-Methode (ADOX Prozeduren)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)
