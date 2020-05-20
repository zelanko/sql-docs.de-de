---
title: Open-Methode (ADO-Stream) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_Open
- _Stream::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: d26f48fb-904e-4932-a245-3b4332ca1600
author: rothja
ms.author: jroth
ms.openlocfilehash: d59fcbbd7edea7ac87b2c080d27160cb98732759
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762158"
---
# <a name="open-method-ado-stream"></a>Open-Methode (ADO-Datenstrom)
Öffnet ein [Stream](../../../ado/reference/ado-api/stream-object-ado.md) -Objekt, um Datenströme von Binär-oder Textdaten zu bearbeiten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.Open Source, Mode , OpenOptions, UserName, Password  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Dies ist optional. Ein **Variant** -Wert, der die Datenquelle für den Daten **Strom**angibt. Die *Quelle* kann eine absolute URL Zeichenfolge enthalten, die auf einen vorhandenen Knoten in einer bekannten Struktur verweist, wie z. b. eine e-Mail oder ein Dateisystem. Eine URL sollte mithilfe des URL-Schlüssel Worts ("URL =*Schema*://*Server* / *Ordner*") angegeben werden. Alternativ kann die *Quelle* einen Verweis auf ein bereits geöffnetes [Daten Satz](../../../ado/reference/ado-api/record-object-ado.md) Objekt enthalten, das den dem **Datensatz**zugeordneten Standardstream öffnet. Wenn *Source* nicht angegeben wird, wird ein **Stream** instanziiert und geöffnet, der standardmäßig keiner zugrunde liegenden Quelle zugeordnet ist. Weitere Informationen zu URL-Schemas und den zugehörigen Anbietern finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 *Mode*  
 Dies ist optional. Ein [connectmodeenum](../../../ado/reference/ado-api/connectmodeenum.md) -Wert, der den Zugriffsmodus für den resultierenden **Stream** angibt (z. b. Lese-/Schreibzugriff oder schreibgeschützt). Der Standardwert ist **adModeUnknown**. Weitere Informationen zu Zugriffs Modi finden Sie unter der [Mode](../../../ado/reference/ado-api/mode-property-ado.md) -Eigenschaft. Wenn der- *Modus* nicht angegeben wird, wird er vom Quell Objekt geerbt. Wenn der Quell **Daten Satz** z. b. im schreibgeschützten Modus geöffnet ist, wird der **Stream** standardmäßig auch im schreibgeschützten Modus geöffnet.  
  
 *OpenOptions*  
 Dies ist optional. Ein [StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md) -Wert. Der Standardwert ist " **adopendstreamunspezifiziert**".  
  
 *User*  
 Dies ist optional. Ein **Zeichen** folgen Wert, der die Benutzeridentifikation enthält, die bei Bedarf auf das **Stream** -Objekt zugreift.  
  
 *Kennwort*  
 Dies ist optional. Ein **Zeichen** folgen Wert, der das Kennwort enthält, das bei Bedarf auf das **Stream** -Objekt zugreift.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein **Datensatz** -Objekt als Quellparameter übergeben wird, werden die Parameter " *UserID* " und " *Password* " nicht verwendet, da der Zugriff auf das **Daten Satz** Objekt bereits verfügbar ist. Entsprechend wird der [Modus](../../../ado/reference/ado-api/mode-property-ado.md) des **Datensatz** -Objekts an das **Stream** -Objekt übertragen. Wenn *Source* nicht angegeben wird, enthält der geöffnete **Stream** keine Daten und hat die [Größe](../../../ado/reference/ado-api/size-property-ado-stream.md) 0 (null). Um den Verlust von Daten zu vermeiden, die in diesen **Stream** geschrieben werden, wenn der **Stream** geschlossen wird, speichern Sie den **Stream** mit den [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) -oder [savedefile](../../../ado/reference/ado-api/savetofile-method.md) -Methoden, oder speichern Sie ihn an einem anderen Speicherort.  
  
 Der Wert *openoptions* von **adopenstreamfromrecord** identifiziert den Inhalt des *Quell* Parameters als bereits geöffnetes **Daten Satz** Objekt. Standardmäßig wird *Source* als URL behandelt, die direkt auf einen Knoten in einer Baumstruktur verweist, z. b. auf eine Datei. Der Standarddaten Strom, der diesem Knoten zugeordnet ist, wird geöffnet.  
  
 Obwohl der **Stream** nicht geöffnet ist, ist es möglich, alle schreibgeschützten Eigenschaften des **Streams**zu lesen. Wenn ein Daten **Strom** asynchron geöffnet wird, werden alle nachfolgenden Vorgänge (außer Überprüfen des [Zustands](../../../ado/reference/ado-api/state-property-ado.md) und anderer Schreib geschützter Eigenschaften) blockiert, bis der **Öffnungs** Vorgang abgeschlossen ist.  
  
 Zusätzlich zu den zuvor erläuterten Optionen können Sie, indem Sie keine *Quelle*angeben, eine Instanz eines **Stream** -Objekts im Arbeitsspeicher erstellen, ohne es einer zugrunde liegenden Quelle zuzuordnen. Sie können dem Stream dynamisch Daten hinzufügen, indem Sie Binär-oder Textdaten mit [Write](../../../ado/reference/ado-api/write-method.md) oder [WRITETEXT](../../../ado/reference/ado-api/writetext-method.md)in den **Stream** schreiben oder indem Sie Daten aus einer Datei mit [LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md)laden.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Open-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open-Methode (ADO-Datensatz)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open-Methode (ADO-Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [OpenSchema-Methode](../../../ado/reference/ado-api/openschema-method.md)   
 [SaveToFile-Methode](../../../ado/reference/ado-api/savetofile-method.md)
