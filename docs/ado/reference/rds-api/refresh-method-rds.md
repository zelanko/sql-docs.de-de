---
title: Refresh-Methode (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
f1_keywords:
- Refresh
- RDS.DataControl::Refresh
- DataControl::Refresh
helpviewer_keywords:
- Refresh method [RDS]
ms.assetid: c90a8050-0ff4-4c83-9925-261f2f2ccfe9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9992b0f7e7281ec318f978ff487107fc832c961f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697525"
---
# <a name="refresh-method-rds"></a>Refresh-Methode (RDS)
Führt der Datenquelle angegeben, der [Connect](../../../ado/reference/rds-api/connect-property-rds.md) -Eigenschaft und die Ergebnisse der Abfrage-Updates.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.Refresh  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objektvariable, steht ein [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen festlegen, die [Connect](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md), und [SQL](../../../ado/reference/rds-api/sql-property.md) Eigenschaften vor der Verwendung der **aktualisieren** Methode. Alle von datengebundenen Steuerelementen im zugeordneten Formular ein **RDS. DataControl** Objekt spiegeln den neuen Satz von Datensätzen. Bereits vorhandene [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt veröffentlicht wird, und alle nicht gespeicherten Änderungen werden verworfen. Die **aktualisieren** Methode wird automatisch der erste Datensatz den aktuellen Datensatz.  
  
 Es ist eine gute Idee, rufen Sie die **aktualisieren** Methode in regelmäßigen Abständen beim Arbeiten mit Daten. Wenn Sie Daten abrufen, und sie dann auf einem Clientcomputer eine Weile lassen, ist es wahrscheinlich nicht mehr aktuell sind. Es ist möglich, dass alle, die von Ihnen vorgenommenen Änderungen fehl, da eine andere Person möglicherweise den Datensatz verändert, und übermittelt die Änderungen vor.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Refresh – Methodenbeispiel (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Refresh – Methodenbeispiel (VBScript)](../../../ado/reference/rds-api/refresh-method-example-vbscript.md)   
 [Behandeln von Book-Befehlsschaltflächen](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [CancelUpdate-Methode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Refresh-Methode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [SubmitChanges-Methode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


