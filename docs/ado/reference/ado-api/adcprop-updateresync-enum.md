---
title: ADCPROP_UPDATERESYNC_ENUM | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords:
- ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
author: rothja
ms.author: jroth
ms.openlocfilehash: d27169aa9da35f84a1d91985f7f2d1a41035a100
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760706"
---
# <a name="adcprop_updateresync_enum"></a>ADCPROP_UPDATERESYNC_ENUM
Gibt an, ob auf die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Methode ein impliziter Vorgang zum [erneuten Synchronisieren](../../../ado/reference/ado-api/resync-method.md) der Methode folgt, und wenn ja, der Gültigkeitsbereich dieses Vorgangs.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adresynrufe**|15|Ruft **Resync** mit dem kombinierten Wert aller anderen ADCPROP_UPDATERESYNC_ENUM Member auf.|  
|**adresyncautoincrement**|1|Standard. Versucht, den neuen Identitäts Wert für Spalten abzurufen, die von der Datenquelle automatisch inkrementiert oder generiert werden, z. b. die automatischen oder Microsoft SQL Server Identitäts Spalten von Microsoft Jet.|  
|**adresyncconflicts**|2|Ruft die **erneute Synchronisierung** für alle Zeilen auf, bei denen der Aktualisierungs-oder Löschvorgang aufgrund eines Parallelitäts Konflikts fehlgeschlagen ist.|  
|**adresyncinserts**|8|Ruft die **erneute Synchronisierung** für alle erfolgreich eingefügten Zeilen auf. AutoIncrement-Spaltenwerte werden jedoch nicht neu synchronisiert. Stattdessen wird der Inhalt der neu eingefügten Zeilen basierend auf dem vorhandenen Primärschlüssel Wert neu synchronisiert. Wenn der Primärschlüssel ein AutoIncrement-Wert ist, wird der Inhalt der beabsichtigten Zeile von **Resync** nicht abgerufen. Zum automatischen erhöhen der AUTOINCREMENT-Primärschlüssel Werte, nennen Sie **UpdateBatch** mit dem kombinierten Wert **adresyncautoincrement**  +  **adresyncinserts**.|  
|**adresyncnone**|0|Die **erneute Synchronisierung**wird nicht aufgerufen.|  
|**adresyncupdates**|4|Ruft die **erneute Synchronisierung** für alle erfolgreich aktualisierten Zeilen auf.|  
  
## <a name="applies-to"></a>Gilt für  
 [Update Resync – dynamische Eigenschaft (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
