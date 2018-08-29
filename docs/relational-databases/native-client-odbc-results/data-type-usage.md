---
title: Datentyp-Nutzung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 796abdb998b09e17cc8308bf28448d60bef813f9
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43102494"
---
# <a name="data-type-usage"></a>Datentypverwendung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erzwingen die Verwendung folgende Datentypen.  
  
|Datentyp|Einschränkung|  
|---------------|----------------|  
|Datumsliterale|Datumsliterale, wenn in einer SQL_TYPE_TIMESTAMP-Spalte gespeichert ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen der **"DateTime"** oder **Smalldatetime**), weisen einen Zeitwert von 12:00:00.000 Uhr|  
|**Money** und **Smallmoney**|Nur der ganzzahlige Teile der **Geld** und **Smallmoney** Datentypen sind von Bedeutung. Wenn der Dezimalwert der SQL **Geld** Daten werden abgeschnitten, während der datentypkonvertierung, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber gibt eine Warnung, nicht um einen Fehler zurück.|  
|SQL_BINARY (NULL zulassen)|Wenn eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 6.0 oder niedriger besteht und eine SQL_BINARY-Spalte NULL-Werte zulässt, werden die in der Datenquelle gespeicherten Daten nicht mit NULL-Werten aufgefüllt. Wenn Daten aus einer solchen Spalte abgerufen werden, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber füllt mit Nullen auf der rechten Seite. Daten, die in von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführten Vorgängen wie Verkettungen erstellt werden, werden jedoch nicht mit NULL-Werten aufgefüllt.<br /><br /> Auch wenn Daten in einer solchen Spalte in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 oder niedriger platziert werden, schneidet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Daten rechts ab, falls sie nicht in die Spalte passen.<br /><br /> Hinweis: Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Native Client ODBC-Treiber zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 und früher.|  
|SQL_CHAR (Kürzung)|Wenn während einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 oder niedriger Daten in eine SQL_CHAR-Spalte platziert werden, schneidet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Daten auf der rechten Seite, ohne dass eine Warnung ausgegeben wird, dass die Daten abgeschnitten werden.<br /><br /> Hinweis: Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Native Client ODBC-Treiber zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 und früher.|  
|SQL_CHAR (NULL zulassen)|Wenn eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 6.0 oder niedriger besteht und eine SQL_CHAR-Spalte NULL-Werte zulässt, werden die in der Datenquelle gespeicherten Daten nicht mit NULL-Werten aufgefüllt. Wenn Daten aus einer solchen Spalte abgerufen werden, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber füllt es mit Leerzeichen auf der rechten Seite. Daten, die in von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführten Vorgängen wie Verkettungen erstellt werden, werden jedoch nicht mit NULL-Werten aufgefüllt.<br /><br /> Hinweis: Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Native Client ODBC-Treiber zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 und früher.|  
|SQL_LONGVARBINARY, SQL_LONGVARCHAR, SQL_WLONGVARCHAR|Updates von Spalten mit SQL_LONGVARBINARY, SQL_LONGVARCHAR oder SQL_WLONGVARCHAR-Datentypen (mit einer WHERE-Klausel), die mehrere Zeilen betreffen, werden vollständig unterstützt, bei der Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6. *X* und höher. Beim Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, ein S1000-Fehler, die "partielle(s) Einfügung/Update. Die Einfügung bzw. das Update von Text- oder Imagespalte(n) war nicht erfolgreich." ausgegeben, wenn das Update mehr als eine Zeile betrifft.<br /><br /> Hinweis: Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Native Client ODBC-Treiber zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 und früher.|  
|Zeichenfolge-Funktionsparameter|*String_exp* Geben Sie Parameter für die Zeichenfolge, die Funktionen der Daten muss SQL_CHAR oder SQL_VARCHAR sein. SQL_LONG_VARCHAR-Datentypen werden in Zeichenfolgenfunktionen nicht unterstützt. Die *Anzahl* Parameter muss mit kleiner oder gleich 8.000 sein, da die Datentypen SQL_CHAR und SQL_VARCHAR auf einer maximalen Länge von 8.000 Zeichen beschränkt sind.|  
|Zeitliterale|Zeitliterale, wenn in einer SQL_TYPE_TIMESTAMP-Spalte gespeichert ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen der **"DateTime"** oder **Smalldatetime**), weisen den Datumswert des 1. Januar 1900.|  
|**timestamp**|Nur ein Nullwert kann in manuell eingefügt werden eine **Zeitstempel** Spalte. Aber da **Zeitstempel**Spalten werden automatisch aktualisiert, indem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ein NULL-Wert überschrieben.|  
|**tinyint**|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Tinyint** Datentyp ohne Vorzeichen ist. Ein **Tinyint** Spalte wird standardmäßig auf eine Variable des Datentyps SQL_C_UTINYINT gebunden.|  
|Alias-Datentypen|Beim Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, der ODBC-Treiber fügt NULL für die Spaltendefinition einer, die einer Spalte NULL-Zulässigkeit nicht explizit deklarieren. Deshalb wird der NULL-Zulässigkeitsstatus, der in der Definition eines Aliasdatentyps gespeichert ist, ignoriert.<br /><br /> Beim Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, Spalten mit einem Aliasdatentyp vom Basisdatentyp, der Typ des **Char** oder **binäre** und für die keine NULL-Zulässigkeit ist deklariert werden als Datentyp erstellt **Varchar** oder **Varbinary**. [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md), und [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) geben SQL_VARCHAR oder SQL_VARBINARY als Datentyp für diese Spalten geben. Daten, die von diesen Spalten abgerufen werden, werden nicht aufgefüllt.<br /><br /> Hinweis: Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Native Client ODBC-Treiber zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 und früher.|  
|LONG-Datentypen|*Data-at-Execution-* Parameter sind für die SQL_LONGVARBINARY und SQL_LONGVARCHAR Datentypen beschränkt.|  
|Typen für hohe Werte|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber macht **varchar(max)**, **'varbinary(max)'**, und **nvarchar(max)** Typen als SQL_VARCHAR, SQL_VARBINARY und SQL_ In WVARCHAR-APIs, die akzeptieren oder Zurückgeben der ODBC-SQL-Datentypen.|  
|Benutzerdefinierter Typ (User-defined type, UDT)|UDT-Spalten werden als SQL_SS_UDT zugeordnet. Wenn eine UDT-Spalte unter Verwendung der ToString()- oder der ToXMLString()-Methode des UDT oder über die CAST/CONVERT-Funktionen explizit einem anderen Typ in der SQL-Anweisung zugeordnet wird, gibt der Typ der Spalte im Resultset den tatsächlichen Typ wieder, in den die Spalte konvertiert wurde.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber kann nur an eine UDT-Spalte als Binärdaten gebunden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt nur die Konvertierung zwischen den Datentypen SQL_SS_UDT und SQL_C_BINARY.|  
|XML|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konvertiert XML automatisch zu Unicode-Text. Der XML-Typ wird als SQL_SS_XML zugeordnet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Verarbeiten von Ergebnissen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
