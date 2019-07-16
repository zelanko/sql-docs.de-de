---
title: DataControl-Fehlercodes | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], DataControl
- DataControl errors [ADO]
ms.assetid: 293df9d5-e1a2-406d-9107-07bf7cdc6f96
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b59f0f98122d37447e2e702304a31c44073bacfa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67926843"
---
# <a name="datacontrol-object-error-codes"></a>DataControl-Objekt-Fehlercodes
Die folgende Tabelle enthält die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt Fehlercodes. Die positive decimal Übersetzung der niedrigen zwei Bytes, die negative dezimale Übersetzung von der vollständigen Fehlercode und die Hexadezimalwerte werden angezeigt.

|RDS. DataControl-Fehlercodes|Number|Beschreibung|
|---------------------------------|------------|-----------------|
|**IDS_AsyncPending**|4107 -2146824175 0x800A1011|Vorgang kann nicht ausgeführt werden, während der asynchrone Vorgang aussteht.|
|**IDS_BadInlineTablegram**|4105 -2146824183 0x800A1009|Ungültiges Inline Tablegram.|
|**IDS_CantConnect**|4099-2146824189 0x800A1003|Kann keine Verbindung mit Server herstellen.|
|**IDS_CantCreateObject**|4100 -2146824188 0x800A1004|Business-Objekt kann nicht erstellt werden.|
|**IDS_CantFindDataspace**|4102 -2146824186 0x800A1006|DataSpace-Eigenschaft ist nicht gültig.|
|**IDS_CantInvokeMethod**|4101 -2146824187 0x800A1005|Methode kann nicht für Geschäftsobjekt aufgerufen werden.|
|**IDS_CrossDomainWarning**|4112-2146824170 0x800A1016|Auf dieser Seite auf die Daten in einer anderen Domäne zugreift. Möchten Sie dies zulassen? Um diese Nachricht in Internet Explorer zu vermeiden, können Sie eine sichere Website der Zone der vertrauenswürdigen Sites hinzufügen, auf die **Sicherheit** Registerkarte die **Internetoptionen** Dialogfeld.|
|**IDS_InvalidADCClientVersion**|4106-2146824176 0x800A1010|Ungültige Version in einer RDS-Client - ist der Client neuer als die Server.|
|**IDS_INVALIDARG**|5376-2147019520 0x80071500|Ein oder mehrere Argumente sind ungültig.|
|**IDS_InvalidBindings**|4097 -2146824191 0x800A1001|Fehler in der Bindings-Eigenschaft.|
|**IDS_InvalidParam**|4110-2146824172 0x800A1014|Ein oder mehrere Argumente sind ungültig.|
|**IDS_NOINTERFACE**|5377 -2147019519 0x80071501|Es wird keine Schnittstelle unterstützt.|
|**IDS_NotReentrant**|4111 -2146824171 0x800A1015|Anforderung kann nicht ausgeführt werden, während der Ereignishandler noch verarbeitet wird.|
|**IDS_ObjectNotSafe**|4103 -2146824185 0x800A1007|Die Sicherheitseinstellungen auf diesem Computer lassen die Erstellung von Business-Objekt.|
|**IDS_RecordsetNotOpen**|4109 -2146824173 0x800A1013|**Recordset** nicht geöffnet ist.|
|**IDS_ResetInvalidField**|4108 -2146824174 0x800A1012|Spalte, die im angegebenen **SortColumn** oder **FilterColumn** ist nicht vorhanden.|
|**IDS_RowsetNotUpdateable**|4104 -2146824184 0x800A1008|Das Rowset ist nicht aktualisierbar.|
|**IDS_UnexpectedError**|4351 -2146823937 0x800A10FF|Unerwarteter Fehler.|
|**IDS_UpdatesFailed**|4098-2146824190 0x800A1002|Datenbank kann nicht aktualisiert.|
|**IDS_URLMONNotFound**|4119-2146824169 0x800A1017|DataControl **URL** Eigenschaft erfordert die Systemprotokolldatei Urlmon.dll, die nicht gefunden werden kann.|

## <a name="see-also"></a>Siehe auch
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)
