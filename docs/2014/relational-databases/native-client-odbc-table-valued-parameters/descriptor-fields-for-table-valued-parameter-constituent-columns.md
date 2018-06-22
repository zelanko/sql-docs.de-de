---
title: Deskriptorfelder für Tabellenwertparameter-Spalten | Microsoft Docs
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
- table-valued parameters (ODBC), descriptor fields for constituent columns
ms.assetid: 944b3968-fd47-4847-98d6-b87e8ef2acdc
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6888494d35b16987cf5d3b3e8a55a44784d2ca11
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058481"
---
# <a name="descriptor-fields-for-table-valued-parameter-constituent-columns"></a>Deskriptorfelder für aus Tabellenwertparameter bestehenden Spalten
  Die in diesem Abschnitt beschriebenen deskriptorfelder für Tabellenwertparameter werden mit bearbeitet [SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md) und [SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md) mit dem Handle für die Implementierung Parameter Descriptor ( IPD).  
  
## <a name="remarks"></a>Hinweise  
 SQL_DESC_AUTO_UNIQUE_VALUE wird für Tabellenwertparameter sowie für andere Funktionen verwendet.  
  
|Attributname|Typ|Description|  
|--------------------|----------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|SQL_TRUE gibt an, dass es sich bei dieser Spalte um eine Identitätsspalte handelt.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können diese Informationen verwenden, um die Leistung zu optimieren sind, Anwendungen jedoch nicht für Identitätsspalten festlegen.|  
  
 Die folgenden Attribute werden allen Parametertypen im Anwendungsparameterdeskriptor (Application Parameter Descriptor, APD) und Implementierungsparameterdeskriptor (Implementation Parameter Descriptor, IPD) hinzugefügt:  
  
|Attributname|Typ|Description|  
|--------------------|----------|-----------------|  
|SQL_CA_SS_COLUMN_COMPUTED|SQLSMALLINT|SQL_TRUE gibt an, dass diese Spalte berechnet wird.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können diese Informationen verwenden, um die Leistung zu optimieren sind, Anwendungen jedoch nicht für berechnete Spalten festlegen.<br /><br /> Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind.|  
|SQL_CA_SS_COLUMN_IN_UNIQUE_KEY|SQLSMALLINT|SQL_TRUE gibt an, dass eine Tabellenwertparameter-Spalte zu einem eindeutigen Schlüssel gehört. Dies kann zu einer verbesserten Abfrageleistung führen. Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind.|  
|SQL_CA_SS_COLUMN_SORT_ORDER|SQLSMALLINT|Gibt die Sortierreihenfolge einer Tabellenwertparameter-Spalte an. Dies kann zu einer verbesserten Abfrageleistung führen. Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind. Die möglichen Werte sind folgende:<br /><br /> -SQL_SS_ASCENDING_ORDER<br />-SQL_SS_DESCENDING_ORDER<br />-SQL_SS_ORDER_UNSPECIFIED<br /><br /> Andere Werte als SQL_SS_ASCENDING_ORDER und SQL_SS_DESCENDING_ORDER erzeugen einen Fehler mit SQLSTATE HY024 und die Meldung 'Ungültiger Attributwert'. Sie werden als SQL_SS_ORDER_UNSPECIFIED behandelt. Dies ist der Standardwert für dieses Attribut.|  
|SQL_CA_SS_COLUMN_SORT_ORDINAL|SQLSMALLINT|Gibt die Ordnungszahl einer Tabellenwertparameter-Spalte in einer Gruppe von Spalten an, die die Gesamtreihenfolge für einen Tabellenwertparameter festlegt. Dies kann zu einer verbesserten Abfrageleistung führen. Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind. Die Sortierung der Ordinalzahlen beginnt bei 1. Der Wert 0 ist der Standardwert und gibt eine Tabellenwertparameter-Spalte an, für die keine Spaltenreihenfolge angegeben wurde.|  
|SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE|SQLSMALLINT|Gibt an, ob alle Zeilen im Tabellenwertparameter den Standardwert für diese Spalte enthalten. Für Tabellenwertparameter ist es nicht möglich, den Standardwert auf Zeilenbasis auszuwählen. Der Wert SQL_FALSE gibt an, dass Zeilen nicht standardmäßige Werte enthalten. Dies ist die Standardeinstellung. Der Wert SQL_TRUE gibt an, dass diese Spalte Standardwerte für alle Zeilen enthält.<br /><br /> Wurde der Wert auf SQL_TRUE festgelegt, werden keine Daten an den Server gesendet.<br /><br /> Dieses Feld kann auch mit Identitätsspalten oder berechneten Spalten verwendet werden, wenn die Spaltenwerte nicht für die Serververarbeitung erforderlich sind.|  
  
 Diese Attribute sind nur für Tabellenwertparameter-Spalten gültig. Sie werden für andere Parameter ignoriert.  
  
 Wenn SQL_CA_SS_COL_HAS_DEFAULT_VALUE für eine Tabellenwertparameter-Spalte festgelegt wurde, muss SQL_DESC_DATA_PTR für diese Spalte ein NULL-Zeiger sein. Andernfalls gibt SQLExecute oder SQLExecDirect SQL_ERROR zurück. Generiert ein Diagnosedatensatz mit SQLSTATE = 07S01 und der Meldung "Verwendung des Standardparameters ungültig für Parameter \<p >, Spalte \<c >", wobei \<p > ist der Parameter ordinal und \<c > ist der Ordnungszahl der Spalte.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  