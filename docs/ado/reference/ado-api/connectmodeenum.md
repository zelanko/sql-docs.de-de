---
title: Connectmodeerum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectModeEnum
helpviewer_keywords:
- ConnectModeEnum enumeration [ADO]
ms.assetid: 3792c294-5161-4538-a908-22a5fc50b85f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e78ab5988d88447539da7c492f0b02943693844
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762611"
---
# <a name="connectmodeenum"></a>ConnectModeEnum
Gibt die verfügbaren Berechtigungen zum Ändern von Daten in einer [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md), zum Öffnen eines Daten [Satzes](../../../ado/reference/ado-api/record-object-ado.md)oder zum Angeben von Werten für die [Mode](../../../ado/reference/ado-api/mode-property-ado.md) -Eigenschaft des **Datensatz** -und des [Stream](../../../ado/reference/ado-api/stream-object-ado.md) -Objekts an.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**admoderead**|1|Gibt schreibgeschützte Berechtigungen an.|  
|**admodereadwrite**|3|Gibt Lese-/Schreibberechtigungen an.|  
|**admoderecursive**|0x400000|Wird in Verbindung mit den anderen * \* sharedeny \* * -Werten (**adModeShareDenyNone**, **admodesharedenywrite**oder **admodesharedenyread**) zum Weitergeben von Freigabe Beschränkungen an alle untergeordneten Datensätze des aktuellen **Datensatzes**verwendet. Dies hat keine Auswirkungen, wenn der **Datensatz** keine untergeordneten Elemente aufweist. Ein Laufzeitfehler wird generiert, wenn nur mit **adModeShareDenyNone** verwendet wird. Sie kann jedoch mit **adModeShareDenyNone** verwendet werden, wenn Sie mit anderen Werten kombiniert werden. Sie können z. b. "**admoderead** oder **adModeShareDenyNone** oder **admoderecursive**" verwenden.|  
|**adModeShareDenyNone**|16|Ermöglicht anderen Benutzern das Öffnen einer Verbindung mit beliebigen Berechtigungen. Weder Lese-noch Schreibezugriff kann anderen Benutzern verweigert werden.|  
|**admodesharedenyread**|4|Verhindert, dass andere eine Verbindung mit Leseberechtigungen öffnen.|  
|**admodesharedenywrite**|8|Verhindert, dass andere eine Verbindung mit Schreibberechtigungen öffnen.|  
|**admodeshareexclusive**|12|Hindert andere daran, eine Verbindung zu öffnen.|  
|**adModeUnknown**|0|Standard. Gibt an, dass die Berechtigungen noch nicht festgelegt wurden oder nicht bestimmt werden können.|  
|**admodewrite**|2|Gibt schreibgeschützte Berechtigungen an.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|AdoEnums. ConnectMode. Read|  
|AdoEnums. ConnectMode. ReadWrite|  
|(Es gibt keine Entsprechung von AdoEnums. ConnectMode. Recursive)|  
|AdoEnums. ConnectMode. sharedenynone|  
|AdoEnums. ConnectMode. sharedenyread|  
|AdoEnums. ConnectMode. sharedenywrite|  
|AdoEnums. ConnectMode. shareexclusive|  
|AdoEnums. ConnectMode. Unknown|  
|AdoEnums. ConnectMode. Write|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Mode-Eigenschaft (ADO)](../../../ado/reference/ado-api/mode-property-ado.md)|[Open-Methode (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Open-Methode (ADO-Datenstrom)](../../../ado/reference/ado-api/open-method-ado-stream.md)|[Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|
