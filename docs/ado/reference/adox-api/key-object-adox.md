---
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
ms.openlocfilehash: 3b1c14c19fe624de5a6b634cd1adebe018896011
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82746648"
---
# <a name="key-object-adox"></a>Key-Objekt (ADOX)
Stellt ein primäres, fremdes oder eindeutiges Schlüsselfeld aus einer Datenbanktabelle dar.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit dem folgenden Code wird ein neuer **Schlüssel**erstellt:  
  
```  
Dim obj As New Key  
```  
  
 Mit den Eigenschaften und Auflistungen eines **Schlüssel** Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie den Schlüssel mit der [Name](../../../ado/reference/adox-api/name-property-adox.md) -Eigenschaft.  
  
-   Bestimmen Sie mit der [Type](../../../ado/reference/adox-api/type-property-key-adox.md) -Eigenschaft, ob der Schlüssel primär, fremd oder eindeutig ist.  
  
-   Greifen Sie mit der [Columns](../../../ado/reference/adox-api/columns-collection-adox.md) -Auflistung auf die Daten Bank Spalten des Schlüssels zu.  
  
-   Geben Sie den Namen der verknüpften Tabelle mit der [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md) -Eigenschaft an.  
  
-   Bestimmen Sie die Aktion, die beim Löschen oder Aktualisieren eines Primärschlüssels mit den Eigenschaften [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) und [UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md) ausgeführt wird.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Key-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Keys Collection (ADOX) (Keys-Auflistung (ADOX))](../../../ado/reference/adox-api/keys-collection-adox.md)
