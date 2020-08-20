---
description: Microsoft-Daten Strukturierungs Dienst für OLE DB (ADO-Dienstanbieter)
title: Microsoft-Daten Strukturierungs Dienst für OLE DB (ADO-Dienstanbieter) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping service for OLE DB
- data shaping service for OLE DB [ADO]
ms.assetid: 523009ce-e01b-4e2d-a7df-816d7688aff0
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c61e40220b99bd68c92e2651d58ea13ee10be29
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454102"
---
# <a name="microsoft-data-shaping-service-for-ole-db-overview"></a>Übersicht über den Microsoft-Daten Strukturierungs Dienst für OLE DB
> [!IMPORTANT]
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Stattdessen sollten Anwendungen XML verwenden.

 Der Microsoft-Daten Strukturierungs Dienst für OLE DB Dienstanbieter unterstützt das Erstellen hierarchischer (geformter) [Recordsetobjekte](../../../ado/reference/ado-api/recordset-object-ado.md) von einem Datenanbieter.

## <a name="provider-keyword"></a>Provider-Schlüsselwort
 Um den Daten Strukturierungs Dienst für OLE DB aufzurufen, geben Sie das folgende Schlüsselwort und den Wert in der Verbindungs Zeichenfolge an.

```vb
"Provider=MSDataShape"
```

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Wenn dieser Dienstanbieter aufgerufen wird, werden die folgenden dynamischen Eigenschaften der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung des[Connection](../../../ado/reference/ado-api/connection-object-ado.md) -Objekts hinzugefügt.

|Name der dynamischen Eigenschaft|Beschreibung|
|---------------------------|-----------------|
|**Eindeutige neushape-Namen**|Gibt an, ob **Recordset** -Objekte mit doppelten Werten für die Eigenschaften von **Reshape-Namen** zulässig sind. Wenn diese dynamische Eigenschaft auf **true** festgelegt ist und ein neues **Recordset** mit dem gleichen benutzerdefinierten umstrukturieren-Namen wie ein vorhandenes **Recordset**erstellt wird, wird der umstrukturieren-Name des neuen **Recordset** -Objekts geändert, um ihn eindeutig zu machen. Wenn diese Eigenschaft auf " **false** " festgelegt ist und ein neues **Recordset** mit dem gleichen benutzerdefinierten Namen der erneuten Form wie das vorhandene **Recordset**erstellt wird, haben beide **Recordset** -Objekte denselben umstrukturieren-Namen. Daher kann keines der **Recordsets** umgestaltet werden, solange beide Recordsets vorhanden sind.<br /><br /> Der Standardwert der-Eigenschaft ist **false**.|
|**Datenanbieter**|Gibt den Namen des Anbieters an, der die zu formatierender Zeilen bereitstellt. Dieser Wert kann "None" lauten, wenn ein Anbieter nicht zum Bereitstellen von Zeilen verwendet wird.|

 Sie können auch beschreibbare dynamische Eigenschaften festlegen, indem Sie Ihre Namen als Schlüsselwörter in der Verbindungs Zeichenfolge angeben. Legen Sie z. b. in Microsoft Visual Basic die **Datenanbieter** dynamische Eigenschaft auf "MSDASQL" fest, indem Sie Folgendes angeben:

```vb
Dim cn as New ADODB.Connection
cn.Open "Provider=MSDataShape;Data Provider=MSDASQL"
```

 Sie können auch eine dynamische Eigenschaft festlegen oder abrufen, indem Sie Ihren Namen als Index für die [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Eigenschaft angeben. Im folgenden Codebeispiel wird z. b. der aktuelle Wert der dynamischen Eigenschaft **Datenanbieter** abgerufen und ausgegeben. Anschließend wird ein neuer Wert festgelegt, wenn CN. "DataProvider" wurde auf "MSDataShape" (entweder direkt oder indirekt über die Verbindungs Zeichenfolge) festgelegt, und die Verbindung wurde nicht geöffnet:

```vb
Debug.Print cn.Properties("Data Provider")
cn.Properties("Data Provider") = "MSDASQL"
```

> [!NOTE]
>  Die dynamische Eigenschaft ( **Datenanbieter**) kann nur für ein ungeöffnetes **Verbindungs** Objekt festgelegt werden. Nachdem die Verbindung geöffnet wurde, wird die **Datenanbieter** -Eigenschaft schreibgeschützt.

 Weitere Informationen zur Daten Strukturierung finden Sie unter Strukturieren von [Daten](../../../ado/guide/data/data-shaping-overview.md).

## <a name="see-also"></a>Weitere Informationen
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
