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
ms.openlocfilehash: 2502e1dec35ec0d6450190650a18ac765ce14421
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88355226"
---
# <a name="capture-ado-error-codes"></a>ADO-Fehler Codes erfassen
Zusätzlich zu den Anbieter Fehlern, die in den [Fehler](../../../ado/reference/ado-api/error-object.md) Objekten der [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung zurückgegeben werden, kann ADO selbst Fehler an den Mechanismus zur Ausnahmebehandlung der Laufzeitumgebung zurückgeben. Verwenden Sie den fehlerabfang Mechanismus in ihrer Programmiersprache, wie z. b. die **On Error** -Anweisung in Microsoft® Visual Basic oder den **try-catch-** Block in Microsoft Visual C++®, um ADO-Fehler aufzuzeichnen.

 Eine Liste der ADO-Fehlercodes finden Sie unter [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>Weitere Informationen
 [Error Object](../../../ado/reference/ado-api/error-object.md) [Errors Collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)
