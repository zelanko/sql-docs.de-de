---
description: Übersicht über Microsoft OLE DB-Anbieter für Oracle
title: Microsoft OLE DB-Anbieter für Oracle | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB provider for Oracle
- OLE DB provider for Oracle [ADO]
- Oracle provider [ADO]
ms.assetid: 44fae9dd-5585-4cd6-8bbd-3248a78931b4
author: rothja
ms.author: jroth
ms.openlocfilehash: d8da5e3d5de1ac0ee3f3dfa1b0f989679af3cd1d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991011"
---
# <a name="microsoft-ole-db-provider-for-oracle-overview"></a>Übersicht über Microsoft OLE DB-Anbieter für Oracle
> [!IMPORTANT]
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den OLE DB-Anbieter von Oracle.

 Der Microsoft OLE DB-Anbieter für Oracle ermöglicht ADO den Zugriff auf Oracle-Datenbanken.

## <a name="connection-string-parameters"></a>Parameter der Verbindungszeichenfolge
 Legen Sie das *Provider* -Argument der [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) -Eigenschaft auf fest, um eine Verbindung mit diesem Anbieter herzustellen:

```vb
MSDAORA
```

 Wenn Sie die [Provider](../../reference/ado-api/provider-property-ado.md) -Eigenschaft lesen, wird auch diese Zeichenfolge zurückgegeben.

 Wenn eine Join-Abfrage mit einem Keyset-oder Dynamic-Cursor in einer Oracle-Datenbank ausgeführt wird, tritt ein Fehler auf. Oracle unterstützt nur einen statischen schreibgeschützten Cursor.

## <a name="typical-connection-string"></a>Typische Verbindungs Zeichenfolge
 Eine typische Verbindungs Zeichenfolge für diesen Anbieter lautet:

```vb
"Provider=MSDAORA;Data Source=serverName;User ID=MyUserID; Password=MyPassword;"
```

 Die Zeichenfolge besteht aus folgenden Schlüsselwörtern:

|Schlüsselwort|Beschreibung|
|-------------|-----------------|
|**Anbieter**|Gibt den OLE DB Anbieter für Oracle an.|
|**Data Source**|Gibt den Namen eines Servers an.|
|**Benutzer-ID**|Gibt den Benutzernamen an.|
|**Kennwort**|Gibt das Benutzer Kennwort an.|

> [!NOTE]
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unterstützt, sollten Sie in der Verbindungs Zeichenfolge **Trusted_Connection = yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort angeben.

## <a name="provider-specific-connection-parameters"></a>Anbieterspezifische Verbindungsparameter
 Der Anbieter unterstützt mehrere Anbieterspezifische Verbindungsparameter zusätzlich zu den von ADO definierten Verbindungsparametern. Wie bei den ADO-Verbindungs Eigenschaften können diese anbieterspezifischen Eigenschaften über die [Properties](../../reference/ado-api/properties-collection-ado.md) -Auflistung einer [Verbindung](../../reference/ado-api/connection-object-ado.md) oder als Teil von **ConnectionString**festgelegt werden.

 Diese Parameter werden in der [OLE DB Programmierer-Referenz](/previous-versions/windows/desktop/ms713643(v=vs.85))vollständig beschrieben. Der [dynamische ADO-Eigenschafts Index](../../reference/ado-api/ado-dynamic-property-index.md) bietet einen Querverweis zwischen diesen Parameternamen und den entsprechenden OLE DB Eigenschaften.

|Parameter|Beschreibung|
|---------------|-----------------|
|**Fensterhandle**|Gibt das Fenster Handle an, das verwendet werden soll, um zusätzliche Informationen einzugeben.|
|**Locale Identifier**|Gibt eine eindeutige 32-Bit-Nummer an (z. b. 1033), die Einstellungen im Zusammenhang mit der Sprache des Benutzers angibt. Diese Einstellungen geben an, wie Datumsangaben und Uhrzeiten formatiert, Elemente alphabetisch sortiert, Zeichen folgen verglichen werden usw.|
|**OLE DB Dienste**|Gibt eine Bitmaske an, die OLE DB Dienste angibt, die aktiviert oder deaktiviert werden sollen.|
|**Eingabeaufforderung**|Gibt an, ob der Benutzer beim Herstellen einer Verbindung aufgefordert werden soll.|
|**Extended Properties**|Eine Zeichenfolge, die anbieterspezifische, erweiterte Verbindungsinformationen enthält. Verwenden Sie diese Eigenschaft nur für anbieterspezifische Verbindungsinformationen, die nicht über den-Eigenschafts Mechanismus beschrieben werden können.|

## <a name="see-also"></a>Weitere Informationen
 [ConnectionString-Eigenschaft (](../../reference/ado-api/connectionstring-property-ado.md) [ADO)-](../../reference/ado-api/provider-property-ado.md) Objekt (ADO)- [Recordset-Objekt (](../../reference/ado-api/recordset-object-ado.md) ADO)