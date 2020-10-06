---
description: Servereigenschaft (RDS)
title: Server Eigenschaft (RDS) | Microsoft-Dokumentation
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
f1_keywords:
- RDS::IBindMgr21::Server
helpviewer_keywords:
- Server property [RDS]
ms.assetid: d2727ce7-da9f-4271-ae3c-9334ef477c14
author: rothja
ms.author: jroth
ms.openlocfilehash: ad10cbb434c1fda57f684438499bf6e4b885cf9b
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724238"
---
# <a name="server-property-rds"></a>Servereigenschaft (RDS)
Gibt den Namen des Internetinformationsdienste (IIS) und das Kommunikationsprotokoll an.  
  
 Sie können die **Server** -Eigenschaft zur Entwurfszeit in den Objekt Tags des[RDS festlegen. DataControl](./datacontrol-object-rds.md) -Objekt oder zur Laufzeit im Skriptcode.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="syntax"></a>Syntax  
 **HTTP**  
  
 Syntax zur Entwurfszeit  
  
```  
  
<PARAM NAME="Server" VALUE="http:  
//awebsrvr:port  
">  
  
```  
  
 Lauf Zeit Syntax  
  
```  
  
DataControl  
.Server="https://  
awebsrvr:port  
"  
  
```  
  
 **HTTPS**  
  
 Syntax zur Entwurfszeit  
  
```  
  
<PARAM NAME="Server" VALUE="https://awebsrvr:port">  
```  
  
 Lauf Zeit Syntax  
  
```  
  
DataControl.Server="https://awebsrvr:port"  
```  
  
 **DCOM**  
  
 Syntax zur Entwurfszeit  
  
```  
  
<PARAM NAME="Server" VALUE="  
computername  
">  
  
```  
  
 Lauf Zeit Syntax  
  
```  
  
DataControl.Server="computername"  
```  
  
 **In-Process**  
  
 Syntax zur Entwurfszeit  
  
```  
  
<PARAM NAME="Server" VALUE="">  
  
```  
  
 Lauf Zeit Syntax  
  
```  
  
DataControl.Server=""  
```  
  
## <a name="parameters"></a>Parameter  
 *awebsrvr*oder *Computername*  
 Ein **Zeichen** folgen Wert, der einen Internet-oder intranetpfad bzw. einen Computernamen enthält, wenn sich der Server auf einem Remote Computer befindet. oder eine leere Zeichenfolge, wenn sich der Server auf dem lokalen Computer befindet.  
  
 *port*  
 Optional. Port, der zum Herstellen einer Verbindung mit einem Server verwendet wird, auf dem IIS ausgeführt wird. Die Portnummer wird in Internet Explorer festgelegt (Klicken Sie im Menü **Ansicht** auf **Optionen**, und wählen Sie dann die Registerkarte **Verbindung** ) oder in IIS aus.  
  
 *DataControl*  
 Eine Objekt Variable, die einen **RDS darstellt. DataControl** -Objekt.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Server ist der Ort, an dem das RDS-Verzeichnis ist **. Die DataControl** -Anforderung (d. h. eine Abfrage oder ein Update) wird verarbeitet. Standardmäßig werden alle Anforderungen vom [RDSServer. DataFactory](./datafactory-object-rdsserver.md) -Objekt, [msdfmap, verarbeitet. Handlerkomponente](../../guide/remote-data-service/datafactory-customization.md) und [MSDFMAP.INI](../../guide/remote-data-service/understanding-the-customization-file.md) Datei auf dem angegebenen Server. Beachten Sie, dass beim Ändern von Servern, um die Einstellungen in den alten und neuen **MSDFMAP.INI** Dateien abzustimmen. Inkompatibilitäten können dazu führen, dass auf einem Server erfolgreiche Anforderungen auf einem anderen Server fehlschlagen. Wenn die Server-Eigenschaft auf die leere Zeichenfolge "" festgelegt ist, werden diese Objekte auf dem lokalen Computer verwendet.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Server Eigenschaft (VBScript)](./server-property-example-vbscript.md)   
 [Connect-Eigenschaft (RDS)](./connect-property-rds.md)   
 [SQL-Eigenschaft](./sql-property.md)   
 [SubmitChanges-Methode (RDS)](./submitchanges-method-rds.md)