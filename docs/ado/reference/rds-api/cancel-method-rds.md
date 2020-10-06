---
description: Cancel-Methode (RDS)
title: Cancel-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Cancel method [RDS]
ms.assetid: 560b5b3d-fba9-4275-8920-9c3e186134f7
author: rothja
ms.author: jroth
ms.openlocfilehash: 24f72c16e1c27d070bcc52fc29c6599cc11c737e
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722691"
---
# <a name="cancel-method-rds"></a>Cancel-Methode (RDS)
Bricht die Ausführung eines ausstehenden asynchronen Methoden Aufrufes ab.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RDS.DataControl.Cancel  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie **Abbrechen**aufrufen, wird "read [ystate](./readystate-property-rds.md) " automatisch auf " **adkreadystateloaded**" festgelegt, und das [Recordset](../ado-api/recordset-object-ado.md) ist leer.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cancel-Methode (Beispiel) (VBScript)](./cancel-method-example-vbscript.md)   
 [Cancel-Methode (ADO)](../ado-api/cancel-method-ado.md)   
 [CancelBatch-Methode (ADO)](../ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate-Methode (ADO)](../ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate-Methode (RDS)](./cancelupdate-method-rds.md)   
 [ExecuteOptions-Eigenschaft (RDS)](./executeoptions-property-rds.md)