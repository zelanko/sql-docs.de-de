---
title: Microsoft Data Shaping Service für OLE DB (ADO-Dienstanbieter) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46f48aa117c18bcc7af28cdf7c676cf195b553f6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62719752"
---
# <a name="microsoft-data-shaping-service-for-ole-db-overview"></a>Microsoft Data Shaping Service für OLE DB-Übersicht
> [!IMPORTANT]
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Stattdessen sollten Anwendungen XML verwenden.

 Der Microsoft Data Shaping Service für OLE DB-Service-Anbieter unterstützt die Erstellung von hierarchischen (strukturiert) [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekte von einem Datenanbieter.

## <a name="provider-keyword"></a>Anbieterschlüsselwort
 Um den Data Shaping Service für OLE DB aufzurufen, geben Sie das folgende Schlüsselwort und Wert in der Verbindungszeichenfolge ein.

```vb
"Provider=MSDataShape"
```

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Wenn diesem Dienstanbieter aufgerufen wird, werden die folgenden dynamischen Eigenschaften hinzugefügt, auf die [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung von der[Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt.

|Name der dynamischen Eigenschaft|Description|
|---------------------------|-----------------|
|**Eindeutige umformen Namen**|Gibt an, ob **Recordset** Objekte mit doppelten Werten für ihre **Reshape Name** Eigenschaften sind zulässig. Wenn diese dynamische Eigenschaft **"true"** und ein neues **Recordset** wird erstellt, mit demselben Namen wie eine vorhandene benutzerdefinierte umformen **Recordset**, klicken Sie dann die neue  **Recordset** umformen-Namen des Objekts wird geändert, um sie eindeutig zu machen. Wenn diese Eigenschaft **"false"** und ein neues **Recordset** wird erstellt, mit demselben Namen wie des vorhandenen benutzerdefinierten umformen **Recordset**, beide **Recordset**  Objekte weisen den gleichen umformen-Namen. Aus diesem Grund keine **Recordset** können umgeformt werden, solange beide Objekte vorhanden sind.<br /><br /> Der Standardwert der Eigenschaft ist **"false"**.|
|**Datenanbieter**|Gibt den Namen des Anbieters, die Zeilen zum Strukturieren bereitgestellt werden. Dieser Wert kann keine sein, wenn ein Anbieter nicht zum Bereitstellen von Zeilen verwendet wird.|

 Sie können auch beschreibbare dynamische Eigenschaften festlegen, durch deren Namen als Schlüsselwörter in der Verbindungszeichenfolge angeben. In Microsoft Visual Basic, z. B. Festlegen der **Datenanbieter** dynamische Eigenschaft auf "MSDASQL", indem Sie angeben:

```vb
Dim cn as New ADODB.Connection
cn.Open "Provider=MSDataShape;Data Provider=MSDASQL"
```

 Sie können auch festlegen oder Abrufen eine dynamische Eigenschaft durch Angabe seines Namens als Index für die [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Eigenschaft. Beispielsweise das folgende Codebeispiel ruft ab und gibt den aktuellen Wert des der **Datenanbieter** dynamische Eigenschaft, klicken Sie dann ein neuer Wert festgelegt, wenn Cn. "DataProvider" auf "MSDataShape" festgelegt wurde (entweder direkt oder indirekt über die Verbindungszeichenfolge) und die Verbindung nicht geöffnet wurde:

```vb
Debug.Print cn.Properties("Data Provider")
cn.Properties("Data Provider") = "MSDASQL"
```

> [!NOTE]
>  Der dynamische Eigenschaft **Datenanbieter**, können nur festgelegt, auf ein ungeöffnetes werden **Verbindung** Objekt. Nachdem die Verbindung geöffnet wird, die **Datenanbieter** Eigenschaft ist schreibgeschützt.

 Weitere Informationen zum Strukturieren von Daten, finden Sie unter [Datenstrukturierung](../../../ado/guide/data/data-shaping-overview.md).

## <a name="see-also"></a>Siehe auch
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
