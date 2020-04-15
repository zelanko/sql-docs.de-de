---
title: Datentypverwendung | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data types
- ODBC data types, about ODBC data types
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC]
- SQL Server Native Client ODBC driver, data types
- data types [ODBC], about data types
ms.assetid: 4f19b0d6-94ac-4a98-a121-57d38787864c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0384857c53e898af9fca89bb2ee2351f0b65f986
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297856"
---
# <a name="data-type-usage"></a>Datentypverwendung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-ODBC-Treiber und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erzwingen die folgende Verwendung von Datentypen.  
  
|Datentyp|Einschränkung|  
|---------------|----------------|  
|Datumsliterale|Datumsliterale, wenn in einer[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL_TYPE_TIMESTAMP Spalte gespeichert (Datentypen von **datetime** oder **smalldatetime**), haben einen Zeitwert von 12:00:00.000 A.M.|  
|**Geld** und **Kleingeld**|Nur die ganzzahligen Teile des **Geldes** und **Smallmoney** Datentypen sind signifikant. Wenn der Dezimalteil der **SQL** Money-Daten während der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypkonvertierung abgeschnitten wird, gibt der Native Client ODBC-Treiber eine Warnung und keinen Fehler zurück.|  
|SQL_BINARY (NULL zulassen)|Wenn eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 6.0 oder niedriger besteht und eine SQL_BINARY-Spalte NULL-Werte zulässt, werden die in der Datenquelle gespeicherten Daten nicht mit NULL-Werten aufgefüllt. Wenn Daten aus einer solchen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Spalte abgerufen werden, wird sie vom Native Client ODBC-Treiber mit Nullen auf der rechten Seite aufgesetzt. Daten, die in von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführten Vorgängen wie Verkettungen erstellt werden, werden jedoch nicht mit NULL-Werten aufgefüllt.<br /><br /> Auch wenn Daten in einer solchen Spalte in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 oder niedriger platziert werden, schneidet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Daten rechts ab, falls sie nicht in die Spalte passen.<br /><br /> Hinweis: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Der Native Client ODBC-Treiber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt die Verbindung mit 6.5 und früher.|  
|SQL_CHAR (Kürzung)|Wenn während einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 oder niedriger Daten in eine SQL_CHAR-Spalte platziert werden, schneidet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Daten auf der rechten Seite, ohne dass eine Warnung ausgegeben wird, dass die Daten abgeschnitten werden.<br /><br /> Hinweis: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Der Native Client ODBC-Treiber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt die Verbindung mit 6.5 und früher.|  
|SQL_CHAR (NULL zulassen)|Wenn eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 6.0 oder niedriger besteht und eine SQL_CHAR-Spalte NULL-Werte zulässt, werden die in der Datenquelle gespeicherten Daten nicht mit NULL-Werten aufgefüllt. Wenn Daten aus einer solchen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Spalte abgerufen werden, wird sie vom Native Client ODBC-Treiber mit Leerzeichen auf der rechten Seite aufgepolstert. Daten, die in von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführten Vorgängen wie Verkettungen erstellt werden, werden jedoch nicht mit NULL-Werten aufgefüllt.<br /><br /> Hinweis: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Der Native Client ODBC-Treiber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt die Verbindung mit 6.5 und früher.|  
|SQL_LONGVARBINARY, SQL_LONGVARCHAR, SQL_WLONGVARCHAR|Aktualisierungen von Spalten mit SQL_LONGVARBINARY, SQL_LONGVARCHAR oder SQL_WLONGVARCHAR Datentypen (mit einer WHERE-Klausel), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die mehrere Zeilen betreffen, werden vollständig unterstützt, wenn eine Verbindung mit einer Instanz von 6 erfolgt. *x* und höher. Wenn eine Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit einer Instanz von 4.2*x*verbunden ist, wird ein S1000-Fehler "Partial insert/update. Die Einfügung bzw. das Update von Text- oder Imagespalte(n) war nicht erfolgreich." ausgegeben, wenn das Update mehr als eine Zeile betrifft.<br /><br /> Hinweis: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Der Native Client ODBC-Treiber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt die Verbindung mit 6.5 und früher.|  
|Zeichenfolge-Funktionsparameter|*string_exp* Parameter für die Zeichenfolgenfunktionen müssen vom Datentyp SQL_CHAR oder SQL_VARCHAR sein. SQL_LONG_VARCHAR-Datentypen werden in Zeichenfolgenfunktionen nicht unterstützt. Der *Zählparameter* muss kleiner oder gleich 8.000 sein, da die SQL_CHAR- und SQL_VARCHAR Datentypen auf eine maximale Länge von 8.000 Zeichen beschränkt sind.|  
|Zeitliterale|Zeitliterale, wenn sie in[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einer SQL_TIMESTAMP Spalte (Datentypen von **datetime** oder **smalldatetime**) gespeichert werden, haben den Datumswert 1. Januar 1900.|  
|**Timestamp**|Nur ein NULL-Wert kann manuell in eine **Zeitstempelspalte** eingefügt werden. Da **Zeitstempelspalten**jedoch automatisch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]durch aktualisiert werden, wird ein NULL-Wert überschrieben.|  
|**TINYINT**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **tinyint-Datentyp** ist nicht signiert. Eine **tinyint-Spalte** ist standardmäßig an eine Variable vom Datentyp SQL_C_UTINYINT gebunden.|  
|Alias-Datentypen|Wenn eine Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit einer Instanz von 4.2*x*besteht, fügt der ODBC-Treiber NULL zu einer Spaltendefinition hinzu, die die Nullbarkeit einer Spalte nicht explizit deklariert. Deshalb wird der NULL-Zulässigkeitsstatus, der in der Definition eines Aliasdatentyps gespeichert ist, ignoriert.<br /><br /> Wenn eine Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit einer Instanz von 4.2*x*besteht, werden Spalten mit einem Aliasdatentyp, der einen Basisdatentyp von **char** oder **binary** hat und für den keine NULL-Zulässigkeit deklariert wird, als Datentyp **varchar** oder **varbinary**erstellt. [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md)und [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) geben SQL_VARCHAR oder SQL_VARBINARY als Datentyp für diese Spalten zurück. Daten, die von diesen Spalten abgerufen werden, werden nicht aufgefüllt.<br /><br /> Hinweis: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Der Native Client ODBC-Treiber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt die Verbindung mit 6.5 und früher.|  
|LONG-Datentypen|*Daten-at-Execution-Parameter* sind sowohl für die SQL_LONGVARBINARY- als auch für die SQL_LONGVARCHAR-Datentypen eingeschränkt.|  
|Typen für hohe Werte|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC-Treiber macht **varchar(max)**, **varbinary(max)** und **nvarchar(max)-Typen** als SQL_VARCHAR, SQL_VARBINARY und SQL_WVARCHAR (bzw.) in APIs verfügbar, die ODBC SQL-Datentypen akzeptieren oder zurückgeben.|  
|Benutzerdefinierter Typ (User-defined type, UDT)|UDT-Spalten werden als SQL_SS_UDT zugeordnet. Wenn eine UDT-Spalte unter Verwendung der ToString()- oder der ToXMLString()-Methode des UDT oder über die CAST/CONVERT-Funktionen explizit einem anderen Typ in der SQL-Anweisung zugeordnet wird, gibt der Typ der Spalte im Resultset den tatsächlichen Typ wieder, in den die Spalte konvertiert wurde.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC-Treiber kann nur als Binärdatei an eine UDT-Spalte gebunden werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt nur die Konvertierung zwischen den Datentypen SQL_SS_UDT und SQL_C_BINARY.|  
|XML|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konvertiert XML automatisch zu Unicode-Text. Der XML-Typ wird als SQL_SS_XML zugeordnet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeitungsergebnisse &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
