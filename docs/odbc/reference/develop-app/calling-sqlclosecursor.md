---
title: Aufrufen von SQLCloseCursor | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2feab58de28e39747a1d9c819f9f15426b156151
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306273"
---
# <a name="calling-sqlclosecursor"></a>Aufrufen von SQLCloseCursor
Da **SQLCloseCursor** fast identisch mit **SQLFreeStmt** mit SQL_CLOSE ist, wird diese Funktion im Treiber-Manager nicht zugeordnet. Ersatzfunktionen werden so abgebildet, dass vorhandene ODBC *2.x-Anwendungen* mithilfe der neuen Funktionen problemlos zu ODBC *3.x* verschoben werden können. Eine solche Bewegung erleichtert es solchen Anwendungen, neue ODBC *3.x-Funktionalität* innerhalb von bedingtem Code modular zu verwenden. **SQLCloseCursor** stellt keine neuen Funktionen dar. Eine Anwendung gewinnt keinen Vorteil, indem sie von **SQLFreeStmt** mit SQL_CLOSE zu **SQLCloseCursor** wechselt.
