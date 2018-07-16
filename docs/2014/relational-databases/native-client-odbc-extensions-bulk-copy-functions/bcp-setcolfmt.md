---
title: Bcp_setcolfmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_setcolfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_setcolfmt function
ms.assetid: afb47987-39e7-4079-ad66-e0abf4d4c72b
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87ded93fbd666155c36c0bb88a0be80c99c59ff8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410679"
---
# <a name="bcpsetcolfmt"></a>bcp_setcolfmt
  Die **Bcp_setcolfmt** Funktion ersetzt die [Bcp_colfmt](bcp-colfmt.md). Beim Angeben der spaltensortierung, die **Bcp_setcolfmt** Funktion muss verwendet werden. [Bcp_setbulkmode](bcp-setbulkmode.md) können verwendet werden, um mehr als ein Spaltenformat anzugeben.  
  
 Diese Funktion bietet einen flexiblen Ansatz für das Angeben des Spaltenformats in einem Massenkopiervorgang. Sie wird verwendet, um einzelne Spaltenformatattribute festzulegen. Jeder Aufruf von **Bcp_setcolfmt** legt ein spaltenformatattribut.  
  
 Die **Bcp_setcolfmt** Funktion gibt die Quelle oder Ziel-Format der Daten in einer Benutzerdatei an. Bei Verwendung als Quellformat **Bcp_setcolfmt** gibt das Format einer vorhandenen Datendatei verwendet, die als Datenquelle von Daten in einem Massenkopiervorgang in einer Tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bei Verwendung als Zielformat die Datendatei wird erstellt mithilfe der mit angegebenen Spaltenformate **Bcp_setcolfmt**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_setcolfmt (  
HDBC   
hdbc  
,  
INT   
field  
,  
INT   
property  
,  
void*   
pValue  
,  
INT   
cbValue  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *HDBC*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *field*  
 Die Spaltenordnungszahl, für die die Eigenschaft festgelegt wird  
  
 *property*  
 Eine der Eigenschaftskonstanten. Eigenschaftskonstanten werden in dieser Tabelle definiert.  
  
|Eigenschaft|value|Description|  
|--------------|-----------|-----------------|  
|BCP_FMT_TYPE|BYTE|Der Datentyp dieser Spalte in der Benutzerdatei. Wenn die Daten nicht mit dem Datentyp der entsprechenden Spalte in der Datenbanktabelle übereinstimmen, werden die Daten, wenn möglich, durch das Massenkopieren konvertiert.<br /><br /> Der BCP_FMT_TYPE-Parameter wird von den SQL Server-Datentyptoken in sqlncli.h anstelle der ODBC C-Datentypenumeratoren aufgelistet. Sie können beispielsweise eine Zeichenfolge, ODBC-Typ SQL_C_CHAR, mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen SQLCHARACTER-Typs angeben.<br /><br /> Um die Standarddatendarstellung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp anzugeben, legen Sie diesen Parameter auf 0 fest.<br /><br /> Für einen Massenkopiervorgang aus SQL Server in eine Datei, wenn BCP_FMT_TYPE auf SQLDECIMAL oder SQLNUMERIC festgelegt ist:<br /><br /> -Wenn die Quellspalte nicht **decimal** oder **numerischen**, die standardmäßige Genauigkeit und Dezimalstellenanzahl verwendet werden.<br />– Wenn die Quellspalte **decimal** oder **numerischen**, Genauigkeit und Dezimalstellen der Quellspalte verwendet werden.|  
|BCP_FMT_INDICATOR_LEN|INT|Die Länge des Indikators (Präfix) in Bytes<br /><br /> Die Länge eines Längen-/NULL-Indikators innerhalb der Spaltendaten in Bytes. Gültige Indikatorlängenwerte sind 0 (wenn kein Indikator verwendet wird), 1, 2 oder 4.<br /><br /> Legen Sie diesen Parameter auf SQL_VARLEN_DATA fest, um die Verwendung eines standardmäßigen Massenkopierindikators anzugeben.<br /><br /> Indikatoren werden im Speicher direkt vor allen anderen Daten angezeigt. In der Datendatei werden sie direkt vor den Daten, auf die sie sich beziehen, angezeigt.<br /><br /> Wird mehr als eine Methode zur Angabe der Länge der Datendateispalte verwendet (z. B. ein Indikator und eine maximale Spaltenlänge oder ein Indikator und eine Abschlusszeichensequenz), wird beim Massenkopieren die Methode ausgewählt, die zu der kleineren zu kopierenden Datenmenge führt.<br /><br /> Datendateien, die durch Massenkopieren generiert wurden, wobei das Datenformat nicht durch Benutzereingriff angepasst wird, enthalten Indikatoren, wenn die Spaltendaten eine unterschiedliche Länge haben oder die Spalte NULL als Wert akzeptieren kann.|  
|BCP_FMT_DATA_LEN|DBINT|Die Länge der Daten (Spaltenlänge) in Bytes<br /><br /> Dies ist die maximale Länge (in Bytes) der Daten dieser Spalte in der Benutzerdatei, ohne die Länge eines Längenindikators oder Abschlusszeichens.<br /><br /> Durch Festlegen von BCP_FMT_DATA_LEN auf SQL_NULL_DATA wird angegeben, dass alle Werte in der Datendateispalte auf NULL festgelegt sind oder sein sollten.<br /><br /> Wird BCP_FMT_DATA_LEN auf SQL_VARLEN_DATA festgelegt, bedeutet dies, dass das System die Länge der Daten für jede Spalte bestimmen soll. Für einige Spalten könnte dies bedeuten, dass ein Längen-/NULL-Indikator generiert wird, der den Daten in einer Kopie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorangestellt wird, oder dass der Indikator in Daten, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kopiert werden, erwartet wird.<br /><br /> BCP_FMT_DATA_LEN kann für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zeichen und Binärdatentypen BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0 oder ein positiver Wert sein. Wenn BCP_FMT_DATA_LEN auf SQL_VARLEN_DATA festgelegt ist, verwendet das System entweder den Längenindikator, sofern vorhanden, oder eine Abschlusszeichensequenz, um die Länge der Daten zu bestimmen. Wenn sowohl ein Längenindikator als auch eine Abschlusszeichensequenz angegeben sind, wird beim Massenkopieren der Wert verwendet, der zu der kleineren zu kopierenden Datenmenge führt. Ist BCP_FMT_DATA_LEN auf SQL_VARLEN_DATA festgelegt, ist der Datentyp ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zeichen oder -Binärtyp. Ist weder ein Längenindikator noch eine Abschlusszeichensequenz angegeben, gibt das System eine Fehlermeldung zurück.<br /><br /> Wenn BCP_FMT_DATA_LEN 0 oder ein positiver Wert ist, verwendet das System BCP_FMT_DATA_LEN als maximale Datenlänge. Wenn jedoch zusätzlich zu einem positiven BCP_FMT_DATA_LEN-Wert ein Längenindikator oder eine Abschlusszeichensequenz angegeben ist, bestimmt das System die Datenlänge mithilfe der Methode, die zu der kleineren zu kopierenden Datenmenge führt.<br /><br /> Der BCP_FMT_DATA_LEN-Wert stellt die Anzahl der Datenbytes dar. Werden Zeichendaten durch Unicode-Zeichen dargestellt, repräsentiert ein positiver BCP_FMT_DATA_LEN-Parameterwert die Anzahl der Zeichen multipliziert mit der Größe (in Bytes) der einzelnen Zeichen.|  
|BCP_FMT_TERMINATOR|LPCBYTE|Zeiger auf die Abschlusszeichensequenz (entweder ANSI oder Unicode), die für diese Spalte verwendet werden soll. Dieser Parameter ist in erster Linie für Zeichendatentypen nützlich, da alle anderen Typen eine feste Länge besitzen oder, im Falle von Binärdaten, einen Indikator für die Länge erfordern, um die Anzahl der vorhandenen Bytes präzise zu erfassen.<br /><br /> Legen Sie diesen Parameter auf NULL fest, um zu vermeiden, dass extrahierte Daten terminiert werden, oder um anzugeben, dass Daten in einer Benutzerdatei nicht terminiert werden.<br /><br /> Wird mehr als eine Methode zur Angabe der Länge der Benutzerdateispalte verwendet (z. B. ein Abschlusszeichen und ein Längenindikator oder ein Abschlusszeichen und eine maximale Spaltenlänge), wird beim Massenkopieren die Methode ausgewählt, die zu der kleineren zu kopierenden Datenmenge führt.<br /><br /> Die API für das Massenkopieren führt nach Bedarf eine Zeichenkonvertierung von Unicode in MBCS aus. Stellen Sie unbedingt sicher, dass sowohl die Bytezeichenfolge des Abschlusszeichens und die Länge der Bytezeichenfolge richtig festgelegt werden.|  
|BCP_FMT_SERVER_COL|INT|Die Position einer Spalte innerhalb der Datenbank|  
|BCP_FMT_COLLATION|LPCSTR|Sortierungsname.|  
  
 *pValue*  
 Der Zeiger auf den Wert, eine Zuordnung zu den *Eigenschaft*. Er ermöglicht es, jede Spaltenformateigenschaft einzeln festzulegen.  
  
 *cbvalue*  
 Die Länge des Puffers der Eigenschaft in Bytes.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion ersetzt die **Bcp_colfmt** Funktion. Alle Funktionen der **Bcp_colfmt** finden Sie im **Bcp_setcolfmt** Funktion. Zusätzlich wird auch Unterstützung für Spaltensortierung bereitgestellt. Es wird empfohlen, die folgenden Spaltenformatattribute in der unten gegebenen Reihenfolge festzulegen:  
  
 BCP_FMT_SERVER_COL  
  
 BCP_FMT_DATA_LEN  
  
 BCP_FMT_TYPE  
  
 Die **Bcp_setcolfmt** -Funktion können Sie das Benutzerdateiformat für Massenkopieren angeben. Für Massenkopieren besteht ein Format aus folgenden Bestandteilen:  
  
-   Eine Zuordnung von Benutzerdateispalten zu Datenbankspalten  
  
-   Der Datentyp der einzelnen Benutzerdateispalten  
  
-   Die Länge des optionalen Indikators für jede Spalte  
  
-   Die maximale Länge der Daten pro Benutzerdateispalte  
  
-   Die optionale abschließende Bytesequenz für jede Spalte  
  
-   Die Länge der optionalen abschließenden Bytesequenz  
  
 Jeder Aufruf von **Bcp_setcolfmt** gibt das Format für eine benutzerdateispalte an. Z. B. um die Standardeinstellungen für drei Spalten in einer Datendatei für die Benutzer mit fünf Spalten zu ändern, rufen Sie zuerst [Bcp_columns](bcp-columns.md)**(5)**, und rufen dann **Bcp_setcolfmt** fünfmal mit drei dieser Aufrufe Ihr bentuzerdefiniertes Format. Klicken Sie für die verbleibenden zwei Aufrufe BCP_FMT_TYPE auf 0 festgelegt, und legen Sie BCP_FMT_INDICATOR_LENGTH, BCP_FMT_DATA_LEN und *CbValue* auf 0, SQL_VARLEN_DATA und 0 bzw. Mit diesem Verfahren werden alle fünf Spalten kopiert, drei mit dem benutzerdefinierten Format und zwei mit dem Standardformat.  
  
 Die **Bcp_columns** Funktion aufgerufen werden muss, bevor **Bcp_setcolfmt**.  
  
 Rufen Sie **Bcp_setcolfmt** einmal für jede Eigenschaft der einzelnen Spalten in der Benutzerdatei.  
  
 Sie müssen nicht alle Daten in einer Benutzerdatei in eine SQL Server-Tabelle kopieren. Um eine Spalte zu überspringen, geben Sie das Format der Daten für die Spalte an, indem Sie den BCP_FMT_SERVER_COL-Parameter auf 0 festlegen. Wenn Sie eine Spalte überspringen möchten, müssen Sie ihren Typ angeben.  
  
 Die [Bcp_writefmt](bcp-writefmt.md) Funktion kann verwendet werden, um die Formatspezifikation persistent zu speichern.  
  
## <a name="bcpsetcolfmt-support-for-enhanced-date-and-time-features"></a>bcp_setcolfmt-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Mit der BCP_FMT_TYPE-Eigenschaft für Datums-/Uhrzeittypen verwendeten Typen sind, als im angegebenen [Massenkopieränderungen für verbesserte Datums- und Uhrzeittypen &#40;OLEDB- und ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
