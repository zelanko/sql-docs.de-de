---
title: Append-Methode (ADOX Prozeduren) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedures::Append
- Procedures::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dd64ba8119db1ecf2d2b621cd202c9f700b53475
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67967284"
---
# <a name="append-method-adox-procedures"></a>Append-Methode (ADOX-Prozeduren)
Fügt ein neues [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md) -Objekt an die [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md) Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Zeichenfolge** Wert, der angibt, der Name der Prozedur zum Erstellen und anfügen.  
  
 *Befehl*  
 Ein ADO [Befehl](../../../ado/reference/ado-api/command-object-ado.md) -Objekt, das Verfahren zum Erstellen und Anfügen darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Erstellt eine neue Prozedur in der Datenquelle mit dem Namen und Attribute der **Befehl** Objekt.  
  
 Wenn der Befehlstext, den angibt, der Benutzer einer Sicht statt einer Prozedur darstellt, ist das Verhalten der verwendete Anbieter abhängig. **Fügen Sie** schlägt fehl, wenn der Anbieter keine persistenten Befehle unterstützt.  
  
> [!NOTE]
>  Bei Verwendung von OLE DB-Anbieter für Microsoft Jet, der **Prozeduren** Auflistung **Anfügen** Methode ermöglicht Ihnen die Angabe einer **Ansicht** anstelle eines  **Prozedur** in die *Befehl* Parameter. Die **Ansicht** wird mit der Datenquelle hinzugefügt und wird hinzugefügt, die **Prozeduren** Auflistung. Nach der **Append**, wenn die **Prozeduren** und **Ansichten** Sammlungen werden aktualisiert, die **Ansicht** werden nicht mehr in der **Prozeduren** Auflistung und erscheint in der **Ansichten** Auflistung.  
  
## <a name="applies-to"></a>Gilt für  
 [Procedures Collection (ADOX) (Procedures-Auflistung (ADOX))](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Prozeduren Append-Methode – Beispiel (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-Methode (ADOX Indizes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-Methode (ADOX-Ansichten)](../../../ado/reference/adox-api/append-method-adox-views.md)
