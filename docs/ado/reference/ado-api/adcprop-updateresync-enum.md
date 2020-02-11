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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 82a5473a68303d429794d8b98c4e91293e4e30cc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921406"
---
# <a name="adcprop_updateresync_enum"></a>ADCPROP_UPDATERESYNC_ENUM
Gibt an, ob auf die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Methode ein impliziter Vorgang zum [erneuten Synchronisieren](../../../ado/reference/ado-api/resync-method.md) der Methode folgt, und wenn ja, der Gültigkeitsbereich dieses Vorgangs.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adresynrufe**|15|Ruft **Resync** mit dem kombinierten Wert aller anderen ADCPROP_UPDATERESYNC_ENUM Member auf.|  
|**adresyncautoincrement**|1|Default. Versucht, den neuen Identitäts Wert für Spalten abzurufen, die von der Datenquelle automatisch inkrementiert oder generiert werden, z. b. die automatischen oder Microsoft SQL Server Identitäts Spalten von Microsoft Jet.|  
|**adresyncconflicts**|2|Ruft die **erneute Synchronisierung** für alle Zeilen auf, bei denen der Aktualisierungs-oder Löschvorgang aufgrund eines Parallelitäts Konflikts fehlgeschlagen ist.|  
|**adresyncinserts**|8|Ruft die **erneute Synchronisierung** für alle erfolgreich eingefügten Zeilen auf. AutoIncrement-Spaltenwerte werden jedoch nicht neu synchronisiert. Stattdessen wird der Inhalt der neu eingefügten Zeilen basierend auf dem vorhandenen Primärschlüssel Wert neu synchronisiert. Wenn der Primärschlüssel ein AutoIncrement-Wert ist, wird der Inhalt der beabsichtigten Zeile von **Resync** nicht abgerufen. Zum automatischen erhöhen der AUTOINCREMENT-Primärschlüssel Werte, nennen Sie **UpdateBatch** mit dem kombinierten Wert **adresyncautoincrement** + **adresyncinserts**.|  
|**adresyncnone**|0|Die **erneute Synchronisierung**wird nicht aufgerufen.|  
|**adresyncupdates**|4|Ruft die **erneute Synchronisierung** für alle erfolgreich aktualisierten Zeilen auf.|  
  
## <a name="applies-to"></a>Gilt für  
 [Update Resync – dynamische Eigenschaft (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
