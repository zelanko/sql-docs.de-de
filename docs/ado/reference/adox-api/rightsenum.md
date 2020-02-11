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
ms.openlocfilehash: f6db3d1fecd8a2670a81fb239cb1a100389be21a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965273"
---
# <a name="rightsenum"></a>RightsEnum
Gibt die Rechte oder Berechtigungen für eine Gruppe oder einen Benutzer für ein Objekt an.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adrightcreate**|16384 (&H4000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Erstellen neuer Objekte dieses Typs.|  
|**adrightdelete**|65536 (&H10000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Löschen von Daten aus einem Objekt. Für Objekte wie **Tabellen**verfügt der Benutzer über die Berechtigung zum Löschen von Datenwerten aus Datensätzen.|  
|**adrightdrop**|256 (&H100)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Entfernen von Objekten aus dem Katalog. **Tabellen** können z. b. durch einen SQL-Befehl DROP TABLE gelöscht werden.|  
|**adrightexclusive**|512 (&H200)|Der Benutzer oder die Gruppe verfügt ausschließlich über die Berechtigung, auf das Objekt zuzugreifen.|  
|**adrightexecute**|536870912 (&H20000000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Ausführen des Objekts.|  
|**adrightfull**|268435456 (&H10000000)|Der Benutzer oder die Gruppe verfügt über alle Berechtigungen für das Objekt.|  
|**adRightInsert**|32768 (&H8000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Einfügen des Objekts. Für Objekte wie **Tabellen**verfügt der Benutzer über die Berechtigung zum Einfügen von Daten in die Tabelle.|  
|**adrightmaximumallowed**|33554432 (&H2000000)|Der Benutzer oder die Gruppe verfügt über die maximal zulässige Anzahl von Berechtigungen für den Anbieter. Bestimmte Berechtigungen sind vom Anbieter abhängig.|  
|**adrightnone**|0|Der Benutzer oder die Gruppe verfügt über keine Berechtigungen für das Objekt.|  
|**adRightRead**|-2147483648 (&H80000000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Lesen des Objekts. Für Objekte, wie z. b. [Tabellen](../../../ado/reference/adox-api/table-object-adox.md), verfügt der Benutzer über die Berechtigung zum Lesen der Daten in der Tabelle.|  
|**adrightreaddesign**|1024 (&H400)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Lesen des Entwurfs für das Objekt.|  
|**adrightreadberechtigungs-**|131072 (&H20000)|Der Benutzer oder die Gruppe kann die spezifischen Berechtigungen für ein Objekt im Katalog anzeigen, aber nicht ändern.|  
|**adrightreferenzierung**|8192 (&H2000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung, auf das Objekt zu verweisen.|  
|**adRightUpdate**|1073741824 (&H40000000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Aktualisieren des Objekts. Für Objekte, wie z. b. **Tabellen**, verfügt der Benutzer über die Berechtigung zum Aktualisieren der Daten in der Tabelle.|  
|**adrightwithgrant**|4096 (&H1000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung, Berechtigungen für das Objekt zu erteilen.|  
|**adrightschreitedesign**|2048 (&H800)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Ändern des Entwurfs für das Objekt.|  
|**adrightschreiteowner**|524288 (&H80000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung, den Besitzer des Objekts zu ändern.|  
|**adrightschreiteberechtigungen**|262144 (&H40000)|Der Benutzer oder die Gruppe kann die spezifischen Berechtigungen für ein Objekt im Katalog ändern.|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[GetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|[SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
