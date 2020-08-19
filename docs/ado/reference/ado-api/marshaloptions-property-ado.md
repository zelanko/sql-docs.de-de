---
description: MarshalOptions-Eigenschaft (ADO)
title: MarshalOptions-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MarshalOptions
helpviewer_keywords:
- MarshalOptions property [ADO]
ms.assetid: 390c8abf-133e-40da-8b99-8f748a983e4f
author: rothja
ms.author: jroth
ms.openlocfilehash: 59f44093725321ef5f5b445d0edad6caec8c2113
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443322"
---
# <a name="marshaloptions-property-ado"></a>MarshalOptions-Eigenschaft (ADO)
Gibt an, welche Datensätze des [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md) zurück an den Server gemarshallt werden sollen.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [marshaloptionsenum](../../../ado/reference/ado-api/marshaloptionsenum.md) -Wert fest oder gibt diesen zurück. Der Standardwert ist " **admarshalall**".  
  
## <a name="remarks"></a>Bemerkungen  
 Bei Verwendung eines Client seitigen [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md)werden Datensätze, die auf dem Client geändert wurden, mithilfe eines Verfahrens namens Marshalling zurück auf die mittlere Ebene oder den Webserver zurückgeschrieben. dabei handelt es sich um das Verpacken und Senden von Schnittstellen Methoden Parametern über Thread-oder Prozess Grenzen hinweg. Das Festlegen der Eigenschaft " **MarshalOptions** " kann die Leistung verbessern, wenn geänderte Remote Daten für die Aktualisierung auf die mittlere Ebene oder den Webserver gemarshallt werden.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Diese Eigenschaft wird nur für ein Client seitiges **Recordset**verwendet.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die MarshalOptions-Eigenschaft (VB)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [MarshalOptions-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   
