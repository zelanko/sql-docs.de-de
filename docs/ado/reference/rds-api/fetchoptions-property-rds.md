---
title: FetchOptions-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FetchOptions property [ADO]
ms.assetid: 7b2e254a-9354-4541-bc98-bb185276388f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4e4e0943a675ef7cf3684ccddd2699fba02dac9e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67964124"
---
# <a name="fetchoptions-property-rds"></a>FetchOptions-Eigenschaft (RDS)
Gibt den Typ des asynchronen abrufen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="setting-and-return-values"></a>Festlegen und Rückgabewerte  
 Legt fest oder gibt einen der folgenden Werte zurück.  
  
|Konstante|Beschreibung|  
|--------------|-----------------|  
|**adcFetchUpFront**|Werden alle Datensätze der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) abgerufen werden, bevor die Steuerung an die Anwendung zurückgegeben wird. Die vollständige **Recordset** wird abgerufen, bevor die Anwendung darf nichts damit zu tun.|  
|**adcFetchBackground**|Steuerelement kann an die Anwendung zurückgegeben, sobald der erste Batch an Datensätzen abgerufen wurde. Ein späterer lesen, der die **Recordset** Zugriffsversuche auf einen Datensatz nicht in den ersten Batch abgerufen werden verzögert, bis der gesuchte Datensatz tatsächlich abgerufen wurde, zu diesem Zeitpunkt die Steuerung an die Anwendung zurückgegeben.|  
|**adcFetchAsync**|Standard. Die Kontrolle sofort wieder an die Anwendung während der Datensätze im Hintergrund abgerufen werden. Wenn die Anwendung versucht, einen Datensatz zu lesen, die noch nicht abgerufen wurde, der den gesuchten Datensatz am nächsten Datensatz werden gelesen, und Kontrolle wird sofort zurückgegeben werden, gibt an, dass das aktuelle Ende der **Recordset** wurde erreicht. Z. B. einen Aufruf von [MoveLast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) wechselt die Position des aktuelle Datensatzes in den letzten Datensatz tatsächlich abgerufen, obwohl mehrere Datensätze für zum Auffüllen weiterhin der **Recordset**.|  
  
> [!NOTE]
>  Jede clientseitige ausführbare Datei, die diese Konstanten verwendet muss die Deklarationen für sie bereitstellen. Sie können die Ausschneiden und Einfügen von Konstanten Deklarationen, die aus der Datei Adcvbs.inc, in den standardmäßigen Installationsordner für die RDS-Bibliothek gespeichert werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 In einer Web-Anwendung, Sie werden in der Regel verwenden möchten **AdcFetchAsync** (der Standardwert), da es sich um eine bessere Leistung bietet. In einer kompilierten Clientanwendung, Sie werden in der Regel verwenden möchten **AdcFetchBackground**.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ExecuteOptions und FetchOptions Eigenschaften – Beispiel (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Cancel-Methode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)


