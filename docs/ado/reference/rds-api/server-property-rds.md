---
title: Servereigenschaft (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: add581048739a6ba12dc046d2f9362816b661687
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680614"
---
# <a name="server-property-rds"></a>Servereigenschaft (RDS)
Gibt das Protokoll (Internet Information Services, IIS), Namen und die Kommunikation an.  
  
 Sie können festlegen, die **Server** Eigenschaft zur Entwurfszeit in den Objekt-Tags, der die[RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt oder zur Laufzeit im Skriptcode.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
 **HTTP**  
  
 Während der Entwurfszeit-syntax  
  
```  
  
<PARAM NAME="Server" VALUE="http:  
//awebsrvr:port  
">  
  
```  
  
 Laufzeit-syntax  
  
```  
  
DataControl  
.Server="http://  
awebsrvr:port  
"  
  
```  
  
 **HTTPS**  
  
 Während der Entwurfszeit-syntax  
  
```  
  
<PARAM NAME="Server" VALUE="https://awebsrvr:port">  
```  
  
 Laufzeit-syntax  
  
```  
  
DataControl.Server="https://awebsrvr:port"  
```  
  
 **DCOM**  
  
 Während der Entwurfszeit-syntax  
  
```  
  
<PARAM NAME="Server" VALUE="  
computername  
">  
  
```  
  
 Laufzeit-syntax  
  
```  
  
DataControl.Server="computername"  
```  
  
 **In-process**  
  
 Während der Entwurfszeit-syntax  
  
```  
  
<PARAM NAME="Server" VALUE="">  
  
```  
  
 Laufzeit-syntax  
  
```  
  
DataControl.Server=""  
```  
  
## <a name="parameters"></a>Parameter  
 *Awebsrvr*oder *Computername*  
 Ein **Zeichenfolge** Wert, der eine Internet oder Intranetpfad oder Namen des Computers enthält, wenn der Server auf einem Remotecomputer befindet, oder eine leere Zeichenfolge ist, wenn der Server auf dem lokalen Computer ist.  
  
 *port*  
 Optional. Ein Port, der zur Verbindung mit eines Servers mit IIS verwendet wird. Die Nummer des Ports, die in Internet Explorer festgelegt ist (auf der **Ansicht** Menü klicken Sie auf **Optionen**, und wählen Sie dann die **Verbindung** Registerkarte) oder in IIS.  
  
 *DataControl*  
 Eine Objektvariable, steht ein **RDS. DataControl** Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Der Server ist der Speicherort, in denen die **RDS. DataControl** Anforderung (d. h. eine Abfrage oder Aktualisierung) verarbeitet. Standardmäßig werden alle Anforderungen von verarbeitet die [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt [MSDFMAP. Handler](../../../ado/guide/remote-data-service/datafactory-customization.md) -Komponente und [MSDFMAP. INI](../../../ado/guide/remote-data-service/understanding-the-customization-file.md) Datei auf dem angegebenen Server. Beachten Sie, dass beim Ändern von Servern zum Abstimmen von Einstellungen in der alten und neuen **MSDFMAP. INI** Dateien. Inkompatibilitäten möglicherweise Anforderungen, die erfolgreich auf einem Server auf einem anderen fehl. Wenn die Server-Eigenschaft, auf die leere Zeichenfolge festgelegt ist "", diese Objekte auf dem lokalen Computer verwendet werden.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Server-Eigenschaft – Beispiel (VBScript)](../../../ado/reference/rds-api/server-property-example-vbscript.md)   
 [Connect-Eigenschaft (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [SQL-Eigenschaft](../../../ado/reference/rds-api/sql-property.md)   
 [SubmitChanges-Methode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


