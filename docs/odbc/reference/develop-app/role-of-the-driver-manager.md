---
title: Rolle des Treiber-Managers | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- diagnostic information [ODBC], driver manager error checking
- SQLGetDiagField function [ODBC], driver manager
- SQLGetDiagRec function [ODBC], driver manager
- ODBC driver manager [ODBC]
- diagnostic information [ODBC], SqlGetDiagRec
- driver manager [ODBC], error checking
ms.assetid: 7b861c82-357e-4590-8074-45136e9ed15e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee3d704ea43125c3cd912a4e67d90bf5d50c733e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304301"
---
# <a name="role-of-the-driver-manager"></a>Rolle des Treiber-Managers
Der Treiber-Manager bestimmt die endgültige Reihenfolge, in der Statusdatensätze zurückgegeben werden sollen, die er generiert. Insbesondere bestimmt er, welcher Datensatz den höchsten Rang hat und zuerst zurückgegeben werden soll. Der Treiber ist für die Reihenfolge der generierten Statusdatensätze verantwortlich. Wenn Statusdatensätze sowohl vom Treiber-Manager als auch vom Treiber gebucht werden, ist der Treiber-Manager für deren Bestellung verantwortlich. Weitere Informationen finden Sie unter [Sequenz von Statusdatensätzen](../../../odbc/reference/develop-app/sequence-of-status-records.md).  
  
 Der Treiber-Manager führt so viele Fehlerüberprüfungen wie möglich durch. Dies erspart jedem Fahrer die Überprüfung auf die gleichen Fehler. Wenn z. B. ein Funktionsargument eine diskrete Anzahl von Werten akzeptiert, z. B. *Operation* in **SQLSetPos**, überprüft der Treiber-Manager, ob der angegebene Wert zulässig ist.  
  
 In den folgenden Abschnitten werden die vom Treiber-Manager überprüften Bedingungen beschrieben. Sie sollen nicht erschöpfend sein; Eine vollständige Liste der vom Treiber-Manager zurückgegebenen SQLSTATEs finden Sie im Abschnitt "Diagnose" jeder Funktion; Die Beschreibung jeder Vom Treiber-Manager vorgenommenen Prüfung beginnt mit den Buchstaben "(DM)." Siehe auch die Zustandsübergangstabellen in [Anhang B: ODBC-Zustandsübergangstabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md); Fehler, die in Klammern angezeigt werden, werden vom Treiber-Manager erkannt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Überprüfungen des Argumentwerts](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [Überprüfungen des Statusübergangs](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [Überprüfungen auf allgemeine Fehler](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [Fehler des Treiber-Managers und Überprüfungen der Warnung](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
