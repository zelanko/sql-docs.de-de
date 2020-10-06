---
description: URL-Eigenschaft (RDS)
title: URL-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d693aab0c01e1a65715597c6f8905569aebbcae
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724672"
---
# <a name="url-property-rds"></a>URL-Eigenschaft (RDS)
Gibt eine Zeichenfolge an, die eine relative oder absolute URL enthält.  
  
 Sie können die **URL** -Eigenschaft zur Entwurfszeit im Objekttag des [DataControl](./datacontrol-object-rds.md) -Objekts oder zur Laufzeit im Skriptcode festlegen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>Parameter  
 *Server*  
 Ein **Zeichen** folgen Wert, der eine gültige URL enthält.  
  
 *DataControl*  
 Eine Objekt Variable, die ein **DataControl** -Objekt darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 In der Regel identifiziert die URL eine Active Server Page (ASP)-Datei, die ein [Recordset](../ado-api/recordset-object-ado.md)erzeugt und zurückgeben kann. Daher kann der Benutzer ein **Recordset** abrufen, ohne das serverseitige [DataFactory](./datafactory-object-rdsserver.md) -Objekt aufrufen oder ein benutzerdefiniertes Geschäftsobjekt programmieren zu müssen.  
  
 Wenn die **URL** -Eigenschaft festgelegt wurde, übermitteln [SubmitChanges](./submitchanges-method-rds.md) Änderungen an den von der URL angegebenen Speicherort.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [URL-Eigenschaft – Beispiel (VBScript)](./url-property-example-vbscript.md)