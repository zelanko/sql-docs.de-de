---
description: FetchOptions-Eigenschaft (RDS)
title: FetchOptions-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FetchOptions property [ADO]
ms.assetid: 7b2e254a-9354-4541-bc98-bb185276388f
author: rothja
ms.author: jroth
ms.openlocfilehash: cee86b2d579a02d9e6cbcc06bfa5d95714f1ecd9
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722311"
---
# <a name="fetchoptions-property-rds"></a>FetchOptions-Eigenschaft (RDS)
Gibt den Typ des asynchronen fetchen an.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="setting-and-return-values"></a>Festlegen und Zurückgeben von Werten  
 Legt einen der folgenden Werte fest oder gibt ihn zurück.  
  
|Konstante|BESCHREIBUNG|  
|--------------|-----------------|  
|**adcFetchUpFront**|Alle Datensätze des [Recordsets](../ado-api/recordset-object-ado.md) werden abgerufen, bevor die Steuerung an die Anwendung zurückgegeben wird. Das gesamte **Recordset** wird abgerufen, bevor die Anwendung mit der Anwendung arbeiten darf.|  
|**adcFetchBackground**|Das Steuerelement kann zur Anwendung zurückkehren, sobald der erste Batch von Datensätzen abgerufen wurde. Ein späterer Lesevorgang des **Recordsets** , das versucht, auf einen Datensatz zuzugreifen, der nicht im ersten Batch abgerufen wurde, wird verzögert, bis der gesuchte Datensatz tatsächlich abgerufen wird. zu diesem Zeitpunkt wird die Steuerung an die Anwendung zurückgegeben.|  
|**adcFetchAsync**|Standard. Die Steuerung wird sofort an die Anwendung zurückgegeben, während die Datensätze im Hintergrund abgerufen werden. Wenn die Anwendung versucht, einen Datensatz zu lesen, der noch nicht abgerufen wurde, wird der Datensatz, der dem gesuchten Datensatz am nächsten ist, gelesen, und die Steuerung wird sofort zurückgegeben. Dies deutet darauf hin, dass das aktuelle Ende des **Recordsets** erreicht wurde. Beispielsweise wird durch einen [MoveLast](./movefirst-movelast-movenext-and-moveprevious-methods-rds.md) -Aufrufvorgang die aktuelle Daten Satz Position in den letzten tatsächlich abgerufenen Datensatz verschoben, auch wenn weitere Datensätze weiterhin das **Recordset**auffüllen.|  
  
> [!NOTE]
>  Jede Client seitige ausführbare Datei, die diese Konstanten verwendet, muss Deklarationen für Sie bereitstellen. Sie können die gewünschten Konstanten Deklarationen aus der Datei "adcvsb. Inc" Ausschneiden und einfügen, die sich im Standard Installationsordner für die RDS-Bibliothek befindet.  
  
## <a name="remarks"></a>Bemerkungen  
 In einer Webanwendung möchten Sie in der Regel **adcfetchasync** (Standardwert) verwenden, da Sie eine bessere Leistung bietet. In einer kompilierten Client Anwendung möchten Sie in der Regel **adcFetchBackground**verwenden.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eigenschaften von "ExecuteOptions" und "FetchOptions" (VBScript)](./executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Cancel-Methode (RDS)](./cancel-method-rds.md)