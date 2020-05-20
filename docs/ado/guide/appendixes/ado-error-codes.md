---
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
ms.openlocfilehash: bceca521ebbf79f3e25fc0585130bc6bc96f7244
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761648"
---
# <a name="capture-ado-error-codes"></a>ADO-Fehler Codes erfassen
Zusätzlich zu den Anbieter Fehlern, die in den [Fehler](../../../ado/reference/ado-api/error-object.md) Objekten der [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung zurückgegeben werden, kann ADO selbst Fehler an den Mechanismus zur Ausnahmebehandlung der Laufzeitumgebung zurückgeben. Verwenden Sie den fehlerabfang Mechanismus in ihrer Programmiersprache, wie z. b. die **On Error** -Anweisung in Microsoft® Visual Basic oder den **try-catch-** Block in Microsoft Visual C++®, um ADO-Fehler aufzuzeichnen.

 Eine Liste der ADO-Fehlercodes finden Sie unter [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>Weitere Informationen
 [Error Object](../../../ado/reference/ado-api/error-object.md) [Errors Collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)
