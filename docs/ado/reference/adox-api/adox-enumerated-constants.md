---
description: ADOX-Enumerationskonstanten
title: ADOX-Enumerationskonstanten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADOX]
ms.assetid: 9d91f511-d46f-44ef-97ef-77bf93836186
author: rothja
ms.author: jroth
ms.openlocfilehash: 553924a51845c7ac49bfb76bab27f75c7d4e4742
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771609"
---
# <a name="adox-enumerated-constants"></a>ADOX-Enumerationskonstanten
Zur Unterstützung des Debuggens listet die ADOX-Enumerationskonstanten einen Wert für jede Konstante auf. Dieser Wert ist jedoch rein beratend und kann sich von einem Release von ADOX zu einem anderen ändern. Der Code sollte nur vom Namen und nicht vom tatsächlichen Wert von enumerierten Konstanten abhängen.  
  
 Die folgenden Enumerationskonstanten sind definiert.  
  
|Enumeration|Beschreibung|  
|-----------------|-----------------|  
|[ActionEnum](./actionenum.md)|Gibt den Typ der Aktion an, die ausgeführt werden soll, wenn **setberechtigungen** aufgerufen wird.|  
|[AllowNullsEnum](./allownullsenum.md)|Gibt an, ob Datensätze mit NULL-Werten indiziert werden.|  
|[ColumnAttributesEnum](./columnattributesenum.md)|Gibt die Eigenschaften einer **Spalte**an.|  
|[DataTypeEnum](../ado-api/datatypeenum.md)|Gibt den Datentyp eines **Felds**, eines **Parameters**oder einer **Eigenschaft**an.|  
|[InheritTypeEnum](./inherittypeenum.md)|Gibt an, wie Objekte Berechtigungen erben, die mit **setberechtigungen**festgelegt sind.|  
|[KeyTypeEnum](./keytypeenum.md)|Gibt den Typ des **Schlüssels**an: primär, fremd oder eindeutig.|  
|[ObjectTypeEnum](./objecttypeenum.md)|Gibt den Typ des Datenbankobjekts an, für das Berechtigungen oder den Besitz festgelegt werden sollen.|  
|[RightsEnum](./rightsenum.md)|Gibt die Rechte oder Berechtigungen für eine Gruppe oder einen Benutzer für ein Objekt an.|  
|[RuleEnum](./ruleenum.md)|Gibt die Regel an, die befolgt werden soll, wenn eine **Taste** gelöscht wird.|  
|[SortOrderEnum](./sortorderenum.md)|Gibt die Sortierreihenfolge für eine indizierte Spalte an.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADOX-API-Referenz](./adox-object-model.md?view=sql-server-ver15)   
 [ADO-Erweiterungen für Datendefinitionssprache und Sicherheit (ADOX)](../../guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)