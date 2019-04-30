---
title: Open-Methode (ADO Record) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b4d105d648c7877e7099dea637c2a2c6a094985f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241086"
---
# <a name="open-method-ado-record"></a>Open-Methode (ADO Record)
Öffnet ein vorhandenes [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt oder erstellt ein neues Element, dargestellt durch die **Datensatz**, z. B. eine Datei oder ein Verzeichnis.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Dies ist optional. Ein **Variant** , kann die URL der Entität, die von diesem dargestellt werden darstellen **Datensatz** Objekt eine **Befehl**, ein offenes [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oder eine andere **Datensatz** -Objekt, das eine Zeichenfolge mit einer SQL SELECT-Anweisung oder einen Tabellennamen an.  
  
 *ActiveConnection*  
 Dies ist optional. Ein **Variant** , das darstellt, der die Verbindungszeichenfolge oder Open [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt.  
  
 *Mode*  
 Dies ist optional. Ein [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) Wert, der angibt, den den Zugriffsmodus für die resultierenden **Datensatz** Objekt. Standardwert ist **AdModeUnknown**.  
  
 *CreateOptions*  
 Optional. Ein [RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md) -Wert, der angibt, ob eine vorhandene Datei oder ein Verzeichnis geöffnet werden soll, oder eine neue Datei oder ein Verzeichnis erstellt werden soll. Standardwert ist **AdFailIfNotExists**. Wenn auf den Standardwert festgelegt, die den Zugriffsmodus aus erfolgt die [Modus](../../../ado/reference/ado-api/mode-property-ado.md) Eigenschaft. Dieser Parameter wird ignoriert, wenn der *Quelle* -Parameter enthält keine URL.  
  
 *Optionen*  
 Dies ist optional. Ein [RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md) Wert, der angibt, die Optionen zum Öffnen der **Datensatz**. Standardwert ist **AdOpenRecordUnspecified**. Diese Werte können kombiniert werden.  
  
 *UserName*  
 Optional. Ein **Zeichenfolge** Wert, der die Benutzer-ID, die enthält bei Bedarf, autorisiert den Zugriff auf *Quelle*.  
  
 *Kennwort*  
 Dies ist optional. Ein **Zeichenfolge** Wert, der das Kennwort, die enthält bei Bedarf, überprüft *Benutzername*.  
  
## <a name="remarks"></a>Hinweise  
 *Quelle* möglicherweise:  
  
-   EINE URL. Wenn das Protokoll für die URL über http ist, wird standardmäßig Internetanbieter aufgerufen. Wenn die URL zu einem Knoten verweist, der ein ausführbares Skript enthält (z. B. ein. ASP-Seite), eine **Datensatz** , enthält die Datenquelle anstelle der ausgeführten Inhalt wird standardmäßig geöffnet. Verwenden der *Optionen* Argument, um dieses Verhalten zu ändern.  
  
-   Ein **Datensatz** Objekt. Ein **Datensatz** -Objekt geöffnet wird, von einem anderen **Datensatz** wird die ursprüngliche Klonen **Datensatz** Objekt.  
  
-   Ein **Befehl** Objekt. Die geöffnete **Datensatz** Objekt darstellt, die einzelne Zeile zurückgegeben, die durch Ausführen der **Befehl**. Die Ergebnisse mehr als eine einzelne Zeile enthalten, den Inhalt der ersten Zeile befinden sich im Datensatz und Fehler kann hinzugefügt werden, um die **Fehler** Auflistung.  
  
-   Eine SQL-SELECT-Anweisung. Die geöffnete **Datensatz** Objekt darstellt, die einzelne Zeile, die durch Ausführen der Inhalt der Zeichenfolge zurückgegeben. Die Ergebnisse mehr als eine einzelne Zeile enthalten, den Inhalt der ersten Zeile befinden sich im Datensatz und Fehler kann hinzugefügt werden, um die **Fehler** Auflistung.  
  
-   Ein Tabellenname.  
  
 Wenn die **Datensatz** Objekt eine Entität darstellt, die mit einer URL nicht zugegriffen werden kann (z. B. eine Zeile mit einer **Recordset** aus einer Datenbank abgeleitet), die Werte von der [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)-Eigenschaft und das Feld mit Zugriff auf die **AdRecordURL** Konstante null sind.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Open Sie-Methode (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open Sie-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open Sie-Methode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema-Methode](../../../ado/reference/ado-api/openschema-method.md)
