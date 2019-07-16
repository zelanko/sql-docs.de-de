---
title: Behandeln von Book-Datenbindungsobjekt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS scenarios [ADO], data-binding object
- address book application scenario [ADO], data-binding object
ms.assetid: 080c1925-d453-4b89-92ac-c93591490518
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 43623bc100fdfe071fcd00926117400a3c96eebe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922974"
---
# <a name="address-book-data-binding-object"></a>Adress Book-Datenbindungsobjekt
Das Adressbuch-App verwendet die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt, das Daten aus SQL Server-Datenbank auf ein visuelles Objekt (in diesem Fall ein DHTML-Tabelle) in der Anwendung Client-HTML-Seite zu binden. Die Logik der ereignisgesteuerten VBScript-Programm verwendet die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) auf:  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
-   Abfragen der Datenbank, Senden von Updates in der Datenbank, und aktualisieren Sie das Datenraster.  
  
-   Können Sie Benutzer zum ersten, als Nächstes vorherige verschieben, oder zum letzten Datensatz im Raster.  
  
 Der folgende Code definiert die **RDS. DataControl** Komponente:  
  
```vb
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=DC1 Width=1 Height=1>  
   <PARAM NAME="SERVER" VALUE="https://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider=sqloledb;  
Initial Catalog=AddrBookDb;Integrated Security=SSPI;">  
</OBJECT>  
```  
  
 OBJECT-Tag definiert die **RDS. DataControl** Komponente in der Anwendung. Das Tag enthält zwei Arten von Parametern:  
  
-   Die generische OBJECT-Tag.  
  
-   Um die für die **RDS. DataControl** Objekt.  
  
## <a name="generic-object-tag-parameters"></a>Generisches Objekt Tag-Parametern  
 Die folgende Tabelle beschreibt die OBJECT-Tag zugeordneten Parameter.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|***CLASSID***|Eine eindeutige, 128-Bit-Zahl, die den Typ des eingebetteten Objekt, das System identifiziert. Dieser Bezeichner wird in der systemregistrierung des lokalen Computers beibehalten. (Für den Klassen-IDs der **RDS. DataControl** Objekt, finden Sie unter [RDS. DataControl-Objekt](../../../ado/reference/rds-api/datacontrol-object-rds.md).)|  
|***ID***|Definiert einen dokumentweiten Bezeichner für das eingebettete Objekt, das verwendet wird, um es im Code zu identifizieren.|  
  
## <a name="rdsdatacontrol-tag-parameters"></a>RDS. DataControl-Tag-Parametern  
 Die folgende Tabelle beschreibt die Parameter für die **RDS. DataControl** Objekt. (Eine vollständige Liste der **RDS. DataControl** Objekt, Parameter, und wann sie implementieren, finden Sie unter [RDS. DataControl-Objekt](../../../ado/reference/rds-api/datacontrol-object-rds.md).)  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|[SERVER](../../../ado/reference/rds-api/server-property-rds.md)|Wenn Sie HTTP verwenden, wird der Wert ist der Name des Servercomputers vorangestellt `https://`.|  
|[CONNECT](../../../ado/reference/rds-api/connect-property-rds.md)|Stellt die erforderlichen Verbindungsinformationen für die **RDS. DataControl** zur Verbindung mit SQL Server.|  
|[SQL](../../../ado/reference/rds-api/sql-property.md)|Legt fest oder gibt die Abfragezeichenfolge zum Abrufen der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Adress Book-Befehlsschaltflächen](../../../ado/guide/remote-data-service/address-book-command-buttons.md)


