---
title: Rolle des Fahrers | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver error checking [ODBC]
- diagnostic information [ODBC], driver error checking
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c683d990aaa3fd6892369e734c06fd1c356bd0f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304282"
---
# <a name="role-of-the-driver"></a>Rolle des Treibers
Der Treiber überprüft alle Fehler und Warnungen, die nicht vom Treiber-Manager überprüft werden, und ordnet statusdatensätze an, die er generiert. (Ein ODBC 2. *x-Treiber* ordnet keine Statusdatensätze an.) Dazu gehören Fehler und Warnungen bei Datenkürzungen, Datenkonvertierungen, Syntax und einigen Zustandsübergängen. Der Treiber kann auch Fehler und Warnungen überprüfen, die teilweise vom Treiber-Manager überprüft wurden. Obwohl der Treiber-Manager beispielsweise überprüft, ob der Wert von *Operation* in **SQLSetPos** zulässig ist, muss der Treiber überprüfen, ob er unterstützt wird.  
  
 Der Treiber ordnet *auch systemeigene Fehler* - d. h. von der Datenquelle zurückgegebene Fehler - SQLSTATEs zu. Der Treiber kann z. B. eine Reihe verschiedener systemeigener Fehler für die unzulässige SQL-Syntax SQLSTATE 42000 zuordnen (Syntaxfehler oder Zugriffsverletzung). Der Treiber gibt die systemeigene Fehlernummer im Feld SQL_DIAG_NATIVE des Statusdatensatzes zurück. Die Treiberdokumentation sollte zeigen, wie Fehler und Warnungen aus der Datenquelle Argumenten in **SQLGetDiagRec** und **SQLGetDiagField**zugeordnet werden.
