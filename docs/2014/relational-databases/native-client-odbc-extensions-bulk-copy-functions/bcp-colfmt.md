---
title: Bcp_colfmt | Microsoft-Dokumentation
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
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089280"
---
# <a name="bcpcolfmt"></a>bcp_colfmt
  Gibt das Quell- oder Zielformat der Daten in einer Benutzerdatei an. Bei Verwendung als Quellformat **Bcp_colfmt** gibt das Format einer vorhandenen Datendatei verwendet, die als Quelle der Daten in einem Massenkopiervorgang in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle. Bei Verwendung als Zielformat die Datendatei wird erstellt mithilfe der mit angegebenen Spaltenformate **Bcp_colfmt**.  
  
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
 *HDBC*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *idxUserDataCol*  
 Die Ordnungsnummer der Spalte in der Benutzerdatendatei, für die das Format angegeben wird. Die erste Spalte ist 1.  
  
 *eUserDataType*  
 Der Datentyp dieser Spalte in der Benutzerdatei. Wenn der Datentyp der entsprechenden Spalte in der Datenbanktabelle (*IdxServerColumn*), das Massenkopieren konvertiert die Daten Wenn möglich.  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Unterstützung für SQLXML und SQLUDT Datentyptoken in die *eUserDataType* Parameter.  
  
 Die *eUserDataType* Parameter aufgelistet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyptoken in sqlncli.h, nicht die ODBC-C-datentypenumeratoren. Sie können beispielsweise mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen SQLCHARACTER-Typs eine Zeichenfolge vom ODBC-Typ SQL_C_CHAR angeben.  
  
 Um die Standarddatendarstellung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp anzugeben, legen Sie diesen Parameter auf 0 fest.  
  
 Für einen Massenkopiervorgang von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in eine Datei, wenn *eUserDataType* SQLDECIMAL oder sqlnumeric festgelegt:  
  
-   Wenn die Quellspalte nicht **decimal** oder **numerischen**, werden verwendet, die standardmäßige Genauigkeit und Dezimalstellenanzahl.  
  
-   Wenn die Quellspalte **decimal** oder **numerischen**, Genauigkeit und Dezimalstellen der Quellspalte verwendet werden.  
  
 *cbIndicator*  
 Die Länge eines Längen-/NULL-Indikators innerhalb der Spaltendaten in Byte. Gültige Indikatorlängenwerte sind 0 (wenn kein Indikator verwendet wird), 1, 2, 4 oder 8.  
  
 Legen Sie diesen Parameter auf SQL_VARLEN_DATA fest, um die Verwendung eines standardmäßigen Massenkopierindikators anzugeben.  
  
 Indikatoren werden im Speicher direkt vor allen anderen Daten angezeigt. In der Datendatei werden sie direkt vor den Daten, auf die sie sich beziehen, angezeigt.  
  
 Wird mehr als eine Methode zur Angabe der Länge der Datendateispalte verwendet (z. B. ein Indikator und eine maximale Spaltenlänge oder ein Indikator und eine Abschlusszeichensequenz), wird beim Massenkopieren die Methode ausgewählt, die zu der kleineren zu kopierenden Datenmenge führt.  
  
 Datendateien, die durch Massenkopieren generiert wurden, wobei das Datenformat nicht durch Benutzereingriff angepasst wird, enthalten Indikatoren, wenn die Spaltendaten eine unterschiedliche Länge haben oder die Spalte NULL als Wert akzeptieren kann.  
  
 *cbUserData*  
 Die maximale Länge (in Byte) der Daten dieser Spalte in der Benutzerdatei, ohne die Länge eines Längenindikators oder Abschlusszeichens.  
  
 Festlegen von *CbUserData* auf SQL_NULL_DATA wird angegeben, dass alle Werte in der datendateispalte sind, oder auf NULL festgelegt werden soll.  
  
 Festlegen von *CbUserData* auf SQL_VARLEN_DATA gibt an, dass das System die Länge der Daten in jeder Spalte bestimmen soll. Für einige Spalten könnte dies bedeuten, dass ein Längen-/NULL-Indikator generiert wird, der den Daten in einer Kopie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorangestellt wird, oder dass der Indikator in Daten, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kopiert werden, erwartet wird.  
  
 Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zeichen und Binärdatentypen *CbUserData* bcp_length_variable, bcp_length_null, 0 oder ein positiver Wert sein kann. Wenn *CbUserData* auf sql_varlen_data festgelegt, verwendet das System entweder den Längenindikator, sofern vorhanden, oder eine abschlusszeichensequenz, um die Länge der Daten zu bestimmen. Wenn sowohl ein Längenindikator als auch eine Abschlusszeichensequenz angegeben sind, wird beim Massenkopieren der Wert verwendet, der zu der kleineren zu kopierenden Datenmenge führt. Wenn *CbUserData* auf sql_varlen_data festgelegt, die Daten der Typ ist ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeichen oder Binärtyp, und weder ein Längenindikator noch eine abschlusszeichensequenz angegeben ist, gibt das System eine Fehlermeldung zurück.  
  
 Wenn *CbUserData* 0 oder ein positiver Wert sein, das System verwendet *CbUserData* als maximale Datenlänge. Allerdings If, zusätzlich zu einem positiven *CbUserData*, ein Länge Längenindikator oder eine abschlusszeichensequenz angegeben ist, bestimmt das System die Datenlänge mithilfe der Methode, die sich ergibt die geringste Menge an Daten, die kopiert wird.  
  
 Die *CbUserData* Wert stellt die Anzahl der Datenbytes dar. Wenn Zeichendaten durch Unicode-Zeichen, und klicken Sie dann auf ein positives Ergebnis dargestellt werden *CbUserData* Parameterwert darstellt, die Anzahl der Zeichen multipliziert mit der Größe der einzelnen Zeichen in Bytes.  
  
 *pUserDataTerm*  
 Die Abschlusszeichensequenz, die für diese Spalte verwendet werden soll. Dieser Parameter ist in erster Linie für Zeichendatentypen nützlich, da alle anderen Typen eine feste Länge besitzen oder, im Falle von Binärdaten, einen Indikator für die Länge erfordern, um die Anzahl der vorhandenen Bytes präzise zu erfassen.  
  
 Legen Sie diesen Parameter auf NULL fest, um zu vermeiden, dass extrahierte Daten terminiert werden, oder um anzugeben, dass Daten in einer Benutzerdatei nicht terminiert werden.  
  
 Wird mehr als eine Methode zur Angabe der Länge der Benutzerdateispalte verwendet (z. B. ein Abschlusszeichen und ein Längenindikator oder ein Abschlusszeichen und eine maximale Spaltenlänge), wird beim Massenkopieren die Methode ausgewählt, die zu der kleineren zu kopierenden Datenmenge führt.  
  
 Die API für das Massenkopieren führt nach Bedarf eine Zeichenkonvertierung von Unicode in MBCS aus. Stellen Sie unbedingt sicher, dass sowohl die Bytezeichenfolge des Abschlusszeichens und die Länge der Bytezeichenfolge richtig festgelegt werden.  
  
 *cbUserDataTerm*  
 Die Länge (in Byte) der Abschlusszeichensequenz, die für diese Spalte verwendet werden soll. Wenn kein Abschlusszeichen vorhanden ist oder in den Daten gewünscht wird, legen Sie diesen Wert auf 0 fest.  
  
 *idxServerCol*  
 Ist die Ordnungsposition der Spalte in der Datenbanktabelle an. Die erste Spaltennummer ist 1. Die Ordnungsposition einer Spalte wird von [SQLColumns](../native-client-odbc-api/sqlcolumns.md)ausgegeben.  
  
 Wenn dieser Wert 0 ist, wird beim Massenkopieren die Spalte in der Datendatei ignoriert.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Die **Bcp_colfmt** -Funktion können Sie das Benutzerdateiformat für Massenkopieren angeben. Für Massenkopieren besteht ein Format aus folgenden Bestandteilen:  
  
-   Eine Zuordnung von Benutzerdateispalten zu Datenbankspalten  
  
-   Der Datentyp der einzelnen Benutzerdateispalten  
  
-   Die Länge des optionalen Indikators für jede Spalte  
  
-   Die maximale Länge der Daten pro Benutzerdateispalte  
  
-   Die optionale abschließende Bytesequenz für jede Spalte  
  
-   Die Länge der optionalen abschließenden Bytesequenz  
  
 Jeder Aufruf von **Bcp_colfmt** gibt das Format für eine benutzerdateispalte an. Z. B. um die Standardeinstellungen für drei Spalten in einer Datendatei für die Benutzer mit fünf Spalten zu ändern, rufen Sie zuerst [Bcp_columns](bcp-columns.md)**(5)**, und rufen dann **Bcp_colfmt** fünfmal, drei dieser Aufrufe Ihr bentuzerdefiniertes Format. Legen Sie für die verbleibenden zwei Aufrufe *eUserDataType* auf 0 und *CbIndicator*, *CbUserData*, und *CbUserDataTerm* auf 0 (null) SQL_VARLEN "_Data", und 0 bzw. Mit diesem Verfahren werden alle fünf Spalten kopiert, drei mit dem benutzerdefinierten Format und zwei mit dem Standardformat.  
  
 Für *CbIndicator*, ein Wert von 8, um einen großen Werttyp anzugeben ist jetzt gültig. Wenn das Präfix für ein Feld angegeben wird, dessen entsprechende Spalte den neuen max-Typ aufweist, kann dafür nur 8 festgelegt werden. Weitere Informationen finden Sie unter [Bcp_bind](bcp-bind.md).  
  
 Die **Bcp_columns** -Funktion muss aufgerufen werden, vor allen Aufrufen von **Bcp_colfmt**.  
  
 Rufen Sie **Bcp_colfmt** einmal für jede Spalte in der Benutzerdatei.  
  
 Aufrufen von **Bcp_colfmt** mehr als einmal für eine benutzerdateispalte einen Fehler.  
  
 Sie brauchen nicht alle Daten in einer Benutzerdatei in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle kopieren. Um eine Spalte zu überspringen, geben Sie das Format der Daten für die Spalte an, indem die *IdxServerCol* Parameter auf 0. Wenn Sie eine Spalte überspringen möchten, müssen Sie ihren Typ angeben.  
  
 Die [Bcp_writefmt](bcp-writefmt.md) Funktion kann verwendet werden, um die Formatspezifikation persistent zu speichern.  
  
## <a name="bcpcolfmt-support-for-enhanced-date-and-time-features"></a>'bcp_colfmt'-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Informationen über Typen verwendet, mit der *eUserDataType* -Parameter für Datum/Uhrzeit-Datentypen, finden Sie unter [Massenkopieränderungen für verbesserte Datums- und Uhrzeittypen &#40;OLEDB- und ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
