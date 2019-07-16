---
title: Rolle des Treiber-Managers | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7184c8ac9e0ad1813999a276f1579351f98544ac
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020398"
---
# <a name="role-of-the-driver-manager"></a>Rolle des Treiber-Managers
Der Treiber-Manager bestimmt die endgültige Reihenfolge in den statusdatensätzen zurückgegeben, die es generiert. Insbesondere bestimmt, welcher Datensatz, hat den höchsten Rang, und zuerst zurückgegeben werden soll. Der Treiber ist verantwortlich für die Sortierung der Statusdatensätze, die es generiert. Wenn sowohl der Treiber-Manager als auch der Treiber Statusdatensätze bereitgestellt werden, ist der Treiber-Manager für ihre Anordnung verantwortlich. Weitere Informationen finden Sie unter [Sequenz der Statusdatensätze](../../../odbc/reference/develop-app/sequence-of-status-records.md).  
  
 Der Treiber-Manager ist so viel fehlerüberprüfung wie möglich. Dadurch werden alle Treiber bei der Überprüfung für die gleichen Fehler. Angenommen, ein Funktionsargument akzeptiert eine diskrete Anzahl von Werten, z.B. *Vorgang* in **SQLSetPos**, der Treiber-Manager überprüft, ob der angegebene Wert zulässig ist.  
  
 Die folgenden Abschnitte beschreiben die Typen von Bedingungen, die vom Treiber-Manager überprüft. Sie sind nicht vorgesehen, umfassendes Ergebnis können; für eine vollständige Liste mit den SQLSTATEs des Treiber-Managers zurückgibt, finden Sie im Abschnitt "Diagnose" für jede Funktion; die Beschreibung der einzelnen Überprüfung vom Treiber-Manager beginnt mit den Buchstaben "(DM)." Siehe auch den Übergang Statustabellen in [Anhang B: ODBC-Übergang Statustabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md); Fehler in Klammern angezeigt werden vom Treiber-Manager erkannt.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Überprüfungen des Argumentwerts](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [Überprüfungen des Statusübergangs](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [Überprüfungen auf allgemeine Fehler](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [Fehler des Treiber-Managers und Überprüfungen der Warnung](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
