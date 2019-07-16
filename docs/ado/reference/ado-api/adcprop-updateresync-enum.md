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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67921406"
---
# <a name="adcpropupdateresyncenum"></a>ADCPROP_UPDATERESYNC_ENUM
Gibt an, ob die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Methode einen impliziten folgt [Resync](../../../ado/reference/ado-api/resync-method.md) -Methodenvorgangs und wenn Ja, im Rahmen dieses Vorgangs.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|Ruft **Resync** mit der kombinierte Wert aller anderen ADCPROP_UPDATERESYNC_ENUM-Member.|  
|**adResyncAutoIncrement**|1|Standard. Versucht, den neuen Identitätswert für Spalten abzurufen, die automatisch erhöht oder von der Datenquelle, z. B. Microsoft Jet AutoNumber-Felder oder Microsoft SQL Server-Identitätsspalten generiert werden.|  
|**adResyncConflicts**|2|Ruft **Resync** für alle Zeilen in der Fehler bei der Update- oder Delete-Vorgang aufgrund eines Parallelitätskonflikts.|  
|**adResyncInserts**|8|Ruft **Resync** für alle erfolgreich eingefügten Zeilen. AutoIncrement-Spaltenwerte werden jedoch nicht neu synchronisiert. Stattdessen werden die Inhalte neu eingefügten Zeilen basierend auf dem vorhandenen Wert des Primärschlüssels neu synchronisiert. Wenn der Primärschlüssel einen Wert für eine Option zum automatischen inkrementieren ist **Resync** wird nicht Abrufen des Inhalts der gewünschten Zeile. Rufen Sie für die Primärschlüsselwerte AutoIncrement automatisch inkrementiert, **UpdateBatch** mit der kombinierte Wert **AdResyncAutoIncrement** + **AdResyncInserts**.|  
|**adResyncNone**|0|Ruft auch keine **Resync**.|  
|**adResyncUpdates**|4|Ruft **Resync** für alle erfolgreich aktualisierten Zeilen.|  
  
## <a name="applies-to"></a>Gilt für  
 [Dynamische Eigenschaft Update Resync (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
