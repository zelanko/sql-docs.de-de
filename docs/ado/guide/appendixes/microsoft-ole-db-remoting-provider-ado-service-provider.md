---
title: Microsoft OLE DB Remoting-Anbieter (ADO-Dienstanbieter) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB remoting provider [ADO]
- providers [ADO], OLE DB remoting provider
- remoting provider [ADO]
ms.assetid: a4360ed4-b70f-4734-9041-4025d033346b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 794e71013b552cbd4e17b9cb37e4c8c261aeeae6
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702694"
---
# <a name="microsoft-ole-db-remoting-provider-overview"></a>Übersicht über die Microsoft OLE DB Remoting-Anbieter
Der Microsoft OLE DB-Anbieter für Remoting können einen lokalen Benutzer auf einem Clientcomputer, um Datenanbieter auf einem Remotecomputer aufzurufen. Geben Sie die Data-Anbieter-Parameter für den Remotecomputer, wie Sie tun würden, würden Sie einen lokalen Benutzer auf dem Remotecomputer. Geben Sie dann die Parameter, die den Remoting-Anbieter für den Remotecomputer zugreifen. Sie können dann den Remotecomputer zugreifen, als wären Sie ein lokaler Benutzer.

> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).

## <a name="provider-keyword"></a>Anbieterschlüsselwort
 Um den OLE DB-Anbieter für Remoting aufzurufen, geben Sie das folgende Schlüsselwort und Wert in der Verbindungszeichenfolge ein. (Beachten Sie den leeren Bereich in der Name des Anbieters ein.)

```vb
"Provider=MS Remote"
```

## <a name="additional-keywords"></a>Zusätzliche Schlüsselwörter
 Wenn dieser Dienstanbieter aufgerufen wird, sind die folgenden zusätzlichen Schlüsselwörter relevant.

|Schlüsselwort|Description|
|-------------|-----------------|
|**Data Source**|Gibt den Namen der remote-Datenquelle. Es wird an den OLE DB-Anbieter für Remoting für die Verarbeitung übergeben.<br /><br /> Dieses Schlüsselwort entspricht der [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) des Objekts [Connect](../../../ado/reference/rds-api/connect-property-rds.md) Eigenschaft.|

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Wenn diesem Dienstanbieter aufgerufen wird, werden die folgenden dynamischen Eigenschaften hinzugefügt, auf die [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md)des Objekts [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.

|Name der dynamischen Eigenschaft|Description|
|---------------------------|-----------------|
|**DFMode**|Gibt den Data Factory-Modus. Eine Zeichenfolge, die die gewünschte Version gibt an, die [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt auf dem Server. Legen Sie diese Eigenschaft vor dem Öffnen einer Verbindungs zum Anfordern einer bestimmten Version von der **DataFactory**. Wenn die benötigte Version nicht verfügbar ist, wird es versucht werden, verwenden Sie die vorherige Version. Wenn keine vorherige Version vorhanden ist, tritt ein Fehler auf. Wenn **DFMode** kleiner als die verfügbare Version ist, tritt ein Fehler auf. Diese Eigenschaft ist schreibgeschützt, nachdem eine Verbindung hergestellt wird.<br /><br /> Dabei kann es sich um eine der folgenden Zeichenfolgenwerte gültig sein:<br /><br /> -"25"-Version 2.5 (Standard)<br />-   "21"-Version 2.1<br />-   "20"-Version 2.0<br />-   "15"-Version 1.5|
|**Befehlseigenschaften**|Gibt die Werte, die auf die Zeichenfolge der (Rowset)-Befehlseigenschaften, die an den Server gesendet werden, durch den MS Remote-Anbieter hinzugefügt werden. Der Standardwert für diese Zeichenfolge ist Vt_empty.|
|**Aktuelle DFMode**|Gibt die tatsächliche Anzahl von der **DataFactory** auf dem Server. Überprüfen Sie diese Eigenschaft, um festzustellen, ob die Version im angeforderten der **DFMode** Eigenschaft berücksichtigt wurde.<br /><br /> Die folgenden gültigen Long Integer-Wert-Werte sind möglich:<br /><br /> -25-Version 2.5 (Standard)<br />-   21-Version 2.1<br />-   20-Version 2.0<br />-   15-Version 1.5<br /><br /> Hinzufügen von "DFMode = 20;" zur Verbindungszeichenfolge bei Verwendung der **MSRemote** Anbieter kann die Leistung Ihres Servers verbessern, beim Aktualisieren von Daten. Mit dieser Einstellung die **RDSServer.DataFactory** Objekt auf dem Server einen weniger ressourcenintensiv-Modus verwendet. Die folgenden Funktionen sind jedoch nicht in dieser Konfiguration verfügbar:<br /><br /> – Verwenden von parametrisierten Abfragen.<br />– Abrufen der Parameter oder eine Spalte Informationen vor dem Aufruf der **Execute** Methode.<br />– Festlegen **Transact Updates** zu **"true"** .<br />-Abrufen des Zeilenstatus.<br />– Aufrufen der **Resync** Methode.<br />-Aktualisieren (explizit oder automatisch) über die **Update Resync** Eigenschaft.<br />– Festlegen **Befehl** oder **Recordset** Eigenschaften.<br />-   Using **adCmdTableDirect**.|
|**Handler**|Gibt den Namen des eine serverseitige Anpassung-Programm (oder Ereignishandler), die die Funktionalität von erweitert die [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), und alle Parameter, die vom Handler verwendete *,* getrennt durch Kommas ( ","). Ein **String-Wert**.|
|**Internet-Zeitüberschreitung.**|Gibt die maximale Anzahl von Millisekunden für eine Anforderung zum und vom Server zu übertragen. (Der Standardwert ist 5 Minuten.)|
|**Remote-Anbieter**|Gibt den Namen des Datenanbieters auf dem Remoteserver verwendet werden.|
|**Remoteserver**|Gibt an, das Serverprotokoll Name und die Kommunikation, die von dieser Verbindung verwendet werden. Diese Eigenschaft entspricht der [RDS. DataContro](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt [Server](../../../ado/reference/rds-api/server-property-rds.md) Eigenschaft.|
|**Transact-Updates**|Bei Festlegung auf **"true"** , dieser Wert gibt an, die bei [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) erfolgt auf dem Server, wird er innerhalb einer Transaktion ausgeführt werden. Der Standardwert für diese boolesche Eigenschaft für die dynamische ist **"false"** .|

 Sie können auch beschreibbare dynamische Eigenschaften festlegen, durch deren Namen als Schlüsselwörter in der Verbindungszeichenfolge angeben. Legen Sie z. B. die **Internet-Zeitüberschreitung** dynamische Eigenschaft auf fünf Sekunden, indem Sie angeben:

```vb
Dim cn as New ADODB.Connection
cn.Open "Provider=MS Remote;Internet Timeout=5000"
```

 Sie können auch festlegen oder Abrufen eine dynamische Eigenschaft durch Angabe seines Namens als Index für die **Eigenschaften** Eigenschaft. Das folgende Beispiel zeigt das Abrufen und drucken den aktuellen Wert des der **Internet-Zeitüberschreitung** dynamische Eigenschaft, und legen Sie dann einen neuen Wert:

```vb
Debug.Print cn.Properties("Internet Timeout")
cn.Properties("Internet Timeout") = 5000
```

## <a name="remarks"></a>Hinweise
 In ADO 2.0 konnte die OLE DB-Anbieter für Remoting nur in angegeben werden die *ActiveConnection* Parameter, der die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt **öffnen** Methode. ADO 2.1 ab, der Anbieter kann auch angegeben werden der *"ConnectionString"* Parameter der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt **öffnen** Methode.

 Das Äquivalent der **RDS. DataControl** Objekt [SQL](../../../ado/reference/rds-api/sql-property.md) Eigenschaft ist nicht verfügbar. Die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt **öffnen** Methode *Quelle* Argument wird stattdessen verwendet.

 **Beachten Sie** Angabe "...; Remote Provider = MS Remote;... "würde zu einem Szenario mit vier Ebenen erstellen. Szenarien mit mehr als drei Ebenen wurden nicht getestet und sollte nicht erforderlich.

## <a name="example"></a>Beispiel
 In diesem Beispiel führt eine Abfrage für die **Autoren** Tabelle mit den **Pubs** Datenbank auf einem Server mit dem Namen *Ihr Server*. Die Namen der remote-Datenquelle und Remoteserver finden Sie in der [öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) -Methode der der[Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt, und die SQL-Abfrage wird angegeben, der[öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode der der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt. Ein **Recordset** Objekt zurückgegeben, bearbeitet und zum Aktualisieren der Datenquelle verwendet wird.

```vb
Dim rs as New ADODB.Recordset
Dim cn as New ADODB.Connection
cn.Open  "Provider=MS Remote;Data Source=pubs;" & _
         "Remote Server=https://YourServer"
rs.Open "SELECT * FROM authors", cn
...                'Edit the recordset
rs.UpdateBatch     'Equivalent of RDS SubmitChanges
...
```

## <a name="see-also"></a>Siehe auch
 [Übersicht über die OLE DB Remoting-Anbieter](https://msdn.microsoft.com/4083b72f-68c4-4252-b366-abb70db5ca2b)
