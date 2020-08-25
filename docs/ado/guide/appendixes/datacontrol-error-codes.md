---
description: Fehler Codes für DataControl-Objekte
title: DataControl-Fehler Codes | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4b145e538ea44d5f007f800f70df84b8eed0b116
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806660"
---
# <a name="datacontrol-object-error-codes"></a>Fehler Codes für DataControl-Objekte
In der folgenden Tabelle sind die [RDS aufgeführt. Fehlercodes des DataControl](../../reference/rds-api/datacontrol-object-rds.md) -Objekts. Die positive Dezimal Übersetzung der unteren zwei Bytes, die negative Dezimal Übersetzung des vollständigen Fehlercodes und die hexadezimalen Werte werden angezeigt.

|RDS. DataControl-Fehlercodes|Number|BESCHREIBUNG|
|---------------------------------|------------|-----------------|
|**IDS_AsyncPending**|4107-2146824175 0x800a1011|Der Vorgang kann nicht ausgeführt werden, während der asynchrone Vorgang aussteht.|
|**IDS_BadInlineTablegram**|4105-2146824183 0x800a1009|Ungültiges Inline-Tablegram.|
|**IDS_CantConnect**|4099-2146824189 0x800a1003|Verbindung mit Server nicht möglich.|
|**IDS_CantCreateObject**|4100-2146824188 0x800a1004|Das Geschäftsobjekt kann nicht erstellt werden.|
|**IDS_CantFindDataspace**|4102-2146824186 0x800a1006|Die DataSpace-Eigenschaft ist ungültig.|
|**IDS_CantInvokeMethod**|4101-2146824187 0x800a1005|Die Methode kann nicht für das Geschäftsobjekt aufgerufen werden.|
|**IDS_CrossDomainWarning**|4112-2146824170 0x800a1016|Diese Seite greift auf Daten in einer anderen Domäne zu. Möchten Sie dies zulassen? Um diese Meldung in Internet Explorer zu vermeiden, können Sie auf der Registerkarte **Sicherheit** des Dialog Felds **Internetoptionen** eine sichere Website zur Zone vertrauenswürdiger Sites hinzufügen.|
|**IDS_InvalidADCClientVersion**|4106-2146824176 0x800a1010|Ungültige RDS-Client Version, der Client ist neuer als der Server.|
|**IDS_INVALIDARG**|5376-2147019520 0x80071500|Mindestens ein Argument ist ungültig.|
|**IDS_InvalidBindings**|4097-2146824191 0x800a1001|Fehler in der Bindungs Eigenschaft.|
|**IDS_InvalidParam**|4110-2146824172 0x800a1014|Mindestens ein Argument ist ungültig.|
|**IDS_NOINTERFACE**|5377-2147019519 0x80071501|Eine solche Schnittstelle wird nicht unterstützt.|
|**IDS_NotReentrant**|4111-2146824171 0x800a1015|Die Anforderung kann nicht ausgeführt werden, solange der Ereignishandler noch verarbeitet wird.|
|**IDS_ObjectNotSafe**|4103-2146824185 0x800a1007|Die Sicherheitseinstellungen auf diesem Computer verbieten die Erstellung eines Geschäftsobjekts.|
|**IDS_RecordsetNotOpen**|4109-2146824173 0x800a1013|Das **Recordset** ist nicht geöffnet.|
|**IDS_ResetInvalidField**|4108-2146824174 0x800a1012|Die in **SortColumn** oder **FilterColumn** angegebene Spalte ist nicht vorhanden.|
|**IDS_RowsetNotUpdateable**|4104-2146824184 0x800a1008|Das Rowset ist nicht aktualisierbar.|
|**IDS_UnexpectedError**|4351-2146823937 0x800a10ff|Unerwarteter Fehler.|
|**IDS_UpdatesFailed**|4098-2146824190 0x800a1002|Die Datenbank kann nicht aktualisiert werden.|
|**IDS_URLMONNotFound**|4119-2146824169 0x800a1017|Die DataControl- **URL** -Eigenschaft erfordert, dass die Systemdatei Urlmon.dll ist, die nicht gefunden werden kann.|

## <a name="see-also"></a>Weitere Informationen
 [DataControl-Objekt (RDS)](../../reference/rds-api/datacontrol-object-rds.md)