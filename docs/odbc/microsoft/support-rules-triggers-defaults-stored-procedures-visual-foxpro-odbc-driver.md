---
title: Unterstützung für Regeln, Trigger, Standardwerte und gespeicherte Prozeduren | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], stored procedures
- FoxPro ODBC driver [ODBC], commands and functions
- commands for FoxPro ODBC driver [ODBC]
- FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], triggers
- stored procedures [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], rules
- FoxPro commands and functions [ODBC]
- rules [ODBC]
- Visual FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], rules
- functions [ODBC], Visual FoxPro
- default values [ODBC]
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro ODBC driver [ODBC], triggers
- FoxPro ODBC driver [ODBC], stored procedures
- Visual FoxPro commands and functions [ODBC]
ms.assetid: e449de20-d6ca-4902-9f8e-814eb6e86650
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2fcf8e7c80b2712313cba81199489dc7cb06dce0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301137"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Unterstützung für Regeln, Trigger, Standardwerte und gespeicherte Prozeduren (Visual FoxPro-ODBC-Treiber)
Sie können Visual FoxPro-Regeln, Trigger, Standardwerte oder gespeicherte Prozeduren nicht mit dem Visual FoxPro ODBC-Treiber erstellen. Ihre Anwendung kann jedoch mit vorhandenen Regeln, Triggern, Standardwerten oder gespeicherten Prozeduren interagieren, während sie Invisual FoxPro-Daten einfügt, aktualisiert oder löscht, die in einer Datenbank gespeichert sind.  
  
 In der folgenden Tabelle sind die Visual FoxPro-Befehle und -Funktionen aufgeführt, die vom Visual FoxPro ODBC-Treiber unterstützt werden, wenn die Befehle oder Funktionen in Regeln, Triggern, Standardwerten oder gespeicherten Prozeduren vorhanden sind.  
  
 Wenn Ihre Anwendung mit Daten interagiert, deren Regeln, Trigger, Standardwerte oder gespeicherte Prozeduren andere Visual FoxPro-Befehle oder -Funktionen aufrufen, generiert der Treiber einen Fehler. Eine Liste der Befehle und Funktionen, die vom Treiber nicht unterstützt werden, finden Sie unter [Nicht unterstützte Visual FoxPro-Befehle und -Funktionen.](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md)  
  
> [!TIP]  
>  Wenn Sie bedingten Code in Ihre Regeln, Trigger oder gespeicherten Prozeduren einfügen möchten, die die Befehle bestimmen, die ausgeführt werden sollen, wenn sie vom Treiber aufgerufen werden, können Sie die **Version( -Funktion** verwenden. Die **VERSION( )-Funktion** gibt "Visual FoxPro ODBC Driver * \<version>*" zurück, wenn sie vom Treiber aufgerufen wird.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>Visual FoxPro-Befehle und -Funktionen werden in Regeln, Triggern, Standardwerten und gespeicherten Prozeduren unterstützt  
  
||||  
|-|-|-|  
|• Operator|%-Operator|&-Befehl|  
|&& -Befehl|* Befehl|= Befehl|  
  
## <a name="a"></a>Ein  
  
||||  
|-|-|-|  
|ABS( ) Funktion|ACOPY( ) Funktion|ADD TABLE-Befehl|  
|ADATABASES( ) Funktion|ADBOBJECTS( ) Funktion|AERROR( ) Funktion|  
|ADEL( ) Funktion|AELEMENT( ) Funktion|ALEN( ) Funktion|  
|AFIELDS( ) Funktion|AINS( ) Funktion|ALTER TABLE (SQL-Befehl)|  
|ALIAS( ) Funktion|ALLTRIM( ) Funktion|APPEND VON ARRAY Befehl|  
|UND Operator|APPEND-Befehl|APPEND MEMO-Befehl|  
|APPEND VON Befehl|APPEND GENERAL Befehl|ASCAN( ) Funktion|  
|APPEND PROCEDURES-Befehl|ASC( ) Funktion|ASUBSCRIPT( ) Funktion|  
|ASIN( ) Funktion|ASORT( ) Funktion|ATAN( ) Funktion|  
|AT( ) Funktion|AT_C( ) Funktion|ATCLINE( ) Funktion|  
|ATC( ) Funktion|ATCC( ) Funktion|AUSED( ) Funktion|  
|ATLINE( ) Funktion|ATN2( ) Funktion||  
|AVERAGE-Befehl|ACOS( ) Funktion||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|BEGIN TRANSACTION-Befehl|ZWISCHEN( ) Funktion|BITNOT( ) Funktion|  
|BITCLEAR( ) Funktion|BITLSHIFT( ) Funktion|BITSET( ) Funktion|  
|BITOR( ) Funktion|BITRSHIFT( ) Funktion|BLANK-Befehl|  
|BITTEST( ) Funktion|BITXOR( ) Funktion||  
|BOF( ) Funktion|BITAND( ) Funktion||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|CALCULATE-Befehl|CANDIDATE( ) Funktion|CHR( ) Funktion|  
|CDX( ) Funktion|CEILING( ) Funktion|CLOSE-Befehle|  
|CHRTRAN( ) Funktion|CHRTRANC( ) Funktion|COPY INDEXES-Befehl|  
|CMONTH( ) Funktion|CONTINUE-Befehl|COPY STRUCTURE EXTENDED Befehl|  
|BEFEHL COPY PROCEDURES|COPY STRUCTURE-Befehl|COPY TO-Befehl|  
|COPY TAG-Befehl|COPY TO ARRAY-Befehl|CPCONVERT( ) Funktion|  
|COS( ) Funktion|COUNT-Befehl|CTOD( ) Funktion|  
|CPCURRENT( ) Funktion|CPDBF( ) Funktion|CURSORSETPROP( ) Funktion|  
|CTOT( ) Funktion|CURSORGETPROP( ) Funktion||  
|CURVAL( ) Funktion|CDOW( ) Funktion||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|DATE( ) Funktion|DATETIME( ) Funktion|DAY( ) Funktion|  
|DBC( ) Funktion|DBF( ) Funktion|DBGETPROP( ) Funktion|  
|DBUSED( ) Funktion|DELETE (SQL-Befehl)|DELETE-Befehl|  
|DELETE TAG-Befehl|DELETED( ) Funktion|DESCENDING( ) Funktion|  
|DIFFERENCE( ) Funktion|DIMENSION-Befehl|DISKSPACE( ) Funktion|  
|DMY( ) Funktion|DO FALL ... ENDCASE-Befehl|DO-Befehl|  
|TUN, WÄHREND ... ENDDO-Befehl|DOW( ) Funktion|DTOC( ) Funktion|  
|DTOR( ) Funktion|DTOS( ) Funktion|DTOT( ) Funktion|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|EMPTY( ) Funktion|EVALUATE( ) Funktion|EXIT-Befehl|  
|ERROR( ) Funktion|EXP( ) Funktion||  
|END TRANSACTION-Befehl|EOF( ) Funktion||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|FCOUNT( ) Funktion|FDATE( ) Funktion|FIELD( ) Funktion|  
|FILE( ) Funktion|FILTER( ) Funktion|FLDLIST( ) Funktion|  
|FLOCK( ) Funktion|FLOOR( ) Funktion|FLUSH-Befehl|  
|Für... ENDFOR-Befehl|FOR( ) Funktion|FOUND( ) Funktion|  
|FREE TABLE Befehl|FSIZE( ) Funktion|FTIME( ) Funktion|  
|FULLPATH( ) Funktion|FUNKTION-Befehl|FV( ) Funktion|  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|GATHER-Befehl|GETNEXTMODIFIED( ) Funktion|GO/GOTO-Befehl|  
|GETFLDSTATE( ) Funktion|GOMONTH( ) Funktion||  
|GETCP( ) Funktion|GETENV( ) Funktion||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|HEADER( ) Funktion|HOUR( ) Funktion|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IDXCOLLATE( ) Funktion|Wenn... ENDIF-Befehl|IIF( ) Funktion|  
|INDBC( ) Funktion|INDEX-Befehl|INLIST( ) Funktion|  
|INSERT-SQL-Befehl|INT( ) Funktion|ISALPHA( ) Funktion|  
|ISBLANK( ) Funktion|ISDIGIT( ) Funktion|ISEXCLUSIVE( ) Funktion|  
|ISLEADBYTE( ) Funktion|ISLOWER( ) Funktion|ISNULL( ) Funktion|  
|ISREADONLY( ) Funktion|ISUPPER( ) Funktion||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|KEY( ) Funktion|KEYMATCH( ) Funktion||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|LINKS( ) Funktion|LEFTC( ) Funktion|LIKEC( ) Funktion|  
|LENC( ) Funktion|LIKE( ) Funktion|LOCK( ) Funktion|  
|LOCAL-Befehl|LOCATE-Befehl|LOOKUP( ) Funktion|  
|LOG( ) Funktion|LOG10( ) Funktion|LTRIM( ) Funktion|  
|LOWER( ) Funktion|LPARAMETERS-Befehl||  
|LUPDATE( ) Funktion|LEN( ) Funktion||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|_MLINE Systemspeichervariable|MAX( ) Funktion|MDX( ) Funktion|  
|MDY( ) Funktion|MEMLINES( ) Funktion|MESSAGE( ) Funktion|  
|MIN( ) Funktion|MINUTE( ) Funktion|MLINE( ) Funktion|  
|MOD( ) Funktion|MONAT( ) Funktion|MTON( ) Funktion|  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NDX( ) Funktion|NORMALIZE( ) Funktion|NOT Operator|  
|HINWEIS Befehl|NTOM( ) Funktion|NVL( ) Funktion|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|OCCURS( ) Funktion|OLDVAL( ) Funktion|ON ERROR-Befehl|  
|ON KEY-Befehl|ON( ) Funktion|OPEN DATABASE-Befehl|  
|OR-Operator|ORDER( ) Funktion|OS( ) Funktion|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|PACK-Befehl|PARAMETERS( ) Funktion|ZAHLUNG( ) Funktion|  
|PARAMETERS-Befehl|PRIMARY( ) Funktion|PRIVATE-Befehl|  
|PI( ) Funktion|PROGRAMM( ) Funktion|PROPER( ) Funktion|  
|PROCEDURE-Befehl|PV( ) Funktion||  
|PUBLIC-Befehl|PADL( ) &#124; PADR( ) &#124; PADC( ) Funktionen||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|RAND( ) Funktion|RAT( ) Funktion|RATC( ) Funktion|  
|RATLINE( ) Funktion|RECALL-Befehl|RECCOUNT( ) Funktion|  
|RECNO( ) Funktion|RECSIZE( ) Funktion|REGIONAL-Befehl|  
|RELATION( ) Funktion|REMOVE TABLE-Befehl|REPLACE-Befehl|  
|REPLACE VON ARRAY Befehl|REPLICATE( ) Funktion|RETRY-Befehl|  
|RETURN-Befehl|RECHTS( ) Funktion|RIGHTC( ) Funktion|  
|RLOCK( ) Funktion|ROLLBACK-Befehl|ROUND( ) Funktion|  
|RTOD( ) Funktion|RTRIM( ) Funktion||  
  
## <a name="s"></a>E  
  
||||  
|-|-|-|  
|Scan... ENDSCAN-Befehl|SCATTER-Befehl|SEC( ) Funktion|  
|SECONDS( ) Funktion|SEEK-Befehl|SEEK( ) Funktion|  
|SELECT-Befehl|SELECT( ) Funktion|SELECT-SQL-Befehl|  
|SET BLOCKSIZE-Befehl|SET CARRY-Befehl|SET CENTURY Befehl|  
|SET COLLATE-Befehl|SET DATABASE-Befehl|SET DATE-Befehl|  
|SET DEFAULT-Befehl|SET DELETED-Befehl|SET EXACT-Befehl|  
|SET EXCLUSIVE-Befehl|SET FDOW-Befehl|SET FIELDS-Befehl|  
|SET FILTER-Befehl|SET FIXED Befehl|SET FULLPATH Befehl|  
|SET FWEEK-Befehl|SET HOURS-Befehl|SET INDEX-Befehl|  
|SET LOCK-Befehl|BEFEHL SET MULTILOCKS|SET NEAR-Befehl|  
|SET NOCPTRANS Befehl|SET NOTIFY-Befehl|SET NULL-Befehl|  
|SET OPTIMIZE Befehl|SET ORDER-Befehl|SET PATH-Befehl|  
|SET PROCEDURE-Befehl|SET RELATION-Befehl|SET RELATION OFF Befehl|  
|SET REPROCESS-Befehl|SET SKIP-Befehl|SET UDFPARMS Befehl|  
|SET UNIQUE-Befehl|SET VOLUME-Befehl|SET( ) Funktion|  
|SETFLDSTATE( ) Funktion|SIGN ( ) Funktion|SIN( ) Funktion|  
|SKIP-Befehl|SORT-Befehl|SPACE( ) Funktion|  
|SQRT( ) Funktion|STORE-Befehl|STR( ) Funktion|  
|STRCONV( ) Funktion|STRTRAN( ) Funktion|STUFF( ) Funktion|  
|STUFFC( ) Funktion|SUBSTR( ) Funktion|SUBSTRC( ) Funktion|  
|SUM-Befehl|SYS(2011) Funktion||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TALLY Systemspeichervariable|_TRIGGERLEVEL Systemspeichervariable|TAGCOUNT( ) Funktion|  
|TABLEUPDATE( ) Funktion|TAG( ) Funktion|TARGET( ) Funktion|  
|TAGNO( ) Funktion|TAN( ) Funktion|TRIM( ) Funktion|  
|TIME( ) Funktion|TOTAL-Befehl|TXNLEVEL( ) Funktion|  
|TTOC( ) Funktion|TTOD( ) Funktion||  
|TYPE( ) Funktion|TABLEREVERT( ) Funktion||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|UNIQUE( ) Funktion|UNLOCK-Befehl|USE-Befehl|  
|UPDATE-Befehl|UPPER( ) Funktion||  
|USED( ) Funktion|UPDATE (SQL-Befehl)||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|VAL( ) Funktion|VERSION( ) Funktion||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|WOCHE( ) Funktion|||  
  
## <a name="y"></a>J  
  
||||  
|-|-|-|  
|JAHR( ) Funktion|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|ZAP-Befehl|||
