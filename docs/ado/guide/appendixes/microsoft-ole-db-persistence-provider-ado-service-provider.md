---
title: Microsoft OLE DB-Persistenzanbieter (ADO-Dienstanbieter) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2bd341a3af2d1fdb076312b4c0993184fb4fae39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926767"
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Übersicht über den Microsoft OLE DB Persistenz
Mit dem Microsoft OLE DB-Persistenzanbieter können Sie ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt in einer Datei speichern und das **Recordset** -Objekt später aus der Datei wiederherstellen. Schema Informationen, Daten und ausstehende Änderungen werden beibehalten.

 Sie können das **Recordset** entweder im proprietären Format von Advanced Data Table Gram (ADTG) oder im Open Extensible Markup Language-Format (XML) speichern.

## <a name="provider-keyword"></a>Provider-Schlüsselwort
 Um diesen Anbieter aufzurufen, geben Sie das folgende Schlüsselwort und den Wert in der Verbindungs Zeichenfolge an.

```vb
"Provider=MSPersist"
```

## <a name="errors"></a>Errors
 Die folgenden Fehler, die von diesem Anbieter ausgegeben werden, können in der Anwendung erkannt werden.

|Dauerhaft|BESCHREIBUNG|
|--------------|-----------------|
|E_BADSTREAM|Die geöffnete Datei weist kein gültiges Format auf (das heißt, das Format ist nicht ADTG oder XML).|
|E_CANTPERSISTROWSET|Das gespeicherte **Recordset** -Objekt verfügt über Eigenschaften, die die Speicherung verhindern.|

## <a name="remarks"></a>Bemerkungen
 Der Microsoft OLE DB-Persistenzanbieter macht keine dynamischen Eigenschaften verfügbar.

 Derzeit können nur parametrisierte hierarchische Recordsetobjekte gespeichert werden. ****

 Weitere Informationen zum persistenten Speichern von **recordsetobjekten** finden Sie unter [Recordset-Persistenz](../../../ado/guide/data/more-about-recordset-persistence.md).

 Wenn ein Datenstrom zum Öffnen eines **Recordsets** verwendet wird, dürfen keine anderen Parameter als der *Quell* Parameter der **Open** -Methode angegeben werden.

## <a name="see-also"></a>Weitere Informationen
[Microsoft OLE DB-Persistenzanbieter (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)
