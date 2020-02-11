---
title: onleserystatechange-Ereignis (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- onReadyStateChange event [ADO]
ms.assetid: bf2ae3ac-bfe4-4709-b50a-ea7c282c3164
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3558fc1fecd343fff480cca3b45c468860a801f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963837"
---
# <a name="onreadystatechange-event-rds"></a>onReadyStateChange-Ereignis (RDS)
Das **onleserystatechange** -Ereignis wird immer dann aufgerufen, wenn sich der Wert der Eigenschaft " [leserystate](../../../ado/reference/rds-api/readystate-property-rds.md) " ändert.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
onReadyStateChange  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaft " **leserystate** " gibt den Status eines [RDS an. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekt, das asynchron Daten in das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt abruft. Verwenden Sie das **onluystatechange** -Ereignis, um Änderungen in der Read- **State** -Eigenschaft zu überwachen, wenn Sie auftreten. Dies ist effizienter als die regelmäßige Überprüfung des Eigenschafts Werts.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../../ado/guide/data/ado-event-handler-summary.md)


