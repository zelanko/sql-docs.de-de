---
title: Tabellenwertparameter-Daten Konvertierung und anderen Fehlern und Warnungen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cde1f88a46594209fa908d81770e2e0345666350
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061160"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>Tabellenwertparameter-Datenkonvertierung und andere Fehler und Warnungen
  Tabellenwertparameter-Spaltenwerte können genau wie andere Spalten- und Parameterwerte zwischen Client- und Serverdatentypen konvertiert werden. Da Tabellenwertparameter jedoch mehrere Spalten und Zeilen enthalten können, ist es wichtig, den Wert identifizieren zu können, bei dem der Fehler aufgetreten ist.  
  
 Wird eine Warnung oder ein Fehler in einer Tabellenwertparameter-Spalte erkannt, generiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client einen Diagnosedatensatz. Die Fehlermeldung enthält die Parameternummer des Tabellenwertparameters sowie die Spaltenordnungszahl und Zeilennummer. Zudem können die Diagnosefelder SQL_DIAG_SS_TABLE_COLUMN_NUMBER und SQL_DIAG_SS_TABLE_ROW_NUMBER innerhalb der Diagnosedatensätze von einer Anwendung verwendet werden, um zu bestimmen, welche Werte mit Fehlern und Warnungen verknüpft sind. Diese Diagnosefelder sind in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen verfügbar.  
  
 In jeder anderen Hinsicht entsprechen die SQLSTATE- und Meldungskomponenten von Diagnosedatensätzen vorhandenem ODBC-Verhalten. Mit Ausnahme von Parameter-, Zeilen- und Spaltenidentifikationsinformationen weisen Fehlermeldungen somit die gleichen Werte für Tabellenwertparameter auf wie für Parameter, die keine Tabellenwertparameter sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  