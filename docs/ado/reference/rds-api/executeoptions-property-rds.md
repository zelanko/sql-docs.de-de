---
description: ExecuteOptions-Eigenschaft (RDS)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 042a69dd679cf84e2ab26da77cda3c06d2abd94e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88768309"
---
# <a name="executeoptions-property-rds"></a>ExecuteOptions-Eigenschaft (RDS)
Gibt an, ob die asynchrone Ausführung aktiviert ist.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen der folgenden Werte fest oder gibt ihn zurück.  
  
|Konstante|Beschreibung|  
|--------------|-----------------|  
|**adcExecSync**|Führt die nächste Aktualisierung des [Recordsets](../ado-api/recordset-object-ado.md) synchron aus.|  
|**adcExecAsync**|Standard. Führt die nächste Aktualisierung des **Recordsets** asynchron aus.|  
  
> [!NOTE]
>  Jede ausführbare Datei, die diese Konstanten verwendet, muss Deklarationen für Sie bereitstellen. Sie können die gewünschten Konstanten Deklarationen aus der Datei "adcvsb. Inc" Ausschneiden und einfügen, die sich im Standard Installationsordner für die RDS-Bibliothek befindet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn **ExecuteOptions** auf **adcexecasync**festgelegt ist, führt dies asynchron den nächsten **Aktualisierungs** Aufrufvorgang für das [RDS aus. ](./datacontrol-object-rds.md) **Recordset**des DataControl-Objekts.  
  
 Wenn Sie versuchen, [Reset](./reset-method-rds.md), [Refresh](./refresh-method-rds.md), [SubmitChanges](./submitchanges-method-rds.md), [CancelUpdate](../ado-api/cancelupdate-method-ado.md)oder [Recordset](./recordset-sourcerecordset-properties-rds.md) aufzurufen, während ein anderer asynchroner Vorgang das RDS ändern könnte [. ](./datacontrol-object-rds.md) Das **Recordset** des DataControl-Objekts wird ausgeführt, es tritt ein Fehler auf.  
  
 Wenn während eines asynchronen Vorgangs ein Fehler auftritt, ist das **RDS. ** Der Read- [State](./readystate-property-rds.md) -Wert des DataControl-Objekts ändert sich von **adkreadystateloaded** in **adkreadystatecomplete**, und der Wert der **Recordset** - *Eigenschaft bleibt unverändert*.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eigenschaften von "ExecuteOptions" und "FetchOptions" (VBScript)](./executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Cancel-Methode (RDS)](./cancel-method-rds.md)