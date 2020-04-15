---
title: Deskriptorfeld für Tabellenwertparameter
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
ms.openlocfilehash: 08074ad57ca4f0e4f7c2c56d9eca595baf595b5f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297853"
---
# <a name="descriptor-fields-for-table-valued-parameter-constituent-columns"></a>Deskriptorfelder für aus Tabellenwertparameter bestehenden Spalten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die in diesem Abschnitt beschriebenen Parameterdeskriptorfelder mit Tabellenwert werden mithilfe von [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md) und [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md) mit dem Handle für den Implementierungsparameterdeskriptor (IPD) bearbeitet.  
  
## <a name="remarks"></a>Bemerkungen  
 SQL_DESC_AUTO_UNIQUE_VALUE wird für Tabellenwertparameter sowie für andere Funktionen verwendet.  
  
|Attributname|type|BESCHREIBUNG|  
|--------------------|----------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|SQL_TRUE gibt an, dass es sich bei dieser Spalte um eine Identitätsspalte handelt.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]können diese Informationen verwenden, um die Leistung zu optimieren, aber Anwendungen sind nicht erforderlich, um sie für Identitätsspalten festzulegen.|  
||||

 Die folgenden Attribute werden allen Parametertypen im Anwendungsparameterdeskriptor (Application Parameter Descriptor, APD) und Implementierungsparameterdeskriptor (Implementation Parameter Descriptor, IPD) hinzugefügt:  
  
|Attributname|type|BESCHREIBUNG|  
|--------------------|----------|-----------------|  
|SQL_CA_SS_COLUMN_COMPUTED|SQLSMALLINT|SQL_TRUE gibt an, dass diese Spalte berechnet wird.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]können diese Informationen verwenden, um die Leistung zu optimieren, aber Anwendungen sind nicht erforderlich, um sie für berechnete Spalten festzulegen.<br /><br /> Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind.|  
|SQL_CA_SS_COLUMN_IN_UNIQUE_KEY|SQLSMALLINT|SQL_TRUE gibt an, dass eine Tabellenwertparameter-Spalte zu einem eindeutigen Schlüssel gehört. Dies kann zu einer verbesserten Abfrageleistung führen. Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind.|  
|SQL_CA_SS_COLUMN_SORT_ORDER|SQLSMALLINT|Gibt die Sortierreihenfolge einer Tabellenwertparameter-Spalte an. Dies kann zu einer verbesserten Abfrageleistung führen. Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind. Die möglichen Werte sind die folgenden: <br />**SQL_SS_ASCENDING_ORDER**<br />**SQL_SS_DESCENDING_ORDER**<br />**SQL_SS_ORDER_UNSPECIFIED**<br /><br /> Andere Werte als **SQL_SS_ASCENDING_ORDER** und **SQL_SS_DESCENDING_ORDER** einen Fehler mit **SQLSTATE HY024** und der Meldung 'Ungültiger Attributwert' generieren und werden als **SQL_SS_ORDER_UNSPECIFIED**behandelt, was der Standardwert für dieses Attribut ist.|  
|SQL_CA_SS_COLUMN_SORT_ORDINAL|SQLSMALLINT|Gibt die Ordnungszahl einer Tabellenwertparameter-Spalte in einer Gruppe von Spalten an, die die Gesamtreihenfolge für einen Tabellenwertparameter festlegt. Dies kann zu einer verbesserten Abfrageleistung führen. Dieses Attribut wird für Bindungen ignoriert, die keine Tabellenwertparameter-Spalten sind. Die Sortierung der Ordinalzahlen beginnt bei 1. Der Wert 0 ist der Standardwert und gibt eine Tabellenwertparameter-Spalte an, für die keine Spaltenreihenfolge angegeben wurde.|  
|SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE|SQLSMALLINT|Gibt an, ob alle Zeilen im Tabellenwertparameter den Standardwert für diese Spalte enthalten. Für Tabellenwertparameter ist es nicht möglich, den Standardwert auf Zeilenbasis auszuwählen. Der Wert SQL_FALSE gibt an, dass Zeilen nicht standardmäßige Werte enthalten. Dies ist die Standardoption. Der Wert SQL_TRUE gibt an, dass diese Spalte Standardwerte für alle Zeilen enthält.<br /><br /> Wurde der Wert auf SQL_TRUE festgelegt, werden keine Daten an den Server gesendet.<br /><br /> Dieses Feld kann auch mit Identitätsspalten oder berechneten Spalten verwendet werden, wenn die Spaltenwerte nicht für die Serververarbeitung erforderlich sind.|  
||||

 Diese Attribute sind nur für Tabellenwertparameter-Spalten gültig. Sie werden für andere Parameter ignoriert.  
  
 Wenn SQL_CA_SS_COL_HAS_DEFAULT_VALUE für eine Tabellenwertparameter-Spalte festgelegt wurde, muss SQL_DESC_DATA_PTR für diese Spalte ein NULL-Zeiger sein. Andernfalls geben SQLExecute oder SQLExecDirect SQL_ERROR zurück. Ein Diagnosedatensatz wird mit SQLSTATE=07S01 und der Meldung "Ungültige \<Verwendung des \<Standardparameters \<für Parameter p>, Spalte \<c>" generiert, wobei p> der Parameter ordinal und c> die Spalte ordinal ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenbewertete Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
