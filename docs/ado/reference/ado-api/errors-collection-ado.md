---
title: Errors-Auflistung (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Errors
- Connection15::get_Errors
- Connection15::GetErrors
helpviewer_keywords:
- Errors collection [ADO]
ms.assetid: 290819e1-7b39-4e1e-a93b-801257138b00
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 109b7ff83e6b3f722560dae0a034c4bf37da137f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719265"
---
# <a name="errors-collection-ado"></a>Errors-Collection (ADO)
Enthält alle der [Fehler](../../../ado/reference/ado-api/error-object.md) Objekte, die in Reaktion auf einen einzelnen Anbieter bezogene Fehler erstellt.  
  
## <a name="remarks"></a>Hinweise  
 Alle Vorgänge im Zusammenhang mit ADO-Objekte kann ein oder mehrere Anbieterfehler generieren. Sobald ein Fehler auftritt, eine oder mehrere **Fehler** Objekte eingefügt werden können, der **Fehler** Auflistung von der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt. Wenn ein anderer ADO-Vorgang einen Fehler generiert die **Fehler** Auflistung deaktiviert ist, und der neue Satz von **Fehler** Objekte eingefügt werden können, der **Fehler** Auflistung.  
  
 Jede **Fehler** Objekt stellt einen bestimmten Anbieterfehler, nicht für einen ADO-Fehler dar. ADO-Fehler werden Verfahren zur Ausnahmebehandlung der Laufzeit verfügbar gemacht. Z. B. in Microsoft Visual Basic, das Vorhandensein einer ADO-spezifischer Fehler löst eine [OnError](../../../ado/reference/rds-api/onerror-event-rds.md) Ereignis und angezeigt werden, der **Err** Objekt.  
  
 ADO-Vorgänge, die einen Fehler generieren nicht haben keine Auswirkungen auf die **Fehler** Auflistung. Verwenden der [löschen](../../../ado/reference/ado-api/clear-method-ado.md) Methode manuell löschen, die **Fehler** Auflistung.  
  
 Der Satz von **Fehler** Objekte in der **Fehler** Sammlung beschreibt alle Fehler, die als Reaktion auf eine einzelne Anweisung aufgetreten sind. Auflisten von der spezifischen Fehlern in der **Fehler** erfasst werden können, genauer gesagt die Ursache ermitteln und Ursprung des Fehler, und führen entsprechende Schritte zur Wiederherstellung Ihrer Routinen zur Fehlerbehandlung.  
  
 Einige Eigenschaften und Methoden zurück Warnungen, als angezeigt **Fehler** Objekte in der **Fehler** Auflistung jedoch nicht die Ausführung eines Programms an. Vor dem Aufruf der [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) Methoden für eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt, das [Öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) Methode für eine **Verbindung** Objekt, oder legen Sie die [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaft für eine **Recordset** Objekt, rufen Sie die **Löschen**Methode für die **Fehler** Auflistung. Auf diese Weise erhalten Sie die [Anzahl](../../../ado/reference/ado-api/count-property-ado.md) Eigenschaft der **Fehler** zurückgegebene Auflistung zum Prüfen auf-Warnungen.  
  
> [!NOTE]
>  Finden Sie unter den **Fehler** Thema-Objekt für eine ausführlichere Erläuterung der Art und Weise, die ein einzelnen ADO-Vorgang kann mehrere Fehler generieren.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Fehler-Auflistung – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/errors-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
