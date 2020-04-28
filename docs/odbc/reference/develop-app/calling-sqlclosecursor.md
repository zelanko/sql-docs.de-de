---
title: Aufrufen von SQLCloseCursor | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306273"
---
# <a name="calling-sqlclosecursor"></a>Aufrufen von SQLCloseCursor
Da **SQLCloseCursor** fast mit **SQLFreeStmt** with SQL_CLOSE identisch ist, ordnet der Treiber-Manager diese Funktion nicht zu. Ersetzungs Funktionen werden zugeordnet, sodass vorhandene ODBC *2. x* -Anwendungen mithilfe der neuen Funktionen problemlos zu ODBC *3. x* verschoben werden können. Eine solche Verschiebung erleichtert es solchen Anwendungen, mit der Verwendung der neuen ODBC *3. x* -Funktionalität innerhalb von bedingtem Code in einem modularen Stil zu beginnen. **SQLCloseCursor** stellt keine neuen Funktionen dar. Eine Anwendung erhält keinen Vorteil, indem Sie von **SQLFreeStmt** mit SQL_CLOSE zu **SQLCloseCursor** wechselt.
