---
description: Fehlerinformationen in Bezug auf Recordsets
title: Recordsetbezogene Fehlerinformationen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 454c62b969ee69e6186792ce77873c8c8fbb5704
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979811"
---
# <a name="recordset-related-error-information"></a>Fehlerinformationen in Bezug auf Recordsets
Während der Batch Verarbeitung stellt die **Status** -Eigenschaft des **Recordset** -Objekts Informationen über die einzelnen Datensätze im **Recordset**bereit. Bevor ein Batch Update durchgeführt wird, gibt die **Status** -Eigenschaft des **Recordsets** Informationen zu Datensätzen wieder, die hinzugefügt, geändert und gelöscht werden sollen. Nachdem **UpdateBatch** aufgerufen wurde, gibt die Eigenschaft **Status** an, dass der Vorgang erfolgreich war oder fehlgeschlagen ist. Wenn Sie von Datensatz zu Datensatz im **Recordset**wechseln, ändert sich der Wert der **Status** -Eigenschaft, um den Status des aktuellen Datensatzes zu beschreiben.
