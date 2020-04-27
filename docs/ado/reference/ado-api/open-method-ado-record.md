---
title: Open-Methode (ADO-Datensatz) | Microsoft-Dokumentation
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
ms.openlocfilehash: 97c7f1c143c83dd35ca5ff17e9776d79fb734ff9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917927"
---
# <a name="open-method-ado-record"></a>Open-Methode (ADO Record)
Öffnet ein vorhandenes [Daten Satz](../../../ado/reference/ado-api/record-object-ado.md) Objekt oder erstellt ein neues Element, das durch den **Datensatz**dargestellt wird, z. b. eine Datei oder ein Verzeichnis.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Optional. Eine **Variante** , die die URL der Entität darstellt, die durch dieses **Daten Satz** Objekt dargestellt werden soll, einen **Befehl**, ein offenes [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oder ein anderes **Datensatz** -Objekt, eine Zeichenfolge, die eine SQL-SELECT-Anweisung oder einen Tabellennamen enthält.  
  
 *ActiveConnection*  
 Optional. Eine **Variante** , die die Verbindungs Zeichenfolge oder das geöffnete [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt darstellt.  
  
 *Mode*  
 Optional. Ein [connectmodeenum](../../../ado/reference/ado-api/connectmodeenum.md) -Wert, der den Zugriffsmodus für das resultierende **Datensatz** -Objekt angibt. Der Standardwert ist **adModeUnknown**.  
  
 *"Kreateoptions"*  
 Optional. Ein [recordkreateoptionsenum](../../../ado/reference/ado-api/recordcreateoptionsenum.md) -Wert, der angibt, ob eine vorhandene Datei oder ein vorhandenes Verzeichnis geöffnet werden soll, oder ob eine neue Datei oder ein neues Verzeichnis erstellt werden soll. Der Standardwert ist " **adfailif NotExists**". Wenn der Standardwert festgelegt ist, wird der Zugriffsmodus aus der [Mode](../../../ado/reference/ado-api/mode-property-ado.md) -Eigenschaft abgerufen. Dieser Parameter wird ignoriert, wenn der *Quell* Parameter keine URL enthält.  
  
 *Optionen*  
 Optional. Ein [recordopenoptionsenum](../../../ado/reference/ado-api/recordopenoptionsenum.md) -Wert, der Optionen zum Öffnen des **Datensatzes**angibt. Der Standardwert ist " **adopendrecordunspezifiziert**". Diese Werte können kombiniert werden.  
  
 *User*  
 Optional. Ein **Zeichen** folgen Wert, der die Benutzer-ID enthält, die, falls erforderlich, den Zugriff auf die *Quelle*autorisiert.  
  
 *Kennwort*  
 Optional. Ein **Zeichen** folgen Wert, der das Kennwort enthält, das bei Bedarf den *Benutzernamen*überprüft.  
  
## <a name="remarks"></a>Hinweise  
 Die *Quelle* kann Folgendes sein:  
  
-   Eine URL. Wenn das Protokoll für die URL http lautet, wird standardmäßig der Internet Anbieter aufgerufen. , Wenn die URL auf einen Knoten verweist, der ein ausführbares Skript enthält (z. b.). ASP-Seite). Standardmäßig wird ein **Datensatz** geöffnet, der die Quelle anstelle des ausgeführten Inhalts enthält. Verwenden Sie das *options* -Argument, um dieses Verhalten zu ändern.  
  
-   Ein **Daten Satz** Objekt. Ein **Daten Satz** Objekt, das aus einem anderen **Datensatz** geöffnet wird, Klonen das ursprüngliche **Datensatz** -Objekt.  
  
-   Ein **Command** -Objekt. Das geöffnete **Datensatz** -Objekt stellt die einzelne Zeile dar, die durch Ausführen des **Befehls**zurückgegeben wird. Wenn die Ergebnisse mehr als eine einzelne Zeile enthalten, wird der Inhalt der ersten Zeile in den Datensatz eingefügt, und der **Fehler** Auflistung kann ein Fehler hinzugefügt werden.  
  
-   Eine SQL-SELECT-Anweisung. Das geöffnete **Datensatz** -Objekt stellt die einzelne Zeile dar, die durch das Ausführen des Inhalts der Zeichenfolge zurückgegeben wird. Wenn die Ergebnisse mehr als eine einzelne Zeile enthalten, wird der Inhalt der ersten Zeile in den Datensatz eingefügt, und der **Fehler** Auflistung kann ein Fehler hinzugefügt werden.  
  
-   Ein Tabellenname.  
  
 Wenn das **Daten Satz** Objekt eine Entität darstellt, auf die mit einer URL nicht zugegriffen werden kann (z. b. eine Zeile eines **Recordsets** , das von einer Datenbank abgeleitet wurde), sind die Werte der Eigenschaft " [parametriurl](../../../ado/reference/ado-api/parenturl-property-ado.md) " und des Felds, auf das mit der **adRecordURL** -Konstante zugegriffen wird, NULL.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Open-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open-Methode (ADO-Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open-Methode (ADO-Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema-Methode](../../../ado/reference/ado-api/openschema-method.md)
