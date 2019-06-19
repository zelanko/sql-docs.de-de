---
title: catalog.execution_property_override_values | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 83cbdd6f-ddde-47bf-abde-36bd24272621
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 922d55e335c8310cec3cf4db8967cadc2affd1f3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65714871"
---
# <a name="catalogexecutionpropertyoverridevalues"></a>catalog.execution_property_override_values 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt die Eigenschaftenüberschreibungswerte an, die während der Ausführung des Pakets festgelegt wurden.  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|property_id|**bigint**|Eindeutige ID für den Eigenschaftenüberschreibungswert.|  
|execution_id|**bigint**|Eindeutige ID für die Instanz der Ausführung.|  
|property_path|**nvarchar(4000)**|Der Pfad zur Eigenschaft im Paket.|  
|property_value|**nvarchar(max)**|Der Überschreibungswert der Eigenschaft.|  
|sensitive|**bit**|Wenn der Wert 1 lautet, ist die Eigenschaft vertraulich und wird beim Speichern verschlüsselt. Lautet der Wert 0, ist die Eigenschaft nicht vertraulich, und der Wert wird als Nur-Text gespeichert.|  
  
## <a name="remarks"></a>Remarks  
 In dieser Sicht wird eine Zeile zu jeder Ausführung angezeigt, in der Eigenschaftswerte mit dem Abschnitt **Eigenschaftenüberschreibungen** auf der Registerkarte **Erweitert** des Dialogfelds **Paket ausführen** überschrieben wurden. Der Pfad zur Eigenschaft wird von der Eigenschaft **Paketpfad** des Pakettasks abgeleitet.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für die Instanz der Ausführung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
