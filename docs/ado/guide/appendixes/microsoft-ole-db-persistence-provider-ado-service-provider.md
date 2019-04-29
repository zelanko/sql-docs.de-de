---
title: Microsoft OLE DB-Persistenz-Provider (ADO-Dienstanbieter) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB persistence provider
- persistence provider [ADO]
- OLE DB persistence provider [ADO]
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2550e36f977be13e10865d4bd238c8508c542091
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63128517"
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Microsoft OLE DB-Persistenz-Anbieter (Übersicht)
Der Microsoft OLE DB-Persistenz-Provider ermöglicht Ihnen das Speichern einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt in eine Datei, und später wiederherstellen, die **Recordset** Objekt aus der Datei. Schemainformationen, die Daten, und ausstehende Änderungen werden beibehalten.

 Sie können speichern die **Recordset** in das proprietäre Advanced Data Table Gramm (ADTG) Format oder die offenen Extensible Markup Language (XML)-Format.

## <a name="provider-keyword"></a>Anbieterschlüsselwort
 Um diesen Anbieter aufzurufen, geben Sie das folgende Schlüsselwort und Wert in der Verbindungszeichenfolge ein.

```vb
"Provider=MSPersist"
```

## <a name="errors"></a>Fehler
 Die folgenden Fehler ausgegeben, die von diesem Anbieter können in der Anwendung erkannt werden.

|Konstante|Description|
|--------------|-----------------|
|E_BADSTREAM|Die Datei geöffnet wird kein gültigen Format ist (d. h. das Format ist nicht ADTG oder XML).|
|E_CANTPERSISTROWSET|Die **Recordset** gespeichertes Objekt verfügt über Eigenschaften, die verhindern, dass es gespeichert werden.|

## <a name="remarks"></a>Hinweise
 Der Microsoft OLE DB-Persistenz-Anbieter macht keine dynamischen Eigenschaften verfügbar.

 Derzeit nur parametrisierte hierarchische **Recordset** Objekte können nicht gespeichert werden.

 Weitere Informationen zum permanenten Speichern von **Recordset** Objekten finden Sie [Recordset-Beibehaltung](../../../ado/guide/data/more-about-recordset-persistence.md).

 Bei Verwendung ein Streams zum Öffnen einer **Recordset,** ohne Parameter nicht angegeben werden soll die *Quelle* Parameter der **öffnen** Methode.

## <a name="see-also"></a>Siehe auch
[Microsoft OLE DB-Persistenz-Provider (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)
