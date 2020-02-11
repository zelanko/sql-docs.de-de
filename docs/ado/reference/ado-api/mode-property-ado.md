---
title: Mode-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Mode
- _Stream::Mode
- _Record::Mode
helpviewer_keywords:
- Mode property [ADO]
ms.assetid: 808661eb-0d7c-4e6d-8e40-9dc3bef3d77a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc5b2e2bce410309656bad5591a3df90781cc8bc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932229"
---
# <a name="mode-property-ado"></a>Mode-Eigenschaft (ADO)
Gibt die verfügbaren Berechtigungen zum Ändern von Daten in einem [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md)-, [Datensatz](../../../ado/reference/ado-api/record-object-ado.md)-oder [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [connectmodeenum](../../../ado/reference/ado-api/connectmodeenum.md) -Wert fest oder gibt ihn zurück. Der Standardwert für eine **Verbindung** ist **adModeUnknown**. Der Standardwert für ein **Datensatz** -Objekt ist **admoderead**. Der Standardwert für einen **Stream** , der einer zugrunde liegenden Quelle (geöffnet mit einer URL als Quelle oder als Standarddaten **Strom** eines **Datensatzes**) zugeordnet ist, ist **admoderead**. Der Standardwert für einen Daten **Strom** , der keiner zugrunde liegenden Quelle (instanziiert im Arbeitsspeicher) zugeordnet ist, ist **adModeUnknown**.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Mode** -Eigenschaft, um die Zugriffsberechtigungen festzulegen oder zurückzugeben, die vom Anbieter für die aktuelle Verbindung verwendet werden. Die **Mode** -Eigenschaft kann nur festgelegt werden, wenn das **Verbindungs** Objekt geschlossen wird.  
  
 Bei einem **Streamobjekt** , wenn der Zugriffsmodus nicht angegeben ist, wird es von der Quelle geerbt, die zum Öffnen des Daten **Strom** Objekts verwendet wird. Wenn beispielsweise ein **Stream** von einem **Datensatz** -Objekt aus geöffnet wird, wird er standardmäßig im gleichen Modus wie der **Datensatz**geöffnet.  
  
 Diese Eigenschaft ist Lese-/Schreibzugriff, wenn das Objekt geschlossen und schreibgeschützt ist, während das-Objekt geöffnet ist.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Wenn die **Mode** -Eigenschaft für ein Client seitiges **Verbindungs** Objekt verwendet wird, kann Sie nur auf **adModeUnknown**festgelegt werden.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [IsolationLevel-und Mode-Eigenschaften (Beispiel) (VB)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel-und Mode-Eigenschaften (Beispiel) (VC + +)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
