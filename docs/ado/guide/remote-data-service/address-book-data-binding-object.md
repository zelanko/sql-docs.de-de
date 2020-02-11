---
title: Adressbuch-Daten Bindungs Objekt | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922974"
---
# <a name="address-book-data-binding-object"></a>Adress Book-Datenbindungsobjekt
Die Adressbuch Anwendung verwendet [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekt zum Binden von Daten aus der SQL Server Datenbank an ein visuelles Objekt (in diesem Fall eine DHTML-Tabelle) auf der Client-HTML-Seite der Anwendung. Die ereignisgesteuerte VBScript-Programmlogik verwendet [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) in:  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
-   Fragen Sie die Datenbank ab, senden Sie Aktualisierungen an die Datenbank, und aktualisieren Sie das Datenraster.  
  
-   Ermöglicht Benutzern das Wechseln zum ersten, nächsten, vorherigen oder letzten Datensatz im Datenraster.  
  
 Im folgenden Code wird der RDS-Code definiert **. DataControl** -Komponente:  
  
```vb
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=DC1 Width=1 Height=1>  
   <PARAM NAME="SERVER" VALUE="https://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider=sqloledb;  
Initial Catalog=AddrBookDb;Integrated Security=SSPI;">  
</OBJECT>  
```  
  
 Das Objekttag definiert das **RDS. Die Komponente "DataControl** " im Programm. Das-Tag enthält zwei Arten von Parametern:  
  
-   Die dem generischen Objekttag zugeordneten.  
  
-   Die für das **RDS spezifischen. DataControl** -Objekt.  
  
## <a name="generic-object-tag-parameters"></a>Generische Objekttagparameter  
 In der folgenden Tabelle werden die Parameter beschrieben, die dem Objekttag zugeordnet sind.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|***ClassID***|Eine eindeutige 128-Bit-Zahl, die den Typ des eingebetteten Objekts für das System identifiziert. Dieser Bezeichner wird in der Systemregistrierung des lokalen Computers verwaltet. (Für die Klassen-IDs der **RDS. DataControl** -Objekt finden Sie unter [RDS. DataControl-Objekt](../../../ado/reference/rds-api/datacontrol-object-rds.md).)|  
|***id***|Definiert einen Dokument weiten Bezeichner für das eingebettete Objekt, das zur Identifizierung im Code verwendet wird.|  
  
## <a name="rdsdatacontrol-tag-parameters"></a>RDS. DataControl-Tagparameter  
 In der folgenden Tabelle werden die für RDS spezifischen Parameter beschrieben **. DataControl** -Objekt. (Eine komplette Liste der **RDS. DataControl** -Objekt Parameter und wann diese implementiert werden sollten, finden Sie unter [RDS. DataControl-Objekt](../../../ado/reference/rds-api/datacontrol-object-rds.md).)  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|[Servers](../../../ado/reference/rds-api/server-property-rds.md)|Wenn Sie http verwenden, ist der Wert der Name des Server Computers, dem vorangestellt `https://`ist.|  
|[Herzustellen](../../../ado/reference/rds-api/connect-property-rds.md)|Stellt die erforderlichen Verbindungsinformationen für **RDS bereit. DataControl** zum Herstellen einer Verbindung mit SQL Server.|  
|[SQL](../../../ado/reference/rds-api/sql-property.md)|Legt die zum Abrufen des [Recordsets verwendete Abfrage Zeichenfolge](../../../ado/reference/ado-api/recordset-object-ado.md)fest oder gibt diese zurück.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Adress Book-Befehlsschaltflächen](../../../ado/guide/remote-data-service/address-book-command-buttons.md)


