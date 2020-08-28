---
description: Open-Methode (ADO-Datenstrom)
title: Open-Methode (ADO-Stream) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: ef760da2bad97cec017c7a58735200be1a14f85d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990321"
---
# <a name="open-method-ado-stream"></a>Open-Methode (ADO-Datenstrom)
Öffnet ein [Stream](./stream-object-ado.md) -Objekt, um Datenströme von Binär-oder Textdaten zu bearbeiten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.Open Source, Mode , OpenOptions, UserName, Password  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Optional. Ein **Variant** -Wert, der die Datenquelle für den Daten **Strom**angibt. Die *Quelle* kann eine absolute URL Zeichenfolge enthalten, die auf einen vorhandenen Knoten in einer bekannten Struktur verweist, wie z. b. eine e-Mail oder ein Dateisystem. Eine URL sollte mithilfe des URL-Schlüssel Worts ("URL =*Schema*://*Server* / *Ordner*") angegeben werden. Alternativ kann die *Quelle* einen Verweis auf ein bereits geöffnetes [Daten Satz](./record-object-ado.md) Objekt enthalten, das den dem **Datensatz**zugeordneten Standardstream öffnet. Wenn *Source* nicht angegeben wird, wird ein **Stream** instanziiert und geöffnet, der standardmäßig keiner zugrunde liegenden Quelle zugeordnet ist. Weitere Informationen zu URL-Schemas und den zugehörigen Anbietern finden Sie unter [absolute und relative URLs](../../guide/data/absolute-and-relative-urls.md).  
  
 *Mode*  
 Optional. Ein [connectmodeenum](./connectmodeenum.md) -Wert, der den Zugriffsmodus für den resultierenden **Stream** angibt (z. b. Lese-/Schreibzugriff oder schreibgeschützt). Der Standardwert ist **adModeUnknown**. Weitere Informationen zu Zugriffs Modi finden Sie unter der [Mode](./mode-property-ado.md) -Eigenschaft. Wenn der- *Modus* nicht angegeben wird, wird er vom Quell Objekt geerbt. Wenn der Quell **Daten Satz** z. b. im schreibgeschützten Modus geöffnet ist, wird der **Stream** standardmäßig auch im schreibgeschützten Modus geöffnet.  
  
 *OpenOptions*  
 Optional. Ein [StreamOpenOptionsEnum](./streamopenoptionsenum.md) -Wert. Der Standardwert ist " **adopendstreamunspezifiziert**".  
  
 *UserName*  
 Optional. Ein **Zeichen** folgen Wert, der die Benutzeridentifikation enthält, die bei Bedarf auf das **Stream** -Objekt zugreift.  
  
 *Kennwort*  
 Optional. Ein **Zeichen** folgen Wert, der das Kennwort enthält, das bei Bedarf auf das **Stream** -Objekt zugreift.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein **Datensatz** -Objekt als Quellparameter übergeben wird, werden die Parameter " *UserID* " und " *Password* " nicht verwendet, da der Zugriff auf das **Daten Satz** Objekt bereits verfügbar ist. Entsprechend wird der [Modus](./mode-property-ado.md) des **Datensatz** -Objekts an das **Stream** -Objekt übertragen. Wenn *Source* nicht angegeben wird, enthält der geöffnete **Stream** keine Daten und hat die [Größe](./size-property-ado-stream.md) 0 (null). Um den Verlust von Daten zu vermeiden, die in diesen **Stream** geschrieben werden, wenn der **Stream** geschlossen wird, speichern Sie den **Stream** mit den [CopyTo](./copyto-method-ado.md) -oder [savedefile](./savetofile-method.md) -Methoden, oder speichern Sie ihn an einem anderen Speicherort.  
  
 Der Wert *openoptions* von **adopenstreamfromrecord** identifiziert den Inhalt des *Quell* Parameters als bereits geöffnetes **Daten Satz** Objekt. Standardmäßig wird *Source* als URL behandelt, die direkt auf einen Knoten in einer Baumstruktur verweist, z. b. auf eine Datei. Der Standarddaten Strom, der diesem Knoten zugeordnet ist, wird geöffnet.  
  
 Obwohl der **Stream** nicht geöffnet ist, ist es möglich, alle schreibgeschützten Eigenschaften des **Streams**zu lesen. Wenn ein Daten **Strom** asynchron geöffnet wird, werden alle nachfolgenden Vorgänge (außer Überprüfen des [Zustands](./state-property-ado.md) und anderer Schreib geschützter Eigenschaften) blockiert, bis der **Öffnungs** Vorgang abgeschlossen ist.  
  
 Zusätzlich zu den zuvor erläuterten Optionen können Sie, indem Sie keine *Quelle*angeben, eine Instanz eines **Stream** -Objekts im Arbeitsspeicher erstellen, ohne es einer zugrunde liegenden Quelle zuzuordnen. Sie können dem Stream dynamisch Daten hinzufügen, indem Sie Binär-oder Textdaten mit [Write](./write-method.md) oder [WRITETEXT](./writetext-method.md)in den **Stream** schreiben oder indem Sie Daten aus einer Datei mit [LoadFromFile](./loadfromfile-method-ado.md)laden.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Open-Methode (ADO-Verbindung)](./open-method-ado-connection.md)   
 [Open-Methode (ADO-Datensatz)](./open-method-ado-record.md)   
 [Open-Methode (ADO-Recordset)](./open-method-ado-recordset.md)   
 [OpenSchema-Methode](./openschema-method.md)   
 [SaveToFile-Methode](./savetofile-method.md)