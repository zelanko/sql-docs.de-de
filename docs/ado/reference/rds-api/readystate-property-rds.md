---
description: ReadyState-Eigenschaft (RDS)
title: Eigenschaft "leserystate" (RDS) | Microsoft-Dokumentation
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: cdc3f2109d1938d7388454dcd1054deba341ed44
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724331"
---
# <a name="readystate-property-rds"></a>ReadyState-Eigenschaft (RDS)
Gibt den Fortschritt eines [DataControl](./datacontrol-object-rds.md) -Objekts beim Abrufen von Daten in das [Recordset](../ado-api/recordset-object-ado.md) -Objekt an.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen der folgenden Werte fest oder gibt ihn zurück.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**adcReadyStateLoaded**|Die aktuelle Abfrage wird noch ausgeführt, und es wurden keine Zeilen abgerufen. Das **Recordset** des **DataControl** -Objekts ist nicht für die Verwendung verfügbar.|  
|**adcReadyStateInteractive**|Ein anfänglicher Satz von Zeilen, der von der aktuellen Abfrage abgerufen wurde, wurde im **Recordset** des **DataControl** -Objekts gespeichert und steht für die Verwendung zur Verfügung. Die verbleibenden Zeilen werden noch abgerufen.|  
|**adcReadyStateComplete**|Alle von der aktuellen Abfrage abgerufenen Zeilen wurden im **Recordset** des **DataControl** -Objekts gespeichert und stehen zur Verwendung zur Verfügung.<br /><br /> Dieser Status ist auch vorhanden, wenn ein Vorgang aufgrund eines Fehlers abgebrochen wurde oder wenn das **Recordset** -Objekt nicht initialisiert ist.|  
  
> [!NOTE]
>  Jede Client seitige ausführbare Datei, die diese Konstanten verwendet, muss Deklarationen für Sie bereitstellen. Sie können die gewünschten Konstanten Deklarationen aus der Datei "adcvsb. Inc" Ausschneiden und einfügen, die sich im Standard Installationsordner für die RDS-Bibliothek befindet.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie das [onluystatechange](./onreadystatechange-event-rds.md) -Ereignis, um Änderungen in der Eigenschaft " **leserystate** " während eines asynchronen Abfrage Vorgangs zu überwachen. Dies ist effizienter als die regelmäßige Überprüfung des Werts der-Eigenschaft.  
  
 Wenn während eines asynchronen Vorgangs ein Fehler auftritt, wird die Eigenschaft "read- **State** " in " **adkreadystatecomplete**" geändert, die [Zustands](../ado-api/state-property-ado.md) Eigenschaft wird von " **adstatecomplete** " in " **adstateclosed**" geändert, und die Eigenschaft " **Recordset** -Objekt [Wert](../ado-api/value-property-ado.md) *" bleibt unverändert*.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 ["Read ystate"-Eigenschaft (Beispiel) (VBScript)](./readystate-property-example-vbscript.md)   
 [Cancel-Methode (RDS)](./cancel-method-rds.md)   
 [ExecuteOptions-Eigenschaft (RDS)](./executeoptions-property-rds.md)