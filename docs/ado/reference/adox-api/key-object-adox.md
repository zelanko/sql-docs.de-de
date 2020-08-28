---
description: Key-Objekt (ADOX)
title: Key-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: d8b2f37dd12f7243f2c5fcb8e577dc35e350c6a9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984051"
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