---
description: Append-Methode (ADOX-Prozeduren)
title: Append-Methode (ADOX-Prozeduren) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8571790b596f037bb528df375c43c98b6b77c3a5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440482"
---
# <a name="append-method-adox-procedures"></a>Append-Methode (ADOX-Prozeduren)
Fügt der [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md) Auflistung ein neues [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Zeichen** folgen Wert, der den Namen der zu erstellenden und anzufügende Prozedur angibt.  
  
 *Befehl*  
 Ein ADO- [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekt, das die zu erstellende und anzufügende Prozedur darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Erstellt eine neue Prozedur in der Datenquelle mit dem Namen und den Attributen, die im **Command** -Objekt angegeben sind.  
  
 Wenn der Befehls Text, den der Benutzer angibt, eine Ansicht anstelle einer Prozedur darstellt, hängt das Verhalten vom verwendeten Anbieter ab. Beim **Anfügen** tritt ein Fehler auf, wenn der Anbieter das Beibehalten von Befehlen nicht unterstützt.  
  
> [!NOTE]
>  Wenn Sie den OLE DB Anbieter für Microsoft Jet verwenden, können Sie mit der Prozeduren-Auflistungs **Methode "** **Prozeduren** " anstelle einer **Prozedur** im *Befehls* Parameter eine **Ansicht** angeben. Die **Sicht** wird der Datenquelle hinzugefügt und der Auflistung der **Prozeduren** hinzugefügt. Wenn die **Auflistungen** der **Prozeduren** und Sichten nach dem **Anfügen**aktualisiert werden, ist die **Ansicht** nicht mehr in der Auflistung der **Prozeduren** enthalten und wird in der Auflistung **Sichten** angezeigt.  
  
## <a name="applies-to"></a>Gilt für  
 [Procedures Collection (ADOX) (Procedures-Auflistung (ADOX))](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Prozeduren Append-Methode Beispiel (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-Methode (ADOX-Indizes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-Methode (ADOX-Ansichten)](../../../ado/reference/adox-api/append-method-adox-views.md)
