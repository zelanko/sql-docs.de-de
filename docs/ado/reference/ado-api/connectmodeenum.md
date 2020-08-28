---
description: ConnectModeEnum
title: Connectmodeerum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 704e4e78c47744fbdf2288800353fbbd33d8b090
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974711"
---
# <a name="connectmodeenum"></a>ConnectModeEnum
Gibt die verfügbaren Berechtigungen zum Ändern von Daten in einer [Verbindung](./connection-object-ado.md), zum Öffnen eines Daten [Satzes](./record-object-ado.md)oder zum Angeben von Werten für die [Mode](./mode-property-ado.md) -Eigenschaft des **Datensatz** -und des [Stream](./stream-object-ado.md) -Objekts an.  
  
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

:::row:::
    :::column:::
        [Mode-Eigenschaft (ADO)](./mode-property-ado.md)  
        [Open-Methode (ADO Record)](./open-method-ado-record.md)  
    :::column-end:::
    :::column:::
        [Open-Methode (ADO-Datenstrom)](./open-method-ado-stream.md)  
        [Stream-Objekt (ADO)](./stream-object-ado.md)  
    :::column-end:::
:::row-end:::