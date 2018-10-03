---
title: ConnectModeEnum | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 2a5ab00cc6e01b97639ae3f7d353fa2462ef3fd0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637858"
---
# <a name="connectmodeenum"></a>ConnectModeEnum
Gibt an, die verfügbaren Berechtigungen zum Ändern von Daten in eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md), öffnen ein [Datensatz](../../../ado/reference/ado-api/record-object-ado.md), oder Werte für die [Modus](../../../ado/reference/ado-api/mode-property-ado.md) Eigenschaft der  **Datensatz** und [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekte.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adModeRead**|1|Gibt schreibgeschützten Zugriff an.|  
|**adModeReadWrite**|3|Gibt an, Lese-/Schreibberechtigungen verfügen.|  
|**adModeRecursive**|0x400000|Zusammen mit den anderen *\*ShareDeny\** Werte (**AdModeShareDenyNone**, **AdModeShareDenyWrite**, oder **AdModeShareDenyRead**) freigabebeschränkungen für alle untergeordneten Datensätze des aktuellen weitergeben **Datensatz**. Es hat keine Auswirkungen, wenn die **Datensatz** verfügt nicht über alle untergeordneten Elemente. Ein Laufzeitfehler wird generiert, wenn es sich bei Verwendung mit **AdModeShareDenyNone** nur. Es kann jedoch verwendet werden, mit **AdModeShareDenyNone** in Kombination mit anderen Werten. Beispielsweise können Sie "**AdModeRead** oder **AdModeShareDenyNone** oder **AdModeRecursive**".|  
|**adModeShareDenyNone**|16|Können andere Benutzer zum Öffnen einer Verbindung mit Berechtigungen. Weder Lese-noch Schreibezugriff kann anderen Benutzern verweigert werden.|  
|**adModeShareDenyRead**|4|Verhindert, dass andere Benutzer eine Verbindung mit der Berechtigung zum Lesen öffnen.|  
|**adModeShareDenyWrite**|8|Verhindert, dass andere Benutzer eine Verbindung mit Berechtigungen zum Schreiben öffnen.|  
|**adModeShareExclusive**|12|Hindert andere Benutzer eine Verbindung zu öffnen.|  
|**adModeUnknown**|0|Standard. Gibt an, dass die Berechtigungen noch nicht festgelegt wurde, oder können nicht bestimmt werden.|  
|**adModeWrite**|2|Gibt an, nur-schreiben-Berechtigungen.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.ConnectMode.READ|  
|AdoEnums.ConnectMode.READWRITE|  
|(Es gibt keine Entsprechung der AdoEnums.ConnectMode.RECURSIVE)|  
|AdoEnums.ConnectMode.SHAREDENYNONE|  
|AdoEnums.ConnectMode.SHAREDENYREAD|  
|AdoEnums.ConnectMode.SHAREDENYWRITE|  
|AdoEnums.ConnectMode.SHAREEXCLUSIVE|  
|AdoEnums.ConnectMode.UNKNOWN|  
|AdoEnums.ConnectMode.WRITE|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Mode-Eigenschaft (ADO)](../../../ado/reference/ado-api/mode-property-ado.md)|[Open-Methode (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Open-Methode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)|[Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|
