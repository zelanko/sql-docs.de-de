---
title: Recordset-bezogene Fehlerinformationen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c4f13a77a9f03aa76fccc41a1fa19878dd935db0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187799"
---
# <a name="recordset-related-error-information"></a>Fehlerinformationen in Bezug auf Recordsets
Während der Stapelverarbeitung der **Status** Eigenschaft der **Recordset** -Objekt stellt Informationen über die einzelnen Datensätze in der **Recordset**. Bevor eine Batchaktualisierung stattfindet, die **Status** Eigenschaft der **Recordset** gibt Informationen zu Datensätzen hinzugefügt, geändert und gelöscht werden. Nach dem **UpdateBatch** aufgerufen wurde, die **Status** Eigenschaft gibt an, den Erfolg oder Misserfolg des Vorgangs. Wie Sie von Datensatz zu Datensatz, in verschoben der **Recordset**, den Wert des der **Status** eigenschaftsänderungen, um den Status des aktuellen Datensatzes beschreiben.
