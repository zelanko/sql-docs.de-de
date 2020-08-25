---
description: Key-Objekt (ADOX)
title: Key-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
author: rothja
ms.author: jroth
ms.openlocfilehash: 619cd72854a4e779fbea8989fa84ef6fdf27f90a
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770109"
---
# <a name="key-object-adox"></a>Key-Objekt (ADOX)
Stellt ein primäres, fremdes oder eindeutiges Schlüsselfeld aus einer Datenbanktabelle dar.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit dem folgenden Code wird ein neuer **Schlüssel**erstellt:  
  
```  
Dim obj As New Key  
```  
  
 Mit den Eigenschaften und Auflistungen eines **Schlüssel** Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie den Schlüssel mit der [Name](./name-property-adox.md) -Eigenschaft.  
  
-   Bestimmen Sie mit der [Type](./type-property-key-adox.md) -Eigenschaft, ob der Schlüssel primär, fremd oder eindeutig ist.  
  
-   Greifen Sie mit der [Columns](./columns-collection-adox.md) -Auflistung auf die Daten Bank Spalten des Schlüssels zu.  
  
-   Geben Sie den Namen der verknüpften Tabelle mit der [RelatedTable](./relatedtable-property-adox.md) -Eigenschaft an.  
  
-   Bestimmen Sie die Aktion, die beim Löschen oder Aktualisieren eines Primärschlüssels mit den Eigenschaften [DeleteRule](./deleterule-property-adox.md) und [UpdateRule](./updaterule-property-adox.md) ausgeführt wird.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Key-Objekt – Eigenschaften, Methoden und Ereignisse](./key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Columns-Auflistung (ADOX)](./columns-collection-adox.md)   
 [Keys-Collection (ADOX)](./keys-collection-adox.md)