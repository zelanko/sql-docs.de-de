---
description: Append-Methode (ADOX-Prozeduren)
title: Append-Methode (ADOX-Prozeduren) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 2bc35ccb48211f6a849dc102ba2d1806a79b2426
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985461"
---
# <a name="append-method-adox-procedures"></a>Append-Methode (ADOX-Prozeduren)
Fügt der [Prozeduren](./procedures-collection-adox.md) Auflistung ein neues [Prozedur](./procedure-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Zeichen** folgen Wert, der den Namen der zu erstellenden und anzufügende Prozedur angibt.  
  
 *Befehl*  
 Ein ADO- [Befehls](../ado-api/command-object-ado.md) Objekt, das die zu erstellende und anzufügende Prozedur darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Erstellt eine neue Prozedur in der Datenquelle mit dem Namen und den Attributen, die im **Command** -Objekt angegeben sind.  
  
 Wenn der Befehls Text, den der Benutzer angibt, eine Ansicht anstelle einer Prozedur darstellt, hängt das Verhalten vom verwendeten Anbieter ab. Beim **Anfügen** tritt ein Fehler auf, wenn der Anbieter das Beibehalten von Befehlen nicht unterstützt.  
  
> [!NOTE]
>  Wenn Sie den OLE DB Anbieter für Microsoft Jet verwenden, können Sie mit der Prozeduren-Auflistungs **Methode "** **Prozeduren** " anstelle einer **Prozedur** im *Befehls* Parameter eine **Ansicht** angeben. Die **Sicht** wird der Datenquelle hinzugefügt und der Auflistung der **Prozeduren** hinzugefügt. Wenn die **Auflistungen** der **Prozeduren** und Sichten nach dem **Anfügen**aktualisiert werden, ist die **Ansicht** nicht mehr in der Auflistung der **Prozeduren** enthalten und wird in der Auflistung **Sichten** angezeigt.  
  
## <a name="applies-to"></a>Gilt für  
 [Procedures-Collection (ADOX)](./procedures-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Prozeduren Append-Methode Beispiel (VB)](./procedures-append-method-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](./append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](./append-method-adox-groups.md)   
 [Append-Methode (ADOX-Indizes)](./append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](./append-method-adox-keys.md)   
 [Append-Methode (ADOX-Tabellen)](./append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](./append-method-adox-users.md)   
 [Append-Methode (ADOX-Sichten)](./append-method-adox-views.md)