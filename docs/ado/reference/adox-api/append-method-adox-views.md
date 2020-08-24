---
description: Append-Methode (ADOX-Sichten)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 74432aa3bb610b1cd5688e1f52c7d7ea81166f75
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771359"
---
# <a name="append-method-adox-views"></a>Append-Methode (ADOX-Sichten)
Erstellt ein neues [Ansichts](./view-object-adox.md) Objekt und fügt es an die [views](./views-collection-adox.md) -Auflistung an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Zeichen** folgen Wert, der den Namen der zu erstellenden Ansicht angibt.  
  
 *Befehl*  
 Ein ADO- [Befehls](../ado-api/command-object-ado.md) Objekt, das die zu erstellende Sicht darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Erstellt eine neue Sicht in der Datenquelle mit dem Namen und den Attributen, die im **Command** -Objekt angegeben sind.  
  
 Wenn der Befehls Text, den der Benutzer angibt, eine Prozedur anstelle einer Ansicht darstellt, hängt das Verhalten vom Anbieter ab. Beim **Anfügen** tritt ein Fehler auf, wenn der Anbieter das Beibehalten von Befehlen nicht unterstützt.  
  
> [!NOTE]
>  Wenn **Sie den OLE DB** Anbieter für Microsoft Jet verwenden, können Sie mit der **Ansichts** Sammlungs- **Append** -Methode anstelle einer Ansicht im *Befehls* Parameter eine **Prozedur** angeben. Die **Prozedur** wird der Datenquelle hinzugefügt und der Auflistung **views** hinzugefügt. Wenn nach dem Anfüge **Vorgang** die Auflistungen für **Prozeduren** und **Sichten** aktualisiert **werden, ist**die Prozedur nicht mehr in der Sammlung **views** enthalten und wird in der Auflistung der **Prozeduren** angezeigt.  
  
## <a name="applies-to"></a>Gilt für  
 [Views-Collection (ADOX)](./views-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiele für die Append-Methode (VB)](./views-append-method-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](./append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](./append-method-adox-groups.md)   
 [Append-Methode (ADOX-Indizes)](./append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](./append-method-adox-keys.md)   
 [Append-Methode (ADOX-Prozeduren)](./append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](./append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](./append-method-adox-users.md)