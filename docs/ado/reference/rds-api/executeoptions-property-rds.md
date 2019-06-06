---
title: ExecuteOptions-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ExecuteOptions property [ADO], VBScript example
ms.assetid: 62a4fd88-afc3-4f1f-b978-40710a30c4e9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 084faa615253c58d7b41214f9abfb4d3c8880bac
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66712604"
---
# <a name="executeoptions-property-rds"></a>ExecuteOptions-Eigenschaft (RDS)
Gibt an, ob die asynchrone Ausführung aktiviert ist.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen der folgenden Werte zurück.  
  
|Konstante|Description|  
|--------------|-----------------|  
|**adcExecSync**|Führt die nächste Aktualisierung von der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) synchron.|  
|**adcExecAsync**|Standard. Führt die nächste Aktualisierung von der **Recordset** asynchron.|  
  
> [!NOTE]
>  Jede ausführbare Datei, die diese Konstanten verwendet muss die Deklarationen für sie bereitstellen. Sie können die Ausschneiden und Einfügen von Konstanten Deklarationen, die aus der Datei Adcvbs.inc, in den standardmäßigen Installationsordner für die RDS-Bibliothek gespeichert werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn **ExecuteOptions** nastaven NA hodnotu **AdcExecAsync**, und dies asynchron die nächste führt **aktualisieren** rufen Sie für die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) des Objekts **Recordset**.  
  
 Wenn Sie versuchen, Sie rufen [zurücksetzen](../../../ado/reference/rds-api/reset-method-rds.md), [aktualisieren](../../../ado/reference/rds-api/refresh-method-rds.md), [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md), oder [Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) ein anderer asynchronen Vorgang, die sich ändern kann zwar die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) des Objekts **Recordset** ausgeführt wird, wird ein Fehler auftritt.  
  
 Wenn ein Fehler, während eines asynchronen Vorgangs auftritt, der **RDS. DataControl** des Objekts [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) Wert ändert sich von **AdcReadyStateLoaded** zu **AdcReadyStateComplete**, und die  **Recordset** Eigenschaftswert bleibt *nichts*.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ExecuteOptions und FetchOptions Eigenschaften – Beispiel (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Cancel-Methode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)


