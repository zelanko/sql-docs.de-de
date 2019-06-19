---
title: RightsEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RightsEnum
helpviewer_keywords:
- RightsEnum enumeration [ADOX]
ms.assetid: 55ee67c7-a583-42aa-849a-78264b4cb614
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a34cbd8ee3d274d3b3d45049611ca9cc99fa7758
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718836"
---
# <a name="rightsenum"></a>RightsEnum
Gibt die Rechte oder Berechtigungen für eine Gruppe oder Benutzer für ein Objekt an.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adRightCreate**|16384 (&H4000)|Der Benutzer oder Gruppe verfügt über die Berechtigung zum Erstellen neuer Objekte dieses Typs.|  
|**adRightDelete**|65536 (&H10000)|Der Benutzer oder Gruppe verfügt über die Berechtigung zum Löschen von Daten aus einem Objekt. Für Objekte wie z. B. **Tabellen**, der Benutzer hat die Berechtigung zum Löschen von Datenwerte aus Datensätzen.|  
|**adRightDrop**|256 (&H100)|Der Benutzer oder Gruppe verfügt über die Berechtigung zum Entfernen von Objekten aus dem Katalog. Z. B. **Tabellen** kann von einem DROP TABLE SQL-Befehl gelöscht werden.|  
|**adRightExclusive**|512 (&H200)|Der Benutzer oder Gruppe verfügt über die Berechtigung zum Zugriff auf das Objekt ausschließlich.|  
|**adRightExecute**|536870912 (&H20000000)|Der Benutzer oder Gruppe verfügt über die Berechtigung zum Ausführen des Objekts.|  
|**adRightFull**|268435456 (&H10000000)|Der Benutzer oder Gruppe verfügt über alle Berechtigungen für das Objekt.|  
|**adRightInsert**|32768 (&H8000)|Benutzer oder Gruppe verfügt über die Berechtigung für das Objekt eingefügt werden soll. Für Objekte wie z. B. **Tabellen**, der Benutzer verfügt über die Berechtigung zum Einfügen von Daten in die Tabelle.|  
|**adRightMaximumAllowed**|33554432 (&H2000000)|Der Benutzer oder die Gruppe hat die maximale Anzahl von Berechtigungen, die vom Anbieter zulässig. Berechtigungen werden vom Anbieter abhängig.|  
|**adRightNone**|0|Der Benutzer oder Gruppe verfügt über keine Berechtigungen für das Objekt aus.|  
|**adRightRead**|-2147483648 (&H80000000)|Der Benutzer oder Gruppe verfügt über die Berechtigung zum Lesen des Objekts. Für Objekte wie z. B. [Tabellen](../../../ado/reference/adox-api/table-object-adox.md), der Benutzer verfügt über die Berechtigung zum Lesen der Daten in der Tabelle.|  
|**adRightReadDesign**|1024 (&H400)|Der Benutzer oder Gruppe verfügt über die Berechtigung zum Lesen des Entwurfs für das Objekt aus.|  
|**adRightReadPermissions**|131072 (&H20000)|Der Benutzer oder die Gruppe kann anzeigen, aber nicht ändern, die bestimmten Berechtigungen für ein Objekt im Katalog.|  
|**adRightReference**|8192 (&H2000)|Benutzer oder Gruppe verfügt über die Berechtigung für das Objekt zu verweisen.|  
|**adRightUpdate**|1073741824 (&H40000000)|Der Benutzer oder Gruppe verfügt über die Berechtigung zum Aktualisieren des Objekts. Für Objekte wie z. B. **Tabellen**, der Benutzer verfügt über die Berechtigung zum Aktualisieren der Daten in der Tabelle.|  
|**adRightWithGrant**|4096 (&H1000)|Benutzer oder Gruppe verfügt über die Berechtigung zum Gewähren von Berechtigungen für das Objekt.|  
|**adRightWriteDesign**|2048 (&H800)|Der Benutzer oder Gruppe verfügt über die Berechtigung zum Ändern des Designs für das Objekt.|  
|**adRightWriteOwner**|524288 (&H80000)|Der Benutzer oder Gruppe verfügt über die Berechtigung zum Ändern des Besitzers des Objekts.|  
|**adRightWritePermissions**|262144 (&H40000)|Der Benutzer oder Gruppe kann die spezifischen Berechtigungen für ein Objekt im Katalog ändern.|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[GetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|[SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
