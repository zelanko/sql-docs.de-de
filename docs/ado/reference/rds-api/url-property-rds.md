---
title: URL-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- URL property [ADO]
ms.assetid: 8c56b233-1be8-442c-8d0e-a4c96465bc99
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d4093321edfca7d1176c4b5be18ee876888b1a2
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600033"
---
# <a name="url-property-rds"></a>URL-Eigenschaft (RDS)
Gibt eine Zeichenfolge, die eine relative oder absolute URL enthält.  
  
 Sie können festlegen, die **URL** Eigenschaft zur Entwurfszeit in den [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) OBJEKTS kennzeichnen, oder zur Laufzeit im Skriptcode.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>Parameter  
 *Server*  
 Ein **Zeichenfolge** Wert, der eine gültige URL enthält.  
  
 *DataControl*  
 Eine Objektvariable, steht ein **DataControl** Objekt.  
  
## <a name="remarks"></a>Hinweise  
 In der Regel identifiziert die URL eine ASP-Seite (.asp)-Datei, die zu erzeugen und zurückgeben kann eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Aus diesem Grund erhalten die Benutzer eine **Recordset** ohne serverseitigen Aufrufen zu müssen [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt oder ein benutzerdefiniertes Geschäftsobjekt programmieren.  
  
 Wenn die **URL** Eigenschaft festgelegt wurde, [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) übergeben von Änderungen an den Speicherort, der durch die URL angegeben werden.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [URL-Eigenschaft – Beispiel (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


