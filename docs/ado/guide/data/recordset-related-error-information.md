---
title: Recordset-bezogene Fehlerinformationen | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 55f64646050eba8c76432c68c39b36b0daa9f4be
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272349"
---
# <a name="recordset-related-error-information"></a>Recordset-bezogene Fehlerinformationen
Während der Batchverarbeitung der **Status** Eigenschaft von der **Recordset** Objekt enthält Informationen zu den einzelnen Einträgen in der **Recordset**. Bevor ein Update mithilfe der Batchverarbeitung stattfindet, die **Status** Eigenschaft von der **Recordset** gibt Informationen zu Datensätzen hinzugefügt, geändert und gelöscht werden. Nach dem **UpdateBatch** aufgerufen wurde, die **Status** Eigenschaft gibt den Erfolg oder Misserfolg des Vorgangs an. Wie beim Verschieben von Datensatz zu Datensatz, der **Recordset**, den Wert von der **Status** eigenschaftsänderungen, um den Status des aktuellen Datensatzes zu beschreiben.
