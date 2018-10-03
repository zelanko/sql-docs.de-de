---
title: Erforderliche Clienteinstellungen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c7e8b5d0583c2f0938c792d4e7fb9980e663a9b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667238"
---
# <a name="required-client-settings"></a>Erforderliche Clienteinstellungen
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Geben Sie die folgenden Einstellungen aus, um eine benutzerdefinierte **DataFactory** Handler.  
  
-   Geben Sie "Anbieter = MS-Remote" in der [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) Objekt [Provider-Eigenschaft (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft oder das **Verbindung** Objekt Verbindungszeichenfolge "**Anbieter**= "Schlüsselwort.  
  
-   Legen Sie die [CursorLocation-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft **AdUseClient**.  
  
-   Geben Sie den Namen des Handlers für die Verwendung in der [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) des Objekts **Handler** -Eigenschaft oder das [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) Verbindungszeichenfolge "des Objekts" " **Handler**= "Schlüsselwort. (Kann nicht, legen Sie den Handler in der **Verbindung** Objekt für die Verbindungszeichenfolge.)  
  
 RDS bietet einen Standard-Handler auf dem Server, die mit dem Namen **MSDFMAP. Handler**. (Die Standarddatei für die Anpassung heißt MSDFMAP. INI.)  
  
 **Beispiel**  
  
 Davon ausgehen, dass in den folgenden Abschnitten **MSDFMAP. INI** und den Namen der Datenquelle AdvWorks, zuvor definiert wurden:  
  
```  
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 Die folgenden Codeausschnitte sind in Visual Basic geschrieben:  
  
## <a name="rdsdatacontrol-version"></a>RDS. DataControl-Version  
  
```  
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "http://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>Recordset-Version  
  
```  
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 Geben Sie entweder die [Handler-Eigenschaft (RDS)](../../../ado/reference/rds-api/handler-property-rds.md) Eigenschaft oder ein Schlüsselwort; die [Provider-Eigenschaft (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft oder ein Schlüsselwort; und die *CustomerById* und  *CustomerDatabase* Bezeichner. Öffnen Sie dann die **Recordset** Objekt  
  
 RS. Öffnen Sie "CustomerById(4)", "Handler MSDFMAP =. Handler"& _  
  
```  
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=http://yourServer"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Connect-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [SQL-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [UserList-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Erforderliche Clienteinstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Grundlegendes zu der Anpassungsdatei](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)






















