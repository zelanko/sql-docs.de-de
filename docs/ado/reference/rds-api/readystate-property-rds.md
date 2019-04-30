---
title: ReadyState-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ReadyState property [ADO]
ms.assetid: 5be75bc7-1171-4440-a37e-c8cc6b5cd865
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c575683b5ec23c6739a37eae177be004efea0a57
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63255731"
---
# <a name="readystate-property-rds"></a>ReadyState-Eigenschaft (RDS)
Gibt den Status einer [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt, wie Daten in abgerufen seine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen der folgenden Werte zurück.  
  
|Wert|Description|  
|-----------|-----------------|  
|**adcReadyStateLoaded**|Die aktuelle Abfrage weiterhin ausgeführt wird, und haben keine Zeilen abgerufen wurden. Die **DataControl** des Objekts **Recordset** ist nicht für die Verwendung verfügbar.|  
|**adcReadyStateInteractive**|Ein anfänglichen Satz von Zeilen, die von der aktuellen Abfrage abgerufen wurden gespeichert der **DataControl** des Objekts **Recordset** und für die Verwendung verfügbar sind. Die übrigen Zeilen werden weiterhin abgerufen wird.|  
|**adcReadyStateComplete**|Alle Zeilen, die von der aktuellen Abfrage abgerufenen im gespeichert wurden die **DataControl** des Objekts **Recordset** und für die Verwendung verfügbar sind.<br /><br /> Dieser Status wird auch vorhanden sein, wenn eine Operation aufgrund eines Fehlers abgebrochen, oder wenn die **Recordset** Objekt ist nicht initialisiert.|  
  
> [!NOTE]
>  Jede clientseitige ausführbare Datei, die diese Konstanten verwendet muss die Deklarationen für sie bereitstellen. Sie können die Ausschneiden und Einfügen von Konstanten Deklarationen, die aus der Datei Adcvbs.inc, in den standardmäßigen Installationsordner für die RDS-Bibliothek gespeichert werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der ["onreadystatechange"](../../../ado/reference/rds-api/onreadystatechange-event-rds.md) Ereignis zum Überwachen von Änderungen in der **ReadyState** -Eigenschaft während eines asynchronen Abfragevorgangs. Dies ist effizienter als der Wert der Eigenschaft in regelmäßigen Abständen geprüft wird.  
  
 Bei einem während eines asynchronen Vorgangs Fehler, der **ReadyState** eigenschaftsänderungen **AdcReadyStateComplete**, [Zustand](../../../ado/reference/ado-api/state-property-ado.md) Eigenschaft ändert sich von **AdStateExecuting** zu **AdStateClosed**, und die **Recordset** Objekt [Wert](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft bleibt *"Nothing"* .  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ReadyState-Eigenschaft – Beispiel (VBScript)](../../../ado/reference/rds-api/readystate-property-example-vbscript.md)   
 [Cancel-Methode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [ExecuteOptions-Eigenschaft (RDS)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


