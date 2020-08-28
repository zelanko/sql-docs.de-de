---
description: ADOX-Enumerationskonstanten
title: ADOX-Enumerationskonstanten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADOX]
ms.assetid: 9d91f511-d46f-44ef-97ef-77bf93836186
author: rothja
ms.author: jroth
ms.openlocfilehash: 1def9c0445551376aec56c36c554b9c74b15c02f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985711"
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