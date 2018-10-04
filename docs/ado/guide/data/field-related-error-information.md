---
title: Feld-bezogene Fehlerinformationen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- field-related errors [ADO]
- errors [ADO], field-related
ms.assetid: 5e7b1af4-996b-47c5-9161-c5575ad4fec9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01f456527d7be8a954fecdace730bd1f8e47936b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47813048"
---
# <a name="field-related-error-information"></a>Fehlerinformationen im Zusammenhang mit Feldern
Wenn ein Fehler auf ein Feld direkt verknüpft ist – z. B. wenn die Daten nicht vorhanden ist oder wenn es sich um den falschen Typ für das Feld ist, können Sie weitere Informationen zur Ursache des Problems abrufen, indem Untersuchen der **Feld** des Objekts **Status**  Eigenschaft. Diese Eigenschaft wurde verbessert, um bestimmte Informationen über das Problem bereitzustellen. Dies der Fall ist, z. B. wenn ein Aufruf von **UpdateBatch** ein Fehler auftritt, die Ursache des Problems können ermittelt werden die **Status** Eigenschaft der **Felder** in jedem der betroffenen Datensätze. Die Eigenschaft enthält einen der Werte in der **FieldStatusEnum** Konstanten. Die folgende Tabelle enthält die Werte, die von besonderem Interesse sind, wenn ein Fehler auftritt.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adFieldCantConvertValue**|2|Gibt an, dass das Feld kann nicht abgerufen oder ohne Verlust von Daten gespeichert werden.|  
|**adFieldDataOverflow**|6|Gibt an, dass die vom Anbieter zurückgegebenen Daten den Datentyp des Felds ist ein Überlauf aufgetreten.|  
|**adFieldDefault**|13|Gibt an, dass der Standardwert für das Feld, beim Festlegen der Daten verwendet wurde.|  
|**adFieldIgnore**|15|Gibt an, dass dieses Feld bei der Einstellung Datenwerte in der Quelle übersprungen wurde. Vom Anbieter wurde kein Wert festgelegt.|  
|**adFieldIntegrityViolation**|10|Gibt an, dass das Feld kann nicht geändert werden, da es sich um eine Entität berechneter oder abgeleiteter handelt.|  
|**adFieldIsNull**|3|Gibt an, dass der Anbieter einen null-Wert zurückgegeben.|  
|**adFieldOutOfSpace**|22|Gibt an, dass der Anbieter ist nicht genügend Speicherplatz zum Abschließen eines Verschiebe- oder Kopiervorgang zu erhalten.|
