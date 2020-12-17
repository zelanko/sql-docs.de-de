---
description: Erforderliche Clienteinstellungen
title: Erforderliche Client Einstellungen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
author: rothja
ms.author: jroth
ms.openlocfilehash: 614f8f4444ab470530cea01133b34adffc505b78
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97638028"
---
# <a name="required-client-settings"></a>Erforderliche Clienteinstellungen
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
 Geben Sie die folgenden Einstellungen für die Verwendung eines benutzerdefinierten **DataFactory** -Handlers an.  
  
-   Geben Sie "Provider = MS Remote" in der ADO-Eigenschaft ( [Verbindungs Objekt](../../reference/ado-api/connection-object-ado.md) -Objekt [Anbieter Eigenschaft)](../../reference/ado-api/provider-property-ado.md) oder Verbindungs Zeichenfolge "**Provider**=" Verbindungs Zeichenfolge für **Verbindungs** Objekt an.  
  
-   Legen Sie die Eigenschaft für die [Cursor Location-Eigenschaft (ADO)](../../reference/ado-api/cursorlocation-property-ado.md) auf **adUseClient** fest.  
  
-   Geben Sie den Namen des Handlers an, der in der **Handler** -Eigenschaft des [DataControl-Objekts (Objekt des DataControl-Objekts)](../../reference/rds-api/datacontrol-object-rds.md) oder der Verbindungs Zeichenfolge für das [Recordset-Objekt (ADO)](../../reference/ado-api/recordset-object-ado.md) -Objekt verwendet werden soll. (Der Handler kann nicht in der Verbindungs Zeichenfolge für **Verbindungs** Objekte festgelegt werden.)  
  
 RDS stellt einen Standard Handler auf dem Server namens **msdfmap bereit. Handler**. (Die Standard Anpassungs Datei hat den Namen MSDFMAP.INI.)  
  
 **Beispiel**  
  
 Angenommen, die folgenden Abschnitte in **MSDFMAP.INI** und der Datenquellen Name AdvWorks wurden zuvor definiert:  
  
```console
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 Die folgenden Code Ausschnitte werden in Visual Basic geschrieben:  
  
## <a name="rdsdatacontrol-version"></a>RDS. DataControl-Version  
  
```vb
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "https://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>Recordsetversion  
  
```vb
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 Geben Sie entweder die Eigenschaft oder das Schlüsselwort der [Handlereigenschaft (RDS)](../../reference/rds-api/handler-property-rds.md) an. die Eigenschaft oder das Schlüsselwort der [Provider-Eigenschaft (ADO)](../../reference/ado-api/provider-property-ado.md) ; und die Bezeichner *customerbyid* und *CustomerDatabase* . Öffnen Sie anschließend das **Recordset** -Objekt.  
  
 Graben. Öffnen Sie "customerbyid (4)", "Handler = msdfmap. Handler; "& _  
  
```vb
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=https://yourServer"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereich für die Anpassungs Dateiverbindung](./customization-file-connect-section.md)   
 [SQL-Abschnitt der Anpassungs Datei](./customization-file-sql-section.md)   
 [Benutzer Listen Abschnitt "Anpassungs Datei"](./customization-file-userlist-section.md)   
 [DataFactory-Anpassung](./datafactory-customization.md)   
 [Grundlegendes zur Anpassungs Datei](./understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](./writing-your-own-customized-handler.md)