---
description: Open-Methode (ADO Record)
title: Open-Methode (ADO-Datensatz) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1ad606821e423892d49feb49a0920c7aea9056aa
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990341"
---
# <a name="open-method-ado-record"></a>Open-Methode (ADO Record)
Öffnet ein vorhandenes [Daten Satz](./record-object-ado.md) Objekt oder erstellt ein neues Element, das durch den **Datensatz**dargestellt wird, z. b. eine Datei oder ein Verzeichnis.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Optional. Eine **Variante** , die die URL der Entität darstellt, die durch dieses **Daten Satz** Objekt dargestellt werden soll, einen **Befehl**, ein offenes [Recordset](./recordset-object-ado.md) oder ein anderes **Datensatz** -Objekt, eine Zeichenfolge, die eine SQL-SELECT-Anweisung oder einen Tabellennamen enthält.  
  
 *ActiveConnection*  
 Optional. Eine **Variante** , die die Verbindungs Zeichenfolge oder das geöffnete [Verbindungs](./connection-object-ado.md) Objekt darstellt.  
  
 *Mode*  
 Optional. Ein [connectmodeenum](./connectmodeenum.md) -Wert, der den Zugriffsmodus für das resultierende **Datensatz** -Objekt angibt. Der Standardwert ist **adModeUnknown**.  
  
 *"Kreateoptions"*  
 Optional. Ein [recordkreateoptionsenum](./recordcreateoptionsenum.md) -Wert, der angibt, ob eine vorhandene Datei oder ein vorhandenes Verzeichnis geöffnet werden soll, oder ob eine neue Datei oder ein neues Verzeichnis erstellt werden soll. Der Standardwert ist " **adfailif NotExists**". Wenn der Standardwert festgelegt ist, wird der Zugriffsmodus aus der [Mode](./mode-property-ado.md) -Eigenschaft abgerufen. Dieser Parameter wird ignoriert, wenn der *Quell* Parameter keine URL enthält.  
  
 *Optionen*  
 Optional. Ein [recordopenoptionsenum](./recordopenoptionsenum.md) -Wert, der Optionen zum Öffnen des **Datensatzes**angibt. Der Standardwert ist " **adopendrecordunspezifiziert**". Diese Werte können kombiniert werden.  
  
 *UserName*  
 Optional. Ein **Zeichen** folgen Wert, der die Benutzer-ID enthält, die, falls erforderlich, den Zugriff auf die *Quelle*autorisiert.  
  
 *Kennwort*  
 Optional. Ein **Zeichen** folgen Wert, der das Kennwort enthält, das bei Bedarf den *Benutzernamen*überprüft.  
  
## <a name="remarks"></a>Bemerkungen  
 Die *Quelle* kann Folgendes sein:  
  
-   Eine URL. Wenn das Protokoll für die URL http lautet, wird standardmäßig der Internet Anbieter aufgerufen. , Wenn die URL auf einen Knoten verweist, der ein ausführbares Skript enthält (z. b.). ASP-Seite). Standardmäßig wird ein **Datensatz** geöffnet, der die Quelle anstelle des ausgeführten Inhalts enthält. Verwenden Sie das *options* -Argument, um dieses Verhalten zu ändern.  
  
-   Ein **Daten Satz** Objekt. Ein **Daten Satz** Objekt, das aus einem anderen **Datensatz** geöffnet wird, Klonen das ursprüngliche **Datensatz** -Objekt.  
  
-   Ein **Command** -Objekt. Das geöffnete **Datensatz** -Objekt stellt die einzelne Zeile dar, die durch Ausführen des **Befehls**zurückgegeben wird. Wenn die Ergebnisse mehr als eine einzelne Zeile enthalten, wird der Inhalt der ersten Zeile in den Datensatz eingefügt, und der **Fehler** Auflistung kann ein Fehler hinzugefügt werden.  
  
-   Eine SQL-SELECT-Anweisung. Das geöffnete **Datensatz** -Objekt stellt die einzelne Zeile dar, die durch das Ausführen des Inhalts der Zeichenfolge zurückgegeben wird. Wenn die Ergebnisse mehr als eine einzelne Zeile enthalten, wird der Inhalt der ersten Zeile in den Datensatz eingefügt, und der **Fehler** Auflistung kann ein Fehler hinzugefügt werden.  
  
-   Ein Tabellenname.  
  
 Wenn das **Daten Satz** Objekt eine Entität darstellt, auf die mit einer URL nicht zugegriffen werden kann (z. b. eine Zeile eines **Recordsets** , das von einer Datenbank abgeleitet wurde), sind die Werte der Eigenschaft " [parametriurl](./parenturl-property-ado.md) " und des Felds, auf das mit der **adRecordURL** -Konstante zugegriffen wird, NULL.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](./record-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Open-Methode (ADO-Verbindung)](./open-method-ado-connection.md)   
 [Open-Methode (ADO-Recordset)](./open-method-ado-recordset.md)   
 [Open-Methode (ADO-Stream)](./open-method-ado-stream.md)   
 [OpenSchema-Methode](./openschema-method.md)