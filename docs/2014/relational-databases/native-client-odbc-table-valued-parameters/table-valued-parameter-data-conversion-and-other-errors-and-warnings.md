---
title: Tabellenwert Parameter-Datenkonvertierung und andere Fehler und Warnungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: rothja
ms.author: jroth
ms.openlocfilehash: 45b9ba7f91b54548e096bbe47da6e01ba562f59d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84999070"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>Tabellenwertparameter-Datenkonvertierung und andere Fehler und Warnungen
  Tabellenwertparameter-Spaltenwerte können genau wie andere Spalten- und Parameterwerte zwischen Client- und Serverdatentypen konvertiert werden. Da Tabellenwertparameter jedoch mehrere Spalten und Zeilen enthalten können, ist es wichtig, den Wert identifizieren zu können, bei dem der Fehler aufgetreten ist.  
  
 Wird eine Warnung oder ein Fehler in einer Tabellenwertparameter-Spalte erkannt, generiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client einen Diagnosedatensatz. Die Fehlermeldung enthält die Parameternummer des Tabellenwertparameters sowie die Spaltenordnungszahl und Zeilennummer. Zudem können die Diagnosefelder SQL_DIAG_SS_TABLE_COLUMN_NUMBER und SQL_DIAG_SS_TABLE_ROW_NUMBER innerhalb der Diagnosedatensätze von einer Anwendung verwendet werden, um zu bestimmen, welche Werte mit Fehlern und Warnungen verknüpft sind. Diese Diagnosefelder sind in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen verfügbar.  
  
 In jeder anderen Hinsicht entsprechen die SQLSTATE- und Meldungskomponenten von Diagnosedatensätzen vorhandenem ODBC-Verhalten. Das heißt, mit Ausnahme der Parameter-, Zeilen-und Spalten Identifizierungs Informationen haben Fehlermeldungen dieselben Werte für Tabellenwert Parameter wie für nicht-Tabellenwert Parameter.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwert Parameter &#40;ODBC-&#41;](table-valued-parameters-odbc.md)  
  
  
