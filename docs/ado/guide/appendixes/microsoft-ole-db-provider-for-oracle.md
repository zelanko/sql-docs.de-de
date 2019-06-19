---
title: Microsoft OLE DB-Anbieter für Oracle | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB provider for Oracle
- OLE DB provider for Oracle [ADO]
- Oracle provider [ADO]
ms.assetid: 44fae9dd-5585-4cd6-8bbd-3248a78931b4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6af8fcd665fdfe503eab5aec591419982d0d3958
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702715"
---
# <a name="microsoft-ole-db-provider-for-oracle-overview"></a>Microsoft OLE DB-Anbieter für Oracle (Übersicht)
> [!IMPORTANT]
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den Oracle OLE DB-Anbieter.

 Microsoft OLE DB-Anbieter für Oracle ermöglicht ADO auf Oracle-Datenbanken zugreifen.

## <a name="connection-string-parameters"></a>Parameter für Verbindungszeichenfolgen
 Legen Sie zum Verbinden mit diesem Anbieter die *Anbieter* Argument der ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) Eigenschaft:

```vb
MSDAORA
```

 Lesen der [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft auch dieser Zeichenfolge zurück.

 Wenn eine Join-Abfrage mit einem Keyset oder dynamic-Cursor in einer Oracle-Datenbank ausgeführt wird, tritt ein Fehler auf. Oracle unterstützt nur einen statischen nur-Lese Cursor.

## <a name="typical-connection-string"></a>Typische Verbindungszeichenfolge
 Eine typische Verbindungszeichenfolge für diesen Anbieter ist:

```vb
"Provider=MSDAORA;Data Source=serverName;User ID=MyUserID; Password=MyPassword;"
```

 Die Zeichenfolge, die dieser Schlüsselwörter besteht aus:

|Schlüsselwort|Description|
|-------------|-----------------|
|**Anbieter**|Gibt an, die OLE DB-Anbieter für Oracle.|
|**Data Source**|Gibt den Namen eines Servers.|
|**Benutzer-ID**|Gibt den Benutzernamen an.|
|**Kennwort**|Gibt das Kennwort des Benutzers an.|

> [!NOTE]
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben **Trusted_Connection = Yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort die Informationen in der Verbindungszeichenfolge.

## <a name="provider-specific-connection-parameters"></a>Anbieterspezifische-Verbindungsparameter
 Der Anbieter unterstützt mehrere Anbieter-spezifischen Verbindungsdaten Parameter zusätzlich zu den von ADO definiert. Wie mit den Eigenschaften der ADO-Verbindung diese Anbieter-spezifischen Eigenschaften können, über festgelegt werden die [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung von einer [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) oder als Teil der **"ConnectionString"** .

 Diese Parameter sind ausführlich erläutert, in der [OLE DB-Programmierreferenz](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8). Die [ADO dynamische Property-Index](../../../ado/reference/ado-api/ado-dynamic-property-index.md) bietet einen Querverweis zwischen diesen Parameternamen und den entsprechenden OLE DB-Eigenschaften.

|Parameter|Description|
|---------------|-----------------|
|**Das Fensterhandle**|Gibt das Fensterhandle verwenden, um zusätzliche Informationen aufzufordern.|
|**Locale Identifier**|Gibt eine eindeutige 32-Bit-Zahl (z. B. 1033), die angibt, Einstellungen, die im Zusammenhang mit der Sprache des Benutzers an. Diese Einstellungen angeben, wie Datums- und Uhrzeitangaben formatiert sind, Elemente alphabetisch sortiert sind, die Zeichenfolgen verglichen werden und so weiter.|
|**OLE DB-Diensten**|Gibt an, eine Bitmaske, die angibt, OLE DB-Dienste zum Aktivieren oder deaktivieren.|
|**Prompt**|Gibt an, ob der Benutzer aufgefordert, während eine Verbindung erstellt wird.|
|**Erweiterte Eigenschaften**|Eine Zeichenfolge mit anbieterspezifischen erweiterten Verbindungsinformationen. Verwenden Sie diese Eigenschaft nur für anbieterspezifische Verbindungsinformationen, die über den Eigenschaftenmechanismus kann nicht beschrieben werden.|

## <a name="see-also"></a>Siehe auch
 [ConnectionString-Eigenschaft (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [Provider-Eigenschaft (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
