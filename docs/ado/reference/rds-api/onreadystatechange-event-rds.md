---
title: OnReadyStateChange-Ereignis (RDS) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: e544c3f373f5e85254d40915e6b6f241a6b70379
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606030"
---
# <a name="onreadystatechange-event-rds"></a>onReadyStateChange-Ereignis (RDS)
Die **"onreadystatechange"** -Ereignis wird aufgerufen, wenn der Wert des der [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) eigenschaftenänderungen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
onReadyStateChange  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine.  
  
## <a name="remarks"></a>Hinweise  
 Die **ReadyState** Eigenschaft spiegelt wider, den Fortschritt einer [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt wie asynchron, Daten in abgerufen die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt. Verwenden der **"onreadystatechange"** Ereignis zum Überwachen von Änderungen in der **ReadyState** Eigenschaft, wenn sie auftreten. Dies ist effizienter als das Überprüfen von in regelmäßigen Abständen den Wert der Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)


