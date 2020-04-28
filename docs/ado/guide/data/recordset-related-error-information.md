---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d3f8e8d9802b5d0c73af73aff20d929c188b9292
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924373"
---
# <a name="recordset-related-error-information"></a>Fehlerinformationen in Bezug auf Recordsets
Während der Batch Verarbeitung stellt die **Status** -Eigenschaft des **Recordset** -Objekts Informationen über die einzelnen Datensätze im **Recordset**bereit. Bevor ein Batch Update durchgeführt wird, gibt die **Status** -Eigenschaft des **Recordsets** Informationen zu Datensätzen wieder, die hinzugefügt, geändert und gelöscht werden sollen. Nachdem **UpdateBatch** aufgerufen wurde, gibt die Eigenschaft **Status** an, dass der Vorgang erfolgreich war oder fehlgeschlagen ist. Wenn Sie von Datensatz zu Datensatz im **Recordset**wechseln, ändert sich der Wert der **Status** -Eigenschaft, um den Status des aktuellen Datensatzes zu beschreiben.
