---
description: ADO-Fehler Codes erfassen
title: ADO-Fehler Codes | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], error codes
ms.assetid: 3aee61c7-a9b7-4596-b78e-5828a00d0281
author: rothja
ms.author: jroth
ms.openlocfilehash: b5c3f5f00355bb2c9f9762db1d317a592b4df7dc
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88805341"
---
# <a name="capture-ado-error-codes"></a>ADO-Fehler Codes erfassen
Zusätzlich zu den Anbieter Fehlern, die in den [Fehler](../../reference/ado-api/error-object.md) Objekten der [Fehler](../../reference/ado-api/errors-collection-ado.md) Auflistung zurückgegeben werden, kann ADO selbst Fehler an den Mechanismus zur Ausnahmebehandlung der Laufzeitumgebung zurückgeben. Verwenden Sie den fehlerabfang Mechanismus in ihrer Programmiersprache, wie z. b. die **On Error** -Anweisung in Microsoft® Visual Basic oder den **try-catch-** Block in Microsoft Visual C++®, um ADO-Fehler aufzuzeichnen.

 Eine Liste der ADO-Fehlercodes finden Sie unter [ErrorValueEnum](../../reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>Weitere Informationen
 [Error Object](../../reference/ado-api/error-object.md) [Errors Collection (ADO)](../../reference/ado-api/errors-collection-ado.md)