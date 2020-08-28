---
description: Fehlerinformationen im Zusammenhang mit Feldern
title: Feldbezogene Fehlerinformationen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- field-related errors [ADO]
- errors [ADO], field-related
ms.assetid: 5e7b1af4-996b-47c5-9161-c5575ad4fec9
author: rothja
ms.author: jroth
ms.openlocfilehash: af7aee82f8568cafcc35ac0e78d13386822888fb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991261"
---
# <a name="field-related-error-information"></a>Fehlerinformationen im Zusammenhang mit Feldern
Wenn ein Fehler direkt mit einem Feld verknüpft ist, z. b. wenn die Daten fehlen oder der falsche Typ für das Feld vorliegt, können Sie weitere Informationen zur Ursache des Problems abrufen, indem Sie die Eigenschaft **Status** des **Field** -Objekts untersuchen. Diese Eigenschaft wurde erweitert, um bestimmte Informationen über das Problem bereitzustellen. Wenn z. b. beim Aufrufen von **UpdateBatch** ein Fehler auftritt, kann die Ursache des Problems durch Untersuchen der **Status** -Eigenschaft der **Felder** in jedem der betroffenen Datensätze ermittelt werden. Die-Eigenschaft enthält einen der Werte in der **fieldstatuusenum** -Konstante. In der folgenden Tabelle sind die Werte enthalten, die bei Auftreten eines Fehlers besonders interessant sind.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adfieldcantconvertvalue**|2|Gibt an, dass das Feld ohne Datenverlust nicht abgerufen oder gespeichert werden kann.|  
|**adfielddataoverflow**|6|Gibt an, dass die vom Anbieter zurückgegebenen Daten zu einem Überlauf des Datentyps des Felds geführt haben.|  
|**adfielddefault**|13|Gibt an, dass beim Festlegen von Daten der Standardwert für das Feld verwendet wurde.|  
|**adfieldignore**|15|Gibt an, dass dieses Feld übersprungen wurde, als Datenwerte in der Quelle festgelegt wurden. Vom Anbieter wurde kein Wert festgelegt.|  
|**adfieldintegrityverletzungs**|10|Gibt an, dass das Feld nicht geändert werden kann, da es eine berechnete oder abgeleitete Entität ist.|  
|**adfieldisnull**|3|Gibt an, dass der Anbieter einen NULL-Wert zurückgegeben hat.|  
|**adfieldouesleerraum**|22|Gibt an, dass der Anbieter nicht genügend Speicherplatz zum Durchführen eines verschiebe-oder Kopiervorgangs abrufen kann.|
