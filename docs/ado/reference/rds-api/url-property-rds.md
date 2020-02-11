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
ms.openlocfilehash: c88b8029ee5d96986cf9b366bd8faee53ca1393b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963226"
---
# <a name="url-property-rds"></a>URL-Eigenschaft (RDS)
Gibt eine Zeichenfolge an, die eine relative oder absolute URL enthält.  
  
 Sie können die **URL** -Eigenschaft zur Entwurfszeit im Objekttag des [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekts oder zur Laufzeit im Skriptcode festlegen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
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
 In der Regel identifiziert die URL eine Active Server Page (ASP)-Datei, die ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)erzeugt und zurückgeben kann. Daher kann der Benutzer ein **Recordset** abrufen, ohne das serverseitige [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) -Objekt aufrufen oder ein benutzerdefiniertes Geschäftsobjekt programmieren zu müssen.  
  
 Wenn die **URL** -Eigenschaft festgelegt wurde, übermitteln [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) Änderungen an den von der URL angegebenen Speicherort.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [URL-Eigenschaft – Beispiel (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


