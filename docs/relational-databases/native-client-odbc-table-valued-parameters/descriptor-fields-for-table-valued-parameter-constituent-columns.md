---
description: Deskriptorfelder für aus Tabellenwertparameter bestehenden Spalten
title: Deskriptorfeld für Tabellenwert Parameter
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor fields for constituent columns
ms.assetid: 944b3968-fd47-4847-98d6-b87e8ef2acdc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 93e89dd98538f8c7c814388e0d9dd8ea25171862
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499104"
---
# <a name="descriptor-fields-for-table-valued-parameter-constituent-columns"></a>Deskriptorfelder für aus Tabellenwertparameter bestehenden Spalten
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Die in diesem Abschnitt beschriebenen Tabellenwert Parameter-Deskriptorfelder werden mithilfe von [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md) und [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md) mit dem Handle für den Implementierungs Parameter Deskriptor (IPD) manipuliert.  
  
## <a name="remarks"></a>Bemerkungen  
 SQL_DESC_AUTO_UNIQUE_VALUE wird für Tabellenwertparameter sowie für andere Funktionen verwendet.  
  
|Attributname|type|Beschreibung|  
|--------------------|----------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|SQL_TRUE gibt an, dass es sich bei dieser Spalte um eine Identitätsspalte handelt.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann diese Informationen verwenden, um die Leistung zu optimieren, Anwendungen müssen jedoch nicht für Identitäts Spalten festgelegt werden.|  
||||

 Die folgenden Attribute werden allen Parametertypen im Anwendungsparameterdeskriptor (Application Parameter Descriptor, APD) und Implementierungsparameterdeskriptor (Implementation Parameter Descriptor, IPD) hinzugefügt:  
  
|Attributname|type|Beschreibung|  
|--------------------|----------|-----------------|  
|SQL_CA_SS_COLUMN_COMPUTED|SQLSMALLINT|SQL_TRUE gibt an, dass diese Spalte berechnet wird.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann diese Informationen verwenden, um die Leistung zu optimieren, Anwendungen müssen Sie jedoch nicht für berechnete Spalten festlegen.<br /><br /> Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind.|  
|SQL_CA_SS_COLUMN_IN_UNIQUE_KEY|SQLSMALLINT|SQL_TRUE gibt an, dass eine Tabellenwertparameter-Spalte zu einem eindeutigen Schlüssel gehört. Dies kann zu einer verbesserten Abfrageleistung führen. Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind.|  
|SQL_CA_SS_COLUMN_SORT_ORDER|SQLSMALLINT|Gibt die Sortierreihenfolge einer Tabellenwertparameter-Spalte an. Dies kann zu einer verbesserten Abfrageleistung führen. Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind. Folgende Werte sind möglich: <br />**SQL_SS_ASCENDING_ORDER**<br />**SQL_SS_DESCENDING_ORDER**<br />**SQL_SS_ORDER_UNSPECIFIED**<br /><br /> Andere Werte als **SQL_SS_ASCENDING_ORDER** und **SQL_SS_DESCENDING_ORDER** generieren einen Fehler mit **SQLSTATE HY024** und der Meldung "Ungültiger Attribut Wert" und werden als **SQL_SS_ORDER_UNSPECIFIED**behandelt. Dies ist der Standardwert für dieses Attribut.|  
|SQL_CA_SS_COLUMN_SORT_ORDINAL|SQLSMALLINT|Gibt die Ordnungszahl einer Tabellenwertparameter-Spalte in einer Gruppe von Spalten an, die die Gesamtreihenfolge für einen Tabellenwertparameter festlegt. Dies kann zu einer verbesserten Abfrageleistung führen. Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind. Die Sortierung der Ordinalzahlen beginnt bei 1. Der Wert 0 ist der Standardwert und gibt eine Tabellenwertparameter-Spalte an, für die keine Spaltenreihenfolge angegeben wurde.|  
|SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE|SQLSMALLINT|Gibt an, ob alle Zeilen im Tabellenwertparameter den Standardwert für diese Spalte enthalten. Für Tabellenwertparameter ist es nicht möglich, den Standardwert auf Zeilenbasis auszuwählen. Der Wert SQL_FALSE gibt an, dass Zeilen nicht standardmäßige Werte enthalten. Dies ist die Standardoption. Der Wert SQL_TRUE gibt an, dass diese Spalte Standardwerte für alle Zeilen enthält.<br /><br /> Wurde der Wert auf SQL_TRUE festgelegt, werden keine Daten an den Server gesendet.<br /><br /> Dieses Feld kann auch mit Identitätsspalten oder berechneten Spalten verwendet werden, wenn die Spaltenwerte nicht für die Serververarbeitung erforderlich sind.|  
||||

 Diese Attribute sind nur für Tabellenwertparameter-Spalten gültig. Sie werden für andere Parameter ignoriert.  
  
 Wenn SQL_CA_SS_COL_HAS_DEFAULT_VALUE für eine Tabellenwertparameter-Spalte festgelegt wurde, muss SQL_DESC_DATA_PTR für diese Spalte ein NULL-Zeiger sein. Andernfalls wird von SQLExecute oder SQLExecDirect SQL_ERROR zurückgegeben. Es wird ein Diagnosedaten Satz mit SQLSTATE = 07s01 und der Meldung "Ungültige Verwendung des Standard Parameters für Parameter \<p> , Spalte \<c> " generiert, wobei \<p> die Parameter Ordinalzahl und \<c> die Spalten Ordnungszahl ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwert Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
