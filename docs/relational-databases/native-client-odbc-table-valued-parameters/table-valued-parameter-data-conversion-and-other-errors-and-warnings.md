---
description: Tabellenwertparameter-Datenkonvertierung und andere Fehler und Warnungen
title: Konvertierung von Table-Valued-Parameter Daten
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 265616a508e610b179d56ed285bd43dcb40beb48
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97473501"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>Tabellenwertparameter-Datenkonvertierung und andere Fehler und Warnungen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Tabellenwertparameter-Spaltenwerte können genau wie andere Spalten- und Parameterwerte zwischen Client- und Serverdatentypen konvertiert werden. Da Tabellenwertparameter jedoch mehrere Spalten und Zeilen enthalten können, ist es wichtig, den Wert identifizieren zu können, bei dem der Fehler aufgetreten ist.  
  
 Wird eine Warnung oder ein Fehler in einer Tabellenwertparameter-Spalte erkannt, generiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client einen Diagnosedatensatz. Die Fehlermeldung enthält die Parameternummer des Tabellenwertparameters sowie die Spaltenordnungszahl und Zeilennummer. Zudem können die Diagnosefelder SQL_DIAG_SS_TABLE_COLUMN_NUMBER und SQL_DIAG_SS_TABLE_ROW_NUMBER innerhalb der Diagnosedatensätze von einer Anwendung verwendet werden, um zu bestimmen, welche Werte mit Fehlern und Warnungen verknüpft sind. Diese Diagnosefelder sind in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen verfügbar.  
  
 In jeder anderen Hinsicht entsprechen die SQLSTATE- und Meldungskomponenten von Diagnosedatensätzen vorhandenem ODBC-Verhalten. Das heißt, mit Ausnahme der Parameter-, Zeilen-und Spalten Identifizierungs Informationen haben Fehlermeldungen dieselben Werte für Tabellenwert Parameter wie für nicht-Tabellenwert Parameter.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwert Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
