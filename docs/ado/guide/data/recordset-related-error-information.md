---
description: Fehlerinformationen in Bezug auf Recordsets
title: Recordsetbezogene Fehlerinformationen | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7806d446c200f4d90ec458ceea268435ad9994e1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452952"
---
# <a name="recordset-related-error-information"></a>Fehlerinformationen in Bezug auf Recordsets
Während der Batch Verarbeitung stellt die **Status** -Eigenschaft des **Recordset** -Objekts Informationen über die einzelnen Datensätze im **Recordset**bereit. Bevor ein Batch Update durchgeführt wird, gibt die **Status** -Eigenschaft des **Recordsets** Informationen zu Datensätzen wieder, die hinzugefügt, geändert und gelöscht werden sollen. Nachdem **UpdateBatch** aufgerufen wurde, gibt die Eigenschaft **Status** an, dass der Vorgang erfolgreich war oder fehlgeschlagen ist. Wenn Sie von Datensatz zu Datensatz im **Recordset**wechseln, ändert sich der Wert der **Status** -Eigenschaft, um den Status des aktuellen Datensatzes zu beschreiben.
