---
title: Open-Methode (ADO Stream) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6549fd10b173a8e133c941ea4315634badb3f35f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917835"
---
# <a name="open-method-ado-stream"></a>Open-Methode (ADO-Datenstrom)
Öffnet eine [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt zum Bearbeiten von binären Vergleich oder einen Datenströme.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.Open Source, Mode , OpenOptions, UserName, Password  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Optional. Ein **Variant** Wert, der angibt, die Quelle der Daten für die **Stream**. *Quelle* darf eine absolute URL-Zeichenfolge, die auf einen vorhandenen Knoten in einer bekannten Baumstruktur, wie z. B. eine E-mail oder Datei verweist. Es sollte eine URL mit dem URL-Schlüsselwort angegeben werden ("URL =*Schema*://*Server*/*Ordner*"). Alternativ *Quelle* möglicherweise enthalten einen Verweis auf ein bereits geöffnetes [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekt, das den Standarddatenstrom zugeordneten öffnet die **Datensatz**. Wenn *Quelle* nicht angegeben ist, eine **Stream** instanziiert und geöffnet, ohne zugrunde liegende Quelle standardmäßig zugeordnet ist. Weitere Informationen zu URL-Schemas und zugeordneten Anbietern, finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 *Mode*  
 Optional. Ein [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) Wert, der angibt, den den Zugriffsmodus für die resultierenden **Stream** (z. B. Lese-/Schreibzugriff oder schreibgeschützt). Standardwert ist **AdModeUnknown**. Finden Sie unter den [Modus](../../../ado/reference/ado-api/mode-property-ado.md) -Eigenschaft für Weitere Informationen zu Access-Modi. Wenn *Modus* nicht angegeben ist, wird es von dem Quellobjekt geerbt. Z. B. wenn die Quelle **Datensatz** im schreibgeschützten Modus geöffnet ist die **Stream** wird standardmäßig auch im schreibgeschützten Modus geöffnet werden.  
  
 *OpenOptions*  
 Optional. Ein [StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md) Wert. Standardwert ist **AdOpenStreamUnspecified**.  
  
 *UserName*  
 Dies ist optional. Ein **Zeichenfolge** Wert, der die Benutzer-ID, die enthält, wenn es erforderlich ist, greift auf, die **Stream** Objekt.  
  
 *Kennwort*  
 Dies ist optional. Ein **Zeichenfolge** Wert, der das Kennwort, die enthält, wenn es erforderlich ist, greift auf, die **Stream** Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine **Datensatz** Objekt wird als der Quellparameter übergeben die *"UserID"* und *Kennwort* Parameter werden nicht verwendet werden, da Zugriff auf die **Datensatz** Objekt ist bereits verfügbar. Auf ähnliche Weise die [Modus](../../../ado/reference/ado-api/mode-property-ado.md) von der **Datensatz** Objekt wird zum Übertragen der **Stream** Objekt. Wenn *Quelle* nicht angegeben ist, die **Stream** geöffnet enthält keine Daten und verfügt über eine [Größe](../../../ado/reference/ado-api/size-property-ado-stream.md) von 0 (null). Um zu vermeiden, Verlust von Daten, die in diese geschrieben werden **Stream** beim der **Stream** ist geschlossen, Speichern der **Stream** mit der [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) oder [ SaveToFile](../../../ado/reference/ado-api/savetofile-method.md) Methoden, oder auf einem anderen Speicherort speichern.  
  
 Ein *OpenOptions* Wert **AdOpenStreamFromRecord** identifiziert den Inhalt des der *Quelle* Parameter einen Parameter eines bereits geöffneten **Datensatz**Objekt. Das Standardverhalten ist, behandeln *Quelle* als eine URL, die direkt auf einen Knoten in einer Baumstruktur, z. B. eine Datei verweist. Die diesem Knoten zugeordnete Standarddatenstrom wird geöffnet.  
  
 Während der **Stream** ist nicht geöffnet ist, es ist möglich, alle schreibgeschützten Eigenschaften des Lesen der **Stream**. Wenn eine **Stream** ist asynchron, alle nachfolgenden Vorgänge geöffnet (außer dem Überprüfen der [Zustand](../../../ado/reference/ado-api/state-property-ado.md) und andere Eigenschaften schreibgeschützt) werden blockiert, bis die **öffnen** Vorgang wird durchgeführt.  
  
 Zusätzlich zu den Optionen, die zuvor erläutert wurden, nicht angegeben *Quelle*, Sie können eine Instanz von erstellen eine **Stream** Objekt im Arbeitsspeicher ohne Zuordnung zu einer zugrunde liegenden Datenquelle. Sie können Daten in den Stream dynamisch hinzufügen, durch das Schreiben von Binär oder Text-Daten auf den **Stream** mit [schreiben](../../../ado/reference/ado-api/write-method.md) oder [WriteText](../../../ado/reference/ado-api/writetext-method.md), oder durch das Laden von Daten aus einer Datei mit [ LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Open Sie-Methode (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open Sie-Methode (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open Sie-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [OpenSchema-Methode](../../../ado/reference/ado-api/openschema-method.md)   
 [SaveToFile-Methode](../../../ado/reference/ado-api/savetofile-method.md)
