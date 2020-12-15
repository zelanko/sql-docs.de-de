---
description: bcp_control
title: bcp_control | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_control
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_control function
ms.assetid: 32187282-1385-4c52-9134-09f061eb44f5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 24aac8fe3f903ebb0cadec8f662a1cc870340d1c
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97473811"
---
# <a name="bcp_control"></a>bcp_control
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Ändert die Standardeinstellungen für verschiedene Steuerelementparameter für einen Massenkopiervorgang zwischen einer Datei und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_control (  
        HDBC hdbc,  
        INT eOption,  
        void* iValue);  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *eOption*  
 Ist einer der folgenden Werte:  
  
 BCPABORT  
 Beendet einen Massenkopiervorgang, der bereits ausgeführt wird. Ruft **bcp_control** mit der *eOption* "BCPABORT" von einem anderen Thread auf, um einen ausgelaufenden Massen Kopiervorgang zu beenden. Der *iValue* -Parameter wird ignoriert.  
  
 BCPBATCH  
 Die Anzahl von Zeilen pro Batch. Der Standardwert ist 0, womit beim Extrahieren von Daten alle Zeilen in einer Tabelle oder beim Kopieren von Daten nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle Zeilen in der Benutzerdatendatei angegeben werden. Ein Wert kleiner als 1 setzt BCPBATCH auf den Standardwert zurück.  
  
 BCPDELAYREADFMT  
 Ein boolescher Wert, wenn er auf "true" festgelegt ist, bewirkt, dass [bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) bei der Ausführung liest. Der Standardwert false gibt an, dass bcp_readfmt die Format Datei sofort liest. Ein Sequenz Fehler tritt auf, wenn bcpdelta ayread fmt den Wert true aufweist und Sie bcp_columns oder bcp_setcolfmt aufgerufen haben.  
  
 Ein Sequenz Fehler tritt auch auf, wenn Sie nach dem Aufruf von `bcp_control(hdbc,` `, (void *)FALSE)` `bcp_control(hdbc,` bcpdelta ayread fmt und bcp_writefmt bcpdelta aylefmt aufrufen `, (void *)TRUE)` .  
  
 Weitere Informationen finden Sie unter [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 BCPFILECP  
 *iValue* enthält die Nummer der Codepage für die Datendatei. Sie können die Nummer der Codepage angeben, z. B. 1252 oder 850 bzw. einen der folgenden Werte  
  
 BCPFILE_ACP: Daten in der Datei befinden sich auf der Microsoft Windows® Codepage des Clients.  
  
 BCPFILE_OEMCP: Daten in der Datei befinden sich auf der OEM-Codepage des Clients (Standard).  
  
 BCPFILE_RAW: Daten in der Datei befinden sich auf der Codepage von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 BCPFILEFMT  
 Die Versionsnummer des Datendateiformats. Dies kann 80 ( [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ), 90 ( [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ), 100 ( [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ), 110 ( [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ) oder 120 () sein [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Der Standardwert ist 120. Dies ist beim Exportieren und Importieren von Daten in Formate nützlich, die in früheren Versionen des Servers unterstützt wurden. Wenn Sie z. b. Daten aus einer Text Spalte eines [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Servers in eine **varchar (max)** -Spalte auf einem Server mit oder höher importieren möchten [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , sollten Sie 80 angeben. Wenn Sie beim Exportieren von Daten aus einer Spalte vom Typ " **varchar (max)** " den Wert "80" angeben, wird dieser ebenso wie Textspalten im [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Format gespeichert und kann in eine Text Spalte eines Servers importiert werden [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] .  
  
 BCPFIRST  
 Dies ist die erste Datenzeile der zu kopierenden Datei oder Tabelle. Der Standard ist 1; ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück.  
  
 BCPFIRSTEX  
 Gibt für BCP-OUT-Vorgänge die erste Zeile der Datenbanktabelle an, die in die Datendatei kopiert werden soll.  
  
 Gibt für BCP-IN-Vorgänge die erste Zeile der Datendatei an, die in die Datenbanktabelle kopiert werden soll.  
  
 Der *iValue* -Parameter wird als Adresse einer signierten 64-Bit-Ganzzahl mit dem Wert erwartet. Der maximale Wert, der an BCPFIRSTEX übermittelt werden kann, ist 2 ^ 63-1.  
  
 BCPFMTXML  
 Gibt an, dass die generierte Format Datei im XML-Format vorliegen soll. Sie ist standardmäßig deaktiviert.  
  
 XML-Formatdateien bieten größere Flexibilität, sind jedoch mit einigen Einschränkungen verbunden. Sie können z. b. das Präfix und das Abschluss Zeichen für ein Feld nicht gleichzeitig angeben, was in älteren Format Dateien möglich war.  
  
> [!NOTE]  
>  XML-Formatdateien werden nur unterstützt, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zusammen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client installiert wird.  
  
 BCPHINTS  
 *iValue* enthält einen SQLTCHAR-Zeichen folgen Zeiger. Die adressierte Zeichenfolge gibt entweder Verarbeitungshinweise für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Massenkopieren oder eine Transact-SQL-Anweisung an, die ein Resultset zurückgibt. Wenn eine Transact-SQL-Anweisung angegeben ist, die mehr als ein Resultset zurückgibt, werden alle auf das erste Resultset folgenden Resultsets nicht berücksichtigt. Weitere Informationen zur Verarbeitung von Massen Kopier Vorgängen finden Sie unter [bcp (Hilfsprogramm](../../tools/bcp-utility.md)).  
  
 BCPKEEPIDENTITY  
 Wenn *iValue* auf true festgelegt ist, wird angegeben, dass die Massen Kopierfunktionen Datenwerte einfügen, die für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit einer Identitäts Einschränkung definierte Spalten bereitgestellt werden Die Eingabedatei muss Werte für die IDENTITY-Spalten angeben. Wenn dies nicht festgelegt ist, werden neue Identitätswerte für die eingefügten Zeilen generiert. Alle in der Datei für die IDENTITY-Spalten vorhandenen Daten werden ignoriert.  
  
 BCPKEEPNULLS  
 Bestimmt, ob leere Datenwerte in der Datei in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle in NULL-Werte konvertiert werden. Wenn *iValue* true ist, werden leere Werte in der Tabelle in NULL konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . In der Standardeinstellung werden leere Werte in einen Standardwert für die Spalte in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle konvertiert, sofern ein Standardwert angegeben ist.  
  
 BCPLAST  
 Entspricht der letzten zu kopierenden Zeile. In der Standardeinstellung werden alle Zeilen kopiert. Ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück.  
  
 BCPLASTEX  
 Gibt für BCP-OUT-Vorgänge die letzte Zeile der Datenbanktabelle an, die in die Datendatei kopiert werden soll.  
  
 Gibt für BCP-IN-Vorgänge die letzte Zeile der Datendatei an, die in die Datenbanktabelle kopiert werden soll.  
  
 Der *iValue* -Parameter wird als Adresse einer signierten 64-Bit-Ganzzahl mit dem Wert erwartet. Der maximale Wert, der an BCPLASTEX übergeben werden kann, ist 2^63-1.  
  
 BCPMAXERRS  
 Gibt die Anzahl von Fehlern an, die zulässig sind, bevor der Massenkopiervorgang fehlschlägt. Der Standardwert ist 10. ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück. Beim Massenkopieren sind maximal 65.535 Fehler zulässig. Wenn für diese Option größere Werte als 65.535 festgelegt werden, wird diese Option auf 65.535 festgelegt.  
  
 BCPODBC  
 Wenn der Wert true ist, wird angegeben, dass **DateTime** -und **smalldatetime** -Werte, die im Zeichenformat gespeichert werden, das ODBC-Zeitstempel-Präfix und-Suffix Die Option BCPODBC gilt nur für DB_OUT.  
  
 Bei false wird ein **DateTime** -Wert, der den 1. Januar 1997 darstellt, in die Zeichenfolge: 1997-01-01 00:00:00.000 konvertiert. Wenn der Wert true ist, wird der gleiche **DateTime** -Wert wie folgt dargestellt: {TS "1997-01-01 00:00:00.000"}.  
  
 BCPROWCOUNT  
 Gibt die Anzahl von Zeilen zurück, auf die sich der aktuelle (oder letzte) BCP-Vorgang auswirkt.  
  
 BCPTEXTFILE  
 Wenn der Wert TRUE ist, wird angegeben, dass die Datendatei eine Textdatei und keine Binärdatei ist. Bei einer Textdatei bestimmt BCP, ob es sich um Unicode handelt, indem der Unicode-Bytemarker in den ersten beiden Bytes der Datendatei überprüft wird.  
  
 BCPUNICODEFILE  
 Wenn der Wert TRUE ist, wird angegeben, dass die Eingabedatei eine Unicode-Datei ist.  
  
 *iValue*  
 Der Wert für die angegebene *eOption*. *iValue* ist ein ganzzahliger Wert (Longlong), der in einen void-Zeiger umgewandelt wird, um zukünftige Erweiterungen auf 64-Bit-Werte zuzulassen.  
  
## <a name="returns"></a>Gibt zurück  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Mit dieser Funktion werden verschiedene Steuerelementparameter für Massenkopiervorgänge festgelegt, einschließlich der Anzahl von Fehlern, die vor dem Abbrechen eines Massenkopiervorgangs zulässig sind, der Nummern der ersten und letzten Zeilen, die aus einer Datendatei kopiert werden sollen, und der Batchgröße.  
  
 Außerdem wird diese Funktion dazu verwendet, die SELECT-Anweisung beim Massenkopieren des Resultsets einer SELECT-Anweisung aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzugeben. Legen Sie *eOption* auf BCPHINTS fest, und legen Sie *iValue* auf einen Zeiger auf eine SQLTCHAR-Zeichenfolge fest, die die SELECT-Anweisung enthält.  
  
 Diese Steuerelementparameter sind nur beim Kopieren zwischen einer Benutzerdatei und einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle sinnvoll. Steuerelement Parametereinstellungen wirken sich nicht auf Zeilen aus, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)kopiert werden.  
  
## <a name="example"></a>Beispiel  
  
```  
// Variables like henv not specified.  
SQLHDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("address"), _T("address.add"), _T("addr.err"),  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the number of rows per batch.   
if (bcp_control(hdbc, BCPBATCH, (void*) 1000) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set file column count.   
if (bcp_columns(hdbc, 1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the file format.   
if (bcp_colfmt(hdbc, 1, 0, 0, SQL_VARLEN_DATA, '\n', 1, 1)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
printf_s("%ld rows processed by bulk copy.", nRowsProcessed);  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
