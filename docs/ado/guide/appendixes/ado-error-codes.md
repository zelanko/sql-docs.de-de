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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9efe0f39ce304501096d9dcc682a0ea5d5137ee7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926996"
---
# <a name="capture-ado-error-codes"></a>ADO-Fehler Codes erfassen
Zusätzlich zu den Anbieter Fehlern, die in den [Fehler](../../../ado/reference/ado-api/error-object.md) Objekten der [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung zurückgegeben werden, kann ADO selbst Fehler an den Mechanismus zur Ausnahmebehandlung der Laufzeitumgebung zurückgeben. Verwenden Sie den fehlerabfang Mechanismus in ihrer Programmiersprache, wie z. b. die **On Error** -Anweisung in Microsoft® Visual Basic oder den **try-catch-** Block in Microsoft Visual C++®, um ADO-Fehler aufzuzeichnen.

 Eine Liste der ADO-Fehlercodes finden Sie unter [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>Weitere Informationen
 [Error Object](../../../ado/reference/ado-api/error-object.md) [Errors Collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)
