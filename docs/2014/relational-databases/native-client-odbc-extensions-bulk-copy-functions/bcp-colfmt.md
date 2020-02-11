---
title: bcp_colfmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colfmt function
ms.assetid: 5c3b6299-80c7-4e84-8e69-4ff33009548e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c583ffad2267a82c39d4ab6c7cd71a1852c7cb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63065458"
---
# <a name="bcp_colfmt"></a>bcp_colfmt
  Gibt das Quell- oder Zielformat der Daten in einer Benutzerdatei an. Bei Verwendung als Quellformat gibt **bcp_colfmt** das Format einer vorhandenen Datendatei an, die als Datenquelle in einem Massen Kopiervorgang in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle verwendet wird. Bei Verwendung als Zielformat wird die Datendatei mithilfe der mit **bcp_colfmt**angegebenen Spalten Formate erstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_colfmt (  
HDBC   
hdbc  
,  
INT  
idxUserDataCol  
,  
BYTE   
eUserDataType  
,  
INT   
cbIndicator  
,  
DBINT   
cbUserData  
,  
LPCBYTE   
pUserDataTerm  
,  
INT   
cbUserDataTerm  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *idxUserDataCol*  
 Die Ordnungsnummer der Spalte in der Benutzerdatendatei, für die das Format angegeben wird. Die erste Spalte ist 1.  
  
 *eUserDataType*  
 Der Datentyp dieser Spalte in der Benutzerdatei. Wenn Sie sich vom Datentyp der entsprechenden Spalte in der Datenbanktabelle (*idxServerColumn*) unterscheiden, werden die Daten nach Möglichkeit durch Massen kopieren konvertiert.  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]in wurde die Unterstützung für die Datentyp Token SQLXML und SQLUDT im *eUserDataType* -Parameter eingeführt.  
  
 Der *eUserDataType* -Parameter wird durch die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp Token in sqlncli. h, nicht die ODBC-C-Datentyp Enumeratoren, aufgelistet. Sie können beispielsweise mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen SQLCHARACTER-Typs eine Zeichenfolge vom ODBC-Typ SQL_C_CHAR angeben.  
  
 Um die Standarddatendarstellung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp anzugeben, legen Sie diesen Parameter auf 0 fest.  
  
 Bei einem Massen Kopiervorgang aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in eine Datei, wenn *eUserDataType* SqlDecimal oder SQLNUMERIC lautet:  
  
-   Wenn die Quell Spalte nicht **Dezimal** oder **numerisch**ist, werden die Standardgenauigkeit und die Standardskala verwendet.  
  
-   Wenn die Quell Spalte **Dezimal** oder **numerisch**ist, werden die Genauigkeit und die Dezimalstellen der Quell Spalte verwendet.  
  
 *cbIndicator*  
 Die Länge eines Längen-/NULL-Indikators innerhalb der Spaltendaten in Byte. Gültige Indikatorlängenwerte sind 0 (wenn kein Indikator verwendet wird), 1, 2, 4 oder 8.  
  
 Legen Sie diesen Parameter auf SQL_VARLEN_DATA fest, um die Verwendung eines standardmäßigen Massenkopierindikators anzugeben.  
  
 Indikatoren werden im Speicher direkt vor allen anderen Daten angezeigt. In der Datendatei werden sie direkt vor den Daten, auf die sie sich beziehen, angezeigt.  
  
 Wird mehr als eine Methode zur Angabe der Länge der Datendateispalte verwendet (z. B. ein Indikator und eine maximale Spaltenlänge oder ein Indikator und eine Abschlusszeichensequenz), wird beim Massenkopieren die Methode ausgewählt, die zu der kleineren zu kopierenden Datenmenge führt.  
  
 Datendateien, die durch Massenkopieren generiert wurden, wobei das Datenformat nicht durch Benutzereingriff angepasst wird, enthalten Indikatoren, wenn die Spaltendaten eine unterschiedliche Länge haben oder die Spalte NULL als Wert akzeptieren kann.  
  
 *cbUserData*  
 Die maximale Länge (in Byte) der Daten dieser Spalte in der Benutzerdatei, ohne die Länge eines Längenindikators oder Abschlusszeichens.  
  
 Wenn *cbUserData* auf SQL_NULL_DATA festgelegt wird, wird angegeben, dass alle Werte in der Datendatei Spalte auf NULL festgelegt werden sollen.  
  
 Durch Festlegen von *cbUserData* auf SQL_VARLEN_DATA wird angegeben, dass das System die Länge der Daten in den einzelnen Spalten bestimmen soll. Für einige Spalten könnte dies bedeuten, dass ein Längen-/NULL-Indikator generiert wird, der den Daten in einer Kopie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorangestellt wird, oder dass der Indikator in Daten, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kopiert werden, erwartet wird.  
  
 Bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeichen-und Binär Datentypen kann *cbUserData* SQL_VARLEN_DATA, SQL_NULL_DATA, 0 oder ein positiver Wert sein. Wenn *cbUserData* SQL_VARLEN_DATA ist, verwendet das System entweder den Längen Indikator, falls vorhanden, oder eine Abschluss Zeichen Sequenz, um die Länge der Daten zu bestimmen. Wenn sowohl ein Längenindikator als auch eine Abschlusszeichensequenz angegeben sind, wird beim Massenkopieren der Wert verwendet, der zu der kleineren zu kopierenden Datenmenge führt. Wenn *cbUserData* SQL_VARLEN_DATA ist, der Datentyp ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeichen-oder Binärtyp ist und weder ein Längen Indikator noch eine Abschluss Zeichen Sequenz angegeben ist, gibt das System eine Fehlermeldung zurück.  
  
 Wenn *cbUserData* 0 oder ein positiver Wert ist, verwendet das System *cbUserData* als maximale Datenlänge. Wenn jedoch zusätzlich zu einem positiven *cbUserData*-Wert ein Längenindikator oder eine Abschlusszeichensequenz angegeben ist, bestimmt das System die Datenlänge mit der Methode, die zu der kleineren zu kopierenden Datenmenge führt.  
  
 Der *cbUserData* -Wert stellt die Anzahl der Datenbytes dar. Werden Zeichendaten durch Unicode-Zeichen dargestellt, repräsentiert ein positiver *cbUserData* -Parameterwert die Anzahl der Zeichen multipliziert mit der Größe (in Byte) der einzelnen Zeichen.  
  
 *pUserDataTerm*  
 Die Abschlusszeichensequenz, die für diese Spalte verwendet werden soll. Dieser Parameter ist in erster Linie für Zeichendatentypen nützlich, da alle anderen Typen eine feste Länge besitzen oder, im Falle von Binärdaten, einen Indikator für die Länge erfordern, um die Anzahl der vorhandenen Bytes präzise zu erfassen.  
  
 Legen Sie diesen Parameter auf NULL fest, um zu vermeiden, dass extrahierte Daten terminiert werden, oder um anzugeben, dass Daten in einer Benutzerdatei nicht terminiert werden.  
  
 Wird mehr als eine Methode zur Angabe der Länge der Benutzerdateispalte verwendet (z. B. ein Abschlusszeichen und ein Längenindikator oder ein Abschlusszeichen und eine maximale Spaltenlänge), wird beim Massenkopieren die Methode ausgewählt, die zu der kleineren zu kopierenden Datenmenge führt.  
  
 Die API für das Massenkopieren führt nach Bedarf eine Zeichenkonvertierung von Unicode in MBCS aus. Stellen Sie unbedingt sicher, dass sowohl die Bytezeichenfolge des Abschlusszeichens und die Länge der Bytezeichenfolge richtig festgelegt werden.  
  
 *cbUserDataTerm*  
 Die Länge (in Byte) der Abschlusszeichensequenz, die für diese Spalte verwendet werden soll. Wenn kein Abschlusszeichen vorhanden ist oder in den Daten gewünscht wird, legen Sie diesen Wert auf 0 fest.  
  
 *idxServerCol*  
 Die Ordinalposition der Spalte in der Datenbanktabelle. Die erste Spaltennummer ist 1. Die Ordnungsposition einer Spalte wird von [SQLColumns](../native-client-odbc-api/sqlcolumns.md)ausgegeben.  
  
 Wenn dieser Wert 0 ist, wird beim Massenkopieren die Spalte in der Datendatei ignoriert.  
  
## <a name="returns"></a>Rückgabe  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der **bcp_colfmt** -Funktion können Sie das Benutzerdatei Format für Massen Kopien angeben. Für Massenkopieren besteht ein Format aus folgenden Bestandteilen:  
  
-   Eine Zuordnung von Benutzerdateispalten zu Datenbankspalten  
  
-   Der Datentyp der einzelnen Benutzerdateispalten  
  
-   Die Länge des optionalen Indikators für jede Spalte  
  
-   Die maximale Länge der Daten pro Benutzerdateispalte  
  
-   Die optionale abschließende Bytesequenz für jede Spalte  
  
-   Die Länge der optionalen abschließenden Bytesequenz  
  
 Jeder **bcp_colfmt** Aufrufe gibt das Format für eine Benutzerdatei Spalte an. Wenn Sie z. b. die Standardeinstellungen für drei Spalten in einer Benutzer Datendatei mit fünf Spalten ändern möchten, rufen Sie zuerst [bcp_columns](bcp-columns.md)**(5)** auf, und rufen Sie dann **bcp_colfmt** fünfmal auf, wobei drei dieser Aufrufe Ihr benutzerdefiniertes Format festlegen. Legen Sie für die verbleibenden zwei Aufrufe *eUserDataType* auf 0 fest, und legen Sie *cbIndicator*, *cbUserData*und *cbUserDataTerm* auf 0, SQL_VARLEN_DATA bzw. 0 fest. Mit diesem Verfahren werden alle fünf Spalten kopiert, drei mit dem benutzerdefinierten Format und zwei mit dem Standardformat.  
  
 Für *cbIndicator*ist der Wert 8, um anzugeben, dass ein großer Werttyp nun gültig ist. Wenn das Präfix für ein Feld angegeben wird, dessen entsprechende Spalte den neuen max-Typ aufweist, kann dafür nur 8 festgelegt werden. Weitere Informationen finden Sie unter [bcp_bind](bcp-bind.md).  
  
 Die **bcp_columns** -Funktion muss vor allen Aufrufen von **bcp_colfmt**aufgerufen werden.  
  
 Sie müssen **bcp_colfmt** einmal für jede Spalte in der Benutzerdatei abrufen.  
  
 Wenn Sie **bcp_colfmt** mehr als einmal für eine Benutzerdatei Spalte aufrufen, wird ein Fehler verursacht.  
  
 Sie brauchen nicht alle Daten in einer Benutzerdatei in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle kopieren. Um eine Spalte zu überspringen, geben Sie das Format der Daten für die Spalte an, indem Sie den *idxServerCol* -Parameter auf 0 festlegen. Wenn Sie eine Spalte überspringen möchten, müssen Sie ihren Typ angeben.  
  
 Die [bcp_writefmt](bcp-writefmt.md) -Funktion kann verwendet werden, um die Format Spezifikation beizubehalten.  
  
## <a name="bcp_colfmt-support-for-enhanced-date-and-time-features"></a>'bcp_colfmt'-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Informationen zu den Typen, die mit dem *eUserDataType* -Parameter für Datums-/Uhrzeittypen verwendet werden, finden Sie unter [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeittypen &#40;OLE DB und ODBC-&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
