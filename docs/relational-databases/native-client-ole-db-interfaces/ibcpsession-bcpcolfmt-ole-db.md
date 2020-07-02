---
title: IBCPSession::BCPColFmt (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPColFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPColFmt method
ms.assetid: 2852f4ba-f1c6-4c4c-86b2-b77e4abe70de
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d03eea8744bce4176551264b10cf2b90507b3473
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85724842"
---
# <a name="ibcpsessionbcpcolfmt-ole-db"></a>IBCPSession::BCPColFmt (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Erstellt eine Bindung zwischen Programmvariablen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Spalten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPColFmt(   
      DBORDINAL idxUserDataCol,  
      int eUserDataType,  
      int cbIndicator,  
      int cbUserData,  
      BYTE *pbUserDataTerm,  
      int cbUserDataTerm,  
      DBORDINAL idxServerCol);  
```  
  
## <a name="remarks"></a>Hinweise  
 Die **BCPColFmt**-Methode wird verwendet, um eine Bindung zwischen BCP-Datendateifeldern und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalten zu erstellen. Sie nimmt Länge, Typ, Abschlusszeichen und Präfixlänge einer Spalte als Parameter auf und legt jede dieser Eigenschaften für einzelne Felder fest.  
  
 Wenn der Benutzer die interaktive Methode wählt, wird diese Methode zweimal aufgerufen: einmal zum Festlegen des Spaltenformats den Standardwerten entsprechend (die sich nach dem Typ der Serverspalte richten) und einmal, um das Format für jede Spalte dem Spaltentyp der Wahl des Clients entsprechend festzulegen, der im interaktiven Modus ausgewählt wurde.  
  
 In nicht interaktiven Modi wird die Methode nur einmal pro Spalte aufgerufen, um den Typ der einzelnen Spalten auf den Zeichen- oder systemeigenen Typ festzulegen und die Spalten- und Zeilenabschlusszeichen festzulegen.  
  
 Mit der **BCPColFmt** -Methode können Sie das Benutzerdateiformat für Massenkopieren angeben. Für Massenkopieren besteht ein Format aus folgenden Bestandteilen:  
  
-   Eine Zuordnung von Benutzerdateifeldern zu Datenbankspalten  
  
-   Der Datentyp der einzelnen Benutzerdateifelder  
  
-   Die Länge des optionalen Indikators für jedes Feld  
  
-   Die maximale Länge der Daten pro Benutzerdateifeld  
  
-   Die optionale abschließende Bytesequenz für jedes Feld  
  
-   Die Länge der optionalen abschließenden Bytesequenz  
  
 Jeder Aufruf von **BCPColFmt** gibt das Format für ein Benutzerdateifeld an. Um die Standardeinstellungen für drei Felder in einer aus fünf Feldern bestehenden Benutzerdatendatei zu ändern, rufen Sie zuerst `BCPColumns(5)`auf und anschließend fünf Mal **BCPColFmt** , wobei mit drei dieser Aufrufe Ihr bentuzerdefiniertes Format festgelegt wird. Legen Sie für die restlichen zwei Aufrufe *eUserDataType* auf BCP_TYPE_DEFAULT und *cbIndicator*, *cbUserData*und *cbUserDataTerm* auf 0, BCP_VARIABLE_LENGTH bzw. 0 fest. Mit diesem Verfahren werden alle fünf Spalten kopiert, drei mit dem benutzerdefinierten Format und zwei mit dem Standardformat.  
  
> [!NOTE]  
>  Die [IBCPSession::BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)-Methode muss vor einem Aufruf von **BCPColFmt** aufgerufen werden. Sie müssen **BCPColFmt** einmal für jede Spalte in der Benutzerdatei aufrufen. Wird **BCPColFmt** mehr als einmal für eine Benutzerdateispalte aufgerufen, tritt ein Fehler auf.  
  
 Sie müssen nicht alle Daten in einer Benutzerdatei in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle kopieren. Um eine Spalte zu überspringen, geben Sie das Format der Daten für die Spalte an, indem Sie den idxServerCol-Parameter auf 0 festlegen. Um ein Feld zu überspringen, sind dennoch alle Informationen erforderlich, damit die Methode ordnungsgemäß funktioniert.  
  
 **Hinweis:** Mit der [IBCPSession::BCPWriteFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)-Funktion kann die über **BCPColFmt** zur Verfügung gestellte Formatspezifikation permanent gespeichert werden.  
  
## <a name="arguments"></a>Argumente  
 *idxUserDataCol*[in]  
 Der Feldindex in der Datendatei des Benutzers  
  
 *eUserDataType*[in]  
 Der Felddatentyp in der Datendatei des Benutzers. Die verfügbaren Datentypen werden in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Headerdatei (sqlncli.h) im Format BCP_TYPE_XXX aufgeführt, z. B. BCP_TYPE_SQLINT4. Ist der BCP_TYPE_DEFAULT-Wert festgelegt, versucht der Anbieter den gleichen Typ zu verwenden wie der Tabellen- oder Sichtspaltentyp. Wenn das **eUserDataType**-Argument BCP_TYPE_SQLDECIMAL oder BCP_TYPE_SQLNUMERIC lautet, gilt für Massenkopiervorgänge aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in eine Datei:  
  
-   Wenn die Quellspalte nicht dezimal oder numerisch ist, werden die Standardgenauigkeit und die Standardanzahl von Dezimalstellen verwendet.  
  
-   Wenn die Quellspalte dezimal oder numerisch ist, werden die Genauigkeit und die Anzahl von Dezimalstellen der Quellspalte verwendet.  
  
 *cbIndicator*[in]  
 Die Präfixlänge für das Feld. Der Standardwert ist BCP_PREFIX_DEFAULT. Gültige Präfixlängen sind 0, 1, 2, 4 und 8. Eine Präfixgröße von 8 wird üblicherweise verwendet, um anzugeben, dass das Feld segmentiert ist. Dies wird zum effizienten Massenkopieren von großen Werttypspalten verwendet.  
  
 *cbUserData*[in]  
 Die maximale Länge (in Byte) der Daten in diesem Feld der Benutzerdatei, ohne die Länge eines Längenindikators oder Abschlusszeichens  
  
 Durch Festlegen von **cbUserData** auf BCP_LENGTH_NULL wird angegeben, dass alle Werte in den Datendateifeldern auf NULL festgelegt sind oder sein sollten. Ist **cbUserData** auf BCP_LENGTH_VARIABLE festgelegt, bedeutet dies, dass das System die Länge der Daten für jedes Feld bestimmen soll. Für einige Felder könnte dies bedeuten, dass ein Längen-/NULL-Indikator generiert wird, der den Daten in einer Kopie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorangestellt wird, oder dass der Indikator in Daten erwartet wird, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kopiert werden.  
  
 Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zeichentypen und Binärdatentypen kann **cbUserData** BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0 oder ein positiver Wert sein. Wenn **cbUserData** auf BCP_LENGTH_VARIABLE festgelegt ist, verwendet das System entweder den Längenindikator, sofern vorhanden, oder eine Abschlusszeichensequenz, um die Länge der Daten zu bestimmen. Wenn sowohl ein Längenindikator als auch eine Abschlusszeichensequenz angegeben sind, wird beim Massenkopieren der Wert verwendet, der zu der kleineren zu kopierenden Datenmenge führt. Ist **cbUserData** auf BCP_LENGTH_VARIABLE festgelegt, ist der Datentyp ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zeichentyp oder Binärtyp, und sind weder ein Längenindikator noch eine Abschlusszeichensequenz angegeben, gibt das System eine Fehlermeldung zurück.  
  
 Wenn **cbUserData** 0 oder ein positiver Wert ist, verwendet das System **cbUserData** als maximale Datenlänge. Wenn jedoch zusätzlich zu einem positiven **cbUserData**-Wert ein Längenindikator oder eine Abschlusszeichensequenz angegeben ist, bestimmt das System die Datenlänge mit der Methode, die zu der kleineren zu kopierenden Datenmenge führt.  
  
 Der **cbUserData** -Wert stellt die Anzahl der Datenbytes dar. Werden Zeichendaten durch Unicode-Zeichen dargestellt, repräsentiert ein positiver **cbUserData** -Parameterwert die Anzahl der Zeichen multipliziert mit der Größe (in Byte) der einzelnen Zeichen.  
  
 *pbUserDataTerm*[size_is] [in]  
 Die Abschlusszeichensequenz, die für das Feld verwendet werden soll. Dieser Parameter ist in erster Linie für Zeichendatentypen nützlich, da alle anderen Typen eine feste Länge besitzen oder, im Falle von Binärdaten, einen Indikator für die Länge erfordern, um die Anzahl der vorhandenen Bytes präzise zu erfassen.  
  
 Legen Sie diesen Parameter auf NULL fest, um zu vermeiden, dass extrahierte Daten terminiert werden, oder um anzugeben, dass Daten in einer Benutzerdatei nicht terminiert werden.  
  
 Wird mehr als eine Methode zur Angabe der Länge der Benutzerdateispalte verwendet (z. B. ein Abschlusszeichen und ein Längenindikator oder ein Abschlusszeichen und eine maximale Spaltenlänge), wird beim Massenkopieren die Methode ausgewählt, die zu der kleineren zu kopierenden Datenmenge führt.  
  
 Die API für das Massenkopieren führt nach Bedarf eine Zeichenkonvertierung von Unicode in MBCS aus. Stellen Sie unbedingt sicher, dass sowohl die Bytezeichenfolge des Abschlusszeichens und die Länge der Bytezeichenfolge richtig festgelegt werden.  
  
 *cbUserDataTerm*[in]  
 Die Länge (in Byte) der Abschlusszeichensequenz, die für die Spalte verwendet werden soll. Wenn kein Abschlusszeichen vorhanden ist oder in den Daten gewünscht wird, legen Sie diesen Wert auf 0 fest.  
  
 *idxServerCol*[in]  
 Die Ordnungsposition der Spalte innerhalb der Datenbanktabelle. Die erste Spaltennummer ist 1. Die Ordnungsposition einer Spalte wird von **IColumnsInfo::GetColumnInfo** oder ähnlichen Methoden gemeldet. Wenn dieser Wert 0 ist, wird beim Massenkopieren das Feld in der Datendatei ignoriert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_FAIL  
 Ein Anbieter spezifischer Fehler ist aufgetreten. Ausführliche Informationen erhalten Sie über die [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) -Schnittstelle.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Die [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)-Methode wurde beispielsweise erst nach dem Aufruf dieser Methode aufgerufen.  
  
 E_INVALIDARG  
 Das Argument war ungültig.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund von nicht genügend Arbeitsspeicher.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
