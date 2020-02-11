---
title: Verwendung des Datentyps | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c0ec45270c7ecd33dae1a441499adefabcc61bb3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73779261"
---
# <a name="data-type-usage"></a>Datentypverwendung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Treiber und erzwingen die Verwendung der Datentypen.  
  
|Datentyp|Einschränkung|  
|---------------|----------------|  
|Datumsliterale|Datums Literale, die in einer SQL_TYPE_TIMESTAMP Spalte ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Datentyp von DateTime** oder **smalldatetime**) gespeichert werden, haben den Uhrzeitwert 12:00:00.000 Uhr.|  
|**Money** und **smallmoney**|Nur die ganzzahligen Teile der Datentypen **Money** und **smallmoney** sind von Bedeutung. Wenn der Dezimalteil der SQL- **Money** -Daten während der Datentyp Konvertierung abgeschnitten wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , gibt der Native Client-ODBC-Treiber eine Warnung und keinen Fehler zurück.|  
|SQL_BINARY (NULL zulassen)|Wenn eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 6.0 oder niedriger besteht und eine SQL_BINARY-Spalte NULL-Werte zulässt, werden die in der Datenquelle gespeicherten Daten nicht mit NULL-Werten aufgefüllt. Wenn Daten aus einer solchen Spalte abgerufen werden, füllt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Native Client-ODBC-Treiber ihn mit Nullen auf der rechten Seite auf. Daten, die in von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführten Vorgängen wie Verkettungen erstellt werden, werden jedoch nicht mit NULL-Werten aufgefüllt.<br /><br /> Auch wenn Daten in einer solchen Spalte in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 oder niedriger platziert werden, schneidet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Daten rechts ab, falls sie nicht in die Spalte passen.<br /><br /> Hinweis: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Herstellen einer Verbindung mit 6,5 und früher.|  
|SQL_CHAR (Kürzung)|Wenn während einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 oder niedriger Daten in eine SQL_CHAR-Spalte platziert werden, schneidet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Daten auf der rechten Seite, ohne dass eine Warnung ausgegeben wird, dass die Daten abgeschnitten werden.<br /><br /> Hinweis: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Herstellen einer Verbindung mit 6,5 und früher.|  
|SQL_CHAR (NULL zulassen)|Wenn eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 6.0 oder niedriger besteht und eine SQL_CHAR-Spalte NULL-Werte zulässt, werden die in der Datenquelle gespeicherten Daten nicht mit NULL-Werten aufgefüllt. Wenn Daten aus einer solchen Spalte abgerufen werden, füllt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Native Client-ODBC-Treiber ihn mit Leerzeichen auf der rechten Seite auf. Daten, die in von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführten Vorgängen wie Verkettungen erstellt werden, werden jedoch nicht mit NULL-Werten aufgefüllt.<br /><br /> Hinweis: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Herstellen einer Verbindung mit 6,5 und früher.|  
|SQL_LONGVARBINARY, SQL_LONGVARCHAR, SQL_WLONGVARCHAR|Aktualisierungen von Spalten mit SQL_LONGVARBINARY-, SQL_LONGVARCHAR-oder SQL_WLONGVARCHAR-Datentypen (mit einer WHERE-Klausel), die mehrere Zeilen betreffen, werden vollständig unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stützt, wenn eine Verbindung mit einer Instanz von 6 besteht. *x* und höher. Wenn eine Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von 4,2*x*hergestellt wurde, ist der Fehler "partielle Einfügung/Aktualisierung". Die Einfügung bzw. das Update von Text- oder Imagespalte(n) war nicht erfolgreich." ausgegeben, wenn das Update mehr als eine Zeile betrifft.<br /><br /> Hinweis: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Herstellen einer Verbindung mit 6,5 und früher.|  
|Zeichenfolge-Funktionsparameter|*string_exp* Parameter für die Zeichen folgen Funktionen müssen vom Datentyp SQL_CHAR oder SQL_VARCHAR sein. SQL_LONG_VARCHAR-Datentypen werden in Zeichenfolgenfunktionen nicht unterstützt. Der *count* -Parameter muss kleiner oder gleich 8.000 sein, da die Datentypen SQL_CHAR und SQL_VARCHAR auf eine maximale Länge von 8.000 Zeichen beschränkt sind.|  
|Zeitliterale|Zeit Literale, die in einer SQL_TIMESTAMP Spalte ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Datentyp von DateTime** oder **smalldatetime**) gespeichert sind, haben einen Datumswert vom 1. Januar 1900.|  
|**timestamp**|Nur ein NULL-Wert kann manuell in eine **Zeitstempel** -Spalte eingefügt werden. Da **Zeitstempel**-Spalten jedoch automatisch von aktualisiert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], wird ein NULL-Wert überschrieben.|  
|**tinyint**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **tinyint** -Datentyp ist nicht signiert. Eine **tinyint** -Spalte ist standardmäßig an eine Variable des Datentyps SQL_C_UTINYINT gebunden.|  
|Alias Datentypen|Wenn eine Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von 4,2*x*besteht, fügt der ODBC-Treiber einer Spaltendefinition NULL hinzu, die die NULL-Zulässigkeit einer Spalte nicht explizit deklariert. Deshalb wird der NULL-Zulässigkeitsstatus, der in der Definition eines Aliasdatentyps gespeichert ist, ignoriert.<br /><br /> Wenn eine Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von 4,2*x*besteht, werden Spalten mit einem Alias Datentyp, der den Basis Datentyp **char** oder **Binary** aufweist und für den keine NULL-Zulässigkeit deklariert ist, als der Datentyp **varchar** oder **varbinary**erstellt. [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md)und [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) geben SQL_VARCHAR oder SQL_VARBINARY als Datentyp für diese Spalten zurück. Daten, die von diesen Spalten abgerufen werden, werden nicht aufgefüllt.<br /><br /> Hinweis: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Herstellen einer Verbindung mit 6,5 und früher.|  
|LONG-Datentypen|*Data-at-Execution-* Parameter sind sowohl für die SQL_LONGVARBINARY-als auch für die SQL_LONGVARCHAR-Datentypen beschränkt.|  
|Typen für hohe Werte|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber macht die Typen **varchar (max)**, **varbinary (max)** und **nvarchar (max)** als SQL_VARCHAR, SQL_VARBINARY und SQL_WVARCHAR in APIs verfügbar, die ODBC-SQL-Datentypen akzeptieren oder zurückgeben.|  
|Benutzerdefinierter Typ (User-defined type, UDT)|UDT-Spalten werden als SQL_SS_UDT zugeordnet. Wenn eine UDT-Spalte unter Verwendung der ToString()- oder der ToXMLString()-Methode des UDT oder über die CAST/CONVERT-Funktionen explizit einem anderen Typ in der SQL-Anweisung zugeordnet wird, gibt der Typ der Spalte im Resultset den tatsächlichen Typ wieder, in den die Spalte konvertiert wurde.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber kann nur als Binär an eine UDT-Spalte gebunden werden. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt nur die Konvertierung zwischen den Datentypen SQL_SS_UDT und SQL_C_BINARY.|  
|XML|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konvertiert XML automatisch zu Unicode-Text. Der XML-Typ wird als SQL_SS_XML zugeordnet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeitungsergebnisse &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
