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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ad38c81101d983f70130bd0df5526ccba785f57
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71296555"
---
# <a name="catalogexecution_property_override_values"></a>catalog.execution_property_override_values 

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
  
  
