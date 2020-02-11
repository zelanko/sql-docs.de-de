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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: debf6f9dc4ac1326caf9fbf32b65f15f34a19094
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933456"
---
# <a name="connectmodeenum"></a>ConnectModeEnum
Gibt die verfügbaren Berechtigungen zum Ändern von Daten in einer [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md), zum Öffnen eines Daten [Satzes](../../../ado/reference/ado-api/record-object-ado.md)oder zum Angeben von Werten für die [Mode](../../../ado/reference/ado-api/mode-property-ado.md) -Eigenschaft des **Datensatz** -und des [Stream](../../../ado/reference/ado-api/stream-object-ado.md) -Objekts an.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**admoderead**|1|Gibt schreibgeschützte Berechtigungen an.|  
|**admodereadwrite**|3|Gibt Lese-/Schreibberechtigungen an.|  
|**admoderecursive**|0x400000|Wird in Verbindung mit den anderen * \*sharedeny\* * -Werten (**adModeShareDenyNone**, **admodesharedenywrite**oder **admodesharedenyread**) zum Weitergeben von Freigabe Beschränkungen an alle untergeordneten Datensätze des aktuellen **Datensatzes**verwendet. Dies hat keine Auswirkungen, wenn der **Datensatz** keine untergeordneten Elemente aufweist. Ein Laufzeitfehler wird generiert, wenn nur mit **adModeShareDenyNone** verwendet wird. Sie kann jedoch mit **adModeShareDenyNone** verwendet werden, wenn Sie mit anderen Werten kombiniert werden. Sie können z. b. "**admoderead** oder **adModeShareDenyNone** oder **admoderecursive**" verwenden.|  
|**adModeShareDenyNone**|16|Ermöglicht anderen Benutzern das Öffnen einer Verbindung mit beliebigen Berechtigungen. Weder Lese-noch Schreibezugriff kann anderen Benutzern verweigert werden.|  
|**admodesharedenyread**|4|Verhindert, dass andere eine Verbindung mit Leseberechtigungen öffnen.|  
|**admodesharedenywrite**|8|Verhindert, dass andere eine Verbindung mit Schreibberechtigungen öffnen.|  
|**admodeshareexclusive**|12|Hindert andere daran, eine Verbindung zu öffnen.|  
|**adModeUnknown**|0|Default. Gibt an, dass die Berechtigungen noch nicht festgelegt wurden oder nicht bestimmt werden können.|  
|**admodewrite**|2|Gibt schreibgeschützte Berechtigungen an.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Dauerhaft|  
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
