---
description: RightsEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ddda86faaf032fbc981c159300ee4545643bb2e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769449"
---
# <a name="rightsenum"></a>RightsEnum
Gibt die Rechte oder Berechtigungen für eine Gruppe oder einen Benutzer für ein Objekt an.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adRightCreate**|16384 (&H4000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Erstellen neuer Objekte dieses Typs.|  
|**adRightDelete**|65536 (&H10000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Löschen von Daten aus einem Objekt. Für Objekte wie **Tabellen**verfügt der Benutzer über die Berechtigung zum Löschen von Datenwerten aus Datensätzen.|  
|**adRightDrop**|256 (&H100)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Entfernen von Objekten aus dem Katalog. **Tabellen** können z. b. durch einen SQL-Befehl DROP TABLE gelöscht werden.|  
|**adRightExclusive**|512 (&H200)|Der Benutzer oder die Gruppe verfügt ausschließlich über die Berechtigung, auf das Objekt zuzugreifen.|  
|**adRightExecute**|536870912 (&H20000000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Ausführen des Objekts.|  
|**adRightFull**|268435456 (&H10000000)|Der Benutzer oder die Gruppe verfügt über alle Berechtigungen für das Objekt.|  
|**adRightInsert**|32768 (&H8000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Einfügen des Objekts. Für Objekte wie **Tabellen**verfügt der Benutzer über die Berechtigung zum Einfügen von Daten in die Tabelle.|  
|**adRightMaximumAllowed**|33554432 (&H2000000)|Der Benutzer oder die Gruppe verfügt über die maximal zulässige Anzahl von Berechtigungen für den Anbieter. Bestimmte Berechtigungen sind vom Anbieter abhängig.|  
|**adRightNone**|0|Der Benutzer oder die Gruppe verfügt über keine Berechtigungen für das Objekt.|  
|**adRightRead**|-2147483648 (&H80000000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Lesen des Objekts. Für Objekte, wie z. b. [Tabellen](./table-object-adox.md), verfügt der Benutzer über die Berechtigung zum Lesen der Daten in der Tabelle.|  
|**adRightReadDesign**|1024 (&H400)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Lesen des Entwurfs für das Objekt.|  
|**adRightReadPermissions**|131072 (&H20000)|Der Benutzer oder die Gruppe kann die spezifischen Berechtigungen für ein Objekt im Katalog anzeigen, aber nicht ändern.|  
|**adRightReference**|8192 (&H2000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung, auf das Objekt zu verweisen.|  
|**adRightUpdate**|1073741824 (&H40000000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Aktualisieren des Objekts. Für Objekte, wie z. b. **Tabellen**, verfügt der Benutzer über die Berechtigung zum Aktualisieren der Daten in der Tabelle.|  
|**adRightWithGrant**|4096 (&H1000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung, Berechtigungen für das Objekt zu erteilen.|  
|**adRightWriteDesign**|2048 (&H800)|Der Benutzer oder die Gruppe verfügt über die Berechtigung zum Ändern des Entwurfs für das Objekt.|  
|**adRightWriteOwner**|524288 (&H80000)|Der Benutzer oder die Gruppe verfügt über die Berechtigung, den Besitzer des Objekts zu ändern.|  
|**adRightWritePermissions**|262144 (&H40000)|Der Benutzer oder die Gruppe kann die spezifischen Berechtigungen für ein Objekt im Katalog ändern.|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [GetPermissions-Methode (ADOX)](./getpermissions-method-adox.md)  
    :::column-end:::
    :::column:::
        [SetPermissions-Methode (ADOX)](./setpermissions-method-adox.md)  
    :::column-end:::
:::row-end:::