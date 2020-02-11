---
title: Microsoft OLE DB Remoting Provider (ADO-Dienstanbieter) | Microsoft-Dokumentation
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
ms.openlocfilehash: 5c60567da677564c168f0601625686bdfb8b3d67
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926599"
---
# <a name="microsoft-ole-db-remoting-provider-overview"></a>Übersicht über den Microsoft OLE DB Remoting-Anbieter
Der Microsoft OLE DB Remoting-Anbieter ermöglicht einem lokalen Benutzer auf einem Client Computer das Aufrufen von Datenanbietern auf einem Remote Computer. Geben Sie die Datenanbieter Parameter für den Remote Computer so an, als wären Sie ein lokaler Benutzer auf dem Remote Computer. Geben Sie dann die Parameter an, die vom Remote Anbieter für den Zugriff auf den Remote Computer verwendet werden. Sie können dann auf den Remote Computer zugreifen, als handele es sich um einen lokalen Benutzer.

> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.

## <a name="provider-keyword"></a>Provider-Schlüsselwort
 Um den OLE DB Remoting-Anbieter aufzurufen, geben Sie das folgende Schlüsselwort und den Wert in der Verbindungs Zeichenfolge an. (Beachten Sie den Leerraum im Anbieter Namen.)

```vb
"Provider=MS Remote"
```

## <a name="additional-keywords"></a>Zusätzliche Schlüsselwörter
 Wenn dieser Dienstanbieter aufgerufen wird, sind die folgenden zusätzlichen Schlüsselwörter relevant.

|Schlüsselwort|BESCHREIBUNG|
|-------------|-----------------|
|**Data Source**|Gibt den Namen der Remote Datenquelle an. Sie wird zur Verarbeitung an den OLE DB Remoting-Anbieter übermittelt.<br /><br /> Dieses Schlüsselwort entspricht dem [RDS. ](../../../ado/reference/rds-api/datacontrol-object-rds.md) [Connect](../../../ado/reference/rds-api/connect-property-rds.md) -Eigenschaft des DataControl-Objekts.|

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Wenn dieser Dienstanbieter aufgerufen wird, werden die folgenden dynamischen Eigenschaften der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung des [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md)Objekts hinzugefügt.

|Name der dynamischen Eigenschaft|BESCHREIBUNG|
|---------------------------|-----------------|
|**DFMode**|Gibt den DataFactory-Modus an. Eine Zeichenfolge, die die gewünschte Version des [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) -Objekts auf dem Server angibt. Legen Sie diese Eigenschaft fest, bevor Sie eine Verbindung öffnen, um eine bestimmte Version des **DataFactory**anzufordern. Wenn die angeforderte Version nicht verfügbar ist, wird versucht, die vorherige Version zu verwenden. Wenn keine vorangehende Version vorhanden ist, tritt ein Fehler auf. Wenn **DFMode** kleiner als die verfügbare Version ist, tritt ein Fehler auf. Diese Eigenschaft ist schreibgeschützt, nachdem eine Verbindung hergestellt wurde.<br /><br /> Kann einer der folgenden gültigen Zeichen folgen Werte sein:<br /><br /> -"25"-Version 2,5 (Standard)<br />-"21"-Version 2,1<br />-"20"-Version 2,0<br />-15, Version 1,5|
|**Befehls Eigenschaften**|Gibt Werte an, die der Zeichenfolge der Command (Rowset)-Eigenschaften hinzugefügt werden, die vom MS-Remote Anbieter an den Server gesendet werden. Der Standardwert für diese Zeichenfolge ist VT_EMPTY.|
|**Aktueller DFMode**|Gibt die tatsächliche Versionsnummer des **DataFactory** auf dem Server an. Überprüfen Sie diese Eigenschaft, um festzustellen, ob die in der **DFMode** -Eigenschaft angeforderte Version berücksichtigt wurde.<br /><br /> Kann einer der folgenden gültigen Long-ganzzahligen Werte sein:<br /><br /> -25-Version 2,5 (Standard)<br />-21-Version 2,1<br />-20-Version 2,0<br />-15-Version 1,5<br /><br /> Wenn Sie "DFMode = 20;" der Verbindungs Zeichenfolge hinzufügen, wenn Sie den **msremote** -Anbieter verwenden, kann die Leistung des Servers beim Aktualisieren von Daten verbessert werden. Mit dieser Einstellung verwendet das **RDSServer. DataFactory** -Objekt auf dem Server einen weniger ressourcenintensiven Modus. Die folgenden Funktionen sind in dieser Konfiguration jedoch nicht verfügbar:<br /><br /> -Verwenden von parametrisierten Abfragen.<br />: Abrufen von Parameter-oder Spalten Informationen vor dem Aufrufen der **Execute** -Methode.<br />-Die **Transact-Updates** werden auf **true**festgelegt.<br />-Zeilen Status wird erhalten.<br />-Aufrufen der **Resync** -Methode.<br />-Aktualisieren (explizit oder automatisch) über die Eigenschaft " **Resync aktualisieren** ".<br />-Festlegen von **Befehls** -oder **Recordseteigenschaften** .<br />-Verwenden von **adCmdTableDirect**.|
|**Handler**|Gibt den Namen eines serverseitigen Anpassungsprogramms (oder-Handlers) an, das die Funktionalität von [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)erweitert, sowie alle Parameter, die vom Handler verwendet werden, die durch Kommas (",") getrennt sind. Ein **String-Wert**.|
|**Internet Timeout**|Gibt die maximale Anzahl von Millisekunden an, die auf die Übertragung einer Anforderung zum und vom Server gewartet werden soll. (Der Standardwert ist 5 Minuten.)|
|**Remote Anbieter**|Gibt den Namen des Datenanbieters an, der auf dem Remote Server verwendet werden soll.|
|**Remote Server**|Gibt den Servernamen und das Kommunikationsprotokoll an, die von dieser Verbindung verwendet werden sollen. Diese Eigenschaft entspricht dem [RDS. Datacontro](../../../ado/reference/rds-api/datacontrol-object-rds.md) Object [Server](../../../ado/reference/rds-api/server-property-rds.md) -Eigenschaft.|
|**Transact-Updates**|Wenn der Wert auf **true**festgelegt ist, gibt dieser Wert an, dass, wenn [Update Batch](../../../ado/reference/ado-api/updatebatch-method.md) auf dem Server ausgeführt wird, innerhalb einer Transaktion ausgeführt wird. Der Standardwert für diese boolesche dynamische Eigenschaft ist **false**.|

 Sie können auch beschreibbare dynamische Eigenschaften festlegen, indem Sie Ihre Namen als Schlüsselwörter in der Verbindungs Zeichenfolge angeben. Legen Sie z. b. die dynamische Eigenschaft **Internet Timeout** auf fünf Sekunden fest, indem Sie Folgendes angeben:

```vb
Dim cn as New ADODB.Connection
cn.Open "Provider=MS Remote;Internet Timeout=5000"
```

 Sie können auch eine dynamische Eigenschaft festlegen oder abrufen, indem Sie Ihren Namen als Index für die **Properties** -Eigenschaft angeben. Im folgenden Beispiel wird gezeigt, wie Sie den aktuellen Wert der dynamischen Eigenschaft **Internet Timeout** erhalten und ausdrucken und dann einen neuen Wert festlegen:

```vb
Debug.Print cn.Properties("Internet Timeout")
cn.Properties("Internet Timeout") = 5000
```

## <a name="remarks"></a>Bemerkungen
 In ADO 2,0 konnte der OLE DB Remoting-Anbieter nur im *ActiveConnection* -Parameter der **Open** -Methode des [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekts angegeben werden. Ab ADO 2,1 kann der Anbieter auch im *ConnectionString* -Parameter der [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt-Methode " **Open** " angegeben werden.

 Die Entsprechung des **RDS. **Die [SQL](../../../ado/reference/rds-api/sql-property.md) -Eigenschaft des DataControl-Objekts ist nicht verfügbar. Stattdessen wird das **Open** -method- *Quell* Argument des [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekts verwendet.

 **Hinweis** Angeben von "...; Remote Anbieter = MS Remote;... " würde ein Szenario mit vier Ebenen erstellen. Szenarien, die drei Ebenen überschreiten, wurden nicht getestet und sollten nicht benötigt werden.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird eine Abfrage für die Tabelle " **Authors** " der **Pubs** -Datenbank auf einem Server namens " *yourserver*" durchführt. Die Namen der Remote Datenquelle und des Remote Servers werden in der [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) -Methode des[Connection](../../../ado/reference/ado-api/connection-object-ado.md) -Objekts bereitgestellt, und die SQL-Abfrage wird in der[Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode des [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekts angegeben. Ein **Recordset** -Objekt wird zurückgegeben, bearbeitet und zum Aktualisieren der Datenquelle verwendet.

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

## <a name="see-also"></a>Weitere Informationen
 [Übersicht über den OLE DB Remoting-Anbieter](https://msdn.microsoft.com/4083b72f-68c4-4252-b366-abb70db5ca2b)
