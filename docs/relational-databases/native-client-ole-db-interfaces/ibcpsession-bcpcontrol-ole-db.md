---
description: 'IBCPSession:: BCPControl (Native Client OLE DB-Anbieter)'
title: 'IBCPSession:: BCPControl (Native Client OLE DB-Anbieter) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPControl (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPControl method
ms.assetid: d58f3fe1-45e3-4e46-8e9c-000971829d99
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f90f55df46097416bc3f3b2c801d021ad0ee50ba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486719"
---
# <a name="ibcpsessionbcpcontrol-native-client-ole-db-provider"></a>IBCPSession:: BCPControl (Native Client OLE DB-Anbieter)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Legt die Optionen für einen Massenkopiervorgang fest.  
  
## <a name="syntax"></a>Syntax  
  
```  

HRESULT BCPControl(   
      int eOption,  
      void *iValue);  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der **BCPControl**-Methode werden verschiedene Steuerelementparameter für Massenkopiervorgänge festgelegt, einschließlich der Anzahl von Fehlern, die vor dem Abbrechen eines Massenkopiervorgangs zulässig sind, der Nummern der ersten und letzten Zeilen, die aus einer Datendatei kopiert werden sollen, und der Batchgröße.  
  
 Außerdem wird diese Methode dazu verwendet, die SELECT-Anweisung beim Massenkopieren von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzugeben. Sie können das **eOption-Argument** auf BCP_OPTION_HINTS und das **iValue**-Argument festlegen, um einen Zeiger auf eine Zeichenfolge mit Breitzeichen zur Verfügung zu haben, die die SELECT-Anweisung enthält.  
  
 Mögliche Werte für *eOption* sind:  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|BCP_OPTION_ABORT|Beendet einen Massenkopiervorgang, der bereits ausgeführt wird. Sie können die **BCPControl**-Methode mit einem *eOption*-Argument von BCP_OPTION_ABORT aus einem anderen Thread aufrufen, um den ausgeführten Massenkopiervorgang anzuhalten. Das -Argument *iValue* wird ignoriert.|  
|BCP_OPTION_BATCH|Die Anzahl der Zeilen pro Batch. Der Standardwert ist 0 (null), womit beim Extrahieren von Daten alle Zeilen in einer Tabelle oder beim Kopieren von Daten nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle Zeilen in der Benutzerdatendatei angegeben werden. Mit einem Wert kleiner als 1 wird BCP_OPTION_BATCH auf den Standardwert zurückgesetzt.|  
|BCP_OPTION_DELAYREADFMT|Ein boolescher Wert. Wenn er auf TRUE festgelegt ist, erfolgt das Lesen durch [IBCPSession::BCPReadFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) bei der Ausführung. Gilt die Standardeinstellung FALSE, wird IBCPSession::BCPReadFm sofort die Formatdatei lesen. Wenn **BCP_OPTION_DELAYREADFMT** auf TRUE festgelegt ist und Sie IBCPSession::BCPColumns oder IBCPSession::BCPColFmt aufrufen, kommt es zu einem Sequenzfehler.<br /><br /> Ein Sequenzfehler tritt auch auf, wenn Sie nach dem Aufrufen von `IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)TRUE)` und IBCPSession::BCPWriteFmt noch `IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)FALSE))` aufrufen.<br /><br /> Weitere Informationen finden Sie unter [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).|  
|BCP_OPTION_FILECP|Das *iValue*-Argument enthält die Nummer der Codepage für die Datendatei. Sie können die Nummer der Codepage angeben, z. B. 1252 oder 850, oder einen der folgenden Werte:<br /><br /> BCP_FILECP_ACP: Daten in der Datei sind in der Microsoft Windows®-Codepage des Clients.<br /><br /> BCP_FILECP_OEMCP: Daten in der Datei sind in der OEM-Codepage des Clients (Standard).<br /><br /> BCP_FILECP_RAW: Daten in der Datei sind in der Codepage von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|BCP_OPTION_FILEFMT|Die Versionsnummer des Datendateiformats. Diese kann 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]), 90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) oder 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) sein. Der Standardwert ist 120. Dies ist beim Exportieren und Importieren von Daten in Formate nützlich, die in früheren Versionen des Servers unterstützt wurden.  Geben Sie beispielsweise zum Importieren von Daten aus einer Textspalte eines [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-Servers in eine **varchar(max)** -Spalte auf einem [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Server oder höher den Wert 80 an. Wenn Sie den Wert 80 entsprechend beim Exportieren von Daten aus einer **varchar(max)** -Spalte angeben, werden diese wie Textspalten im [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-Format gespeichert und können in eine Textspalte eines[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] -Servers importiert werden.|  
|BCP_OPTION_FIRST|Die erste Datenzeile der zu kopierenden Datei oder Tabelle. Der Standard ist 1; ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück.|  
|BCP_OPTION_FIRSTEX|Gibt für BCP-OUT-Vorgänge die erste Zeile der Datenbanktabelle an, die in die Datendatei kopiert werden soll.<br /><br /> Gibt für BCP-IN-Vorgänge die erste Zeile der Datendatei an, die in die Datenbanktabelle kopiert werden soll.<br /><br /> Der -Parameter *iValue* sollte die Adresse einer 64-Bit-Ganzzahl mit Vorzeichen sein, die den Wert enthält. Der maximale Wert, der an BCPFIRSTEX übergeben werden kann, ist 2^63-1.|  
|BCP_OPTION_FMTXML|Gibt an, dass die generierte Formatdatei das XML-Format aufweisen sollte. Diese Option ist standardmäßig deaktiviert. Die Formatdateien werden standardmäßig als Textdateien gespeichert. Das XML-Format bietet größere Flexibilität, ist jedoch mit einigen Einschränkungen verbunden. Sie können beispielsweise das Präfix und das Abschlusszeichen für ein Feld nicht gleichzeitig angeben, was in älteren Formatdateien durchaus möglich war.<br /><br /> Hinweis: XML-Format Dateien werden nur unterstützt, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tools zusammen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client installiert werden.|  
|BCP_OPTION_HINTS|Das *iValue*-Argument enthält einen Zeichenfolgenzeiger mit Breitzeichen. Die adressierte Zeichenfolge gibt entweder Verarbeitungshinweise für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Massenkopieren oder eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung an, die ein Resultset zurückgibt. Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung angegeben ist, die mehr als ein Resultset zurückgibt, werden alle auf das erste Resultset folgenden Resultsets nicht berücksichtigt.|  
|BCP_OPTION_KEEPIDENTITY|Wenn das *iValue*-Argument auf TRUE festgelegt ist, wird mit dieser Option angegeben, dass die Massenkopiermethoden Datenwerte einfügen, die für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalten bereitgestellt werden, die mit einer Identitätsbeschränkung definiert sind. Die Eingabedatei muss Werte für die IDENTITY-Spalten angeben. Wenn dies nicht festgelegt ist, werden neue Identitätswerte für die eingefügten Zeilen generiert. Alle in der Datei für die IDENTITY-Spalten vorhandenen Daten werden ignoriert.|  
|BCP_OPTION_KEEPNULLS|Bestimmt, ob leere Datenwerte in der Datei in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle in NULL-Werte konvertiert werden. Wenn das *iValue*-Argument auf TRUE festgelegt ist, werden leere Werte in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle in NULL-Werte konvertiert. In der Standardeinstellung werden leere Werte in einen Standardwert für die Spalte in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle konvertiert, sofern ein Standardwert angegeben ist.|  
|BCP_OPTION_LAST|Die letzte zu kopierende Zeile. Standardmäßig werden alle Zeilen kopiert. Ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück.|  
|BCP_OPTION_LASTEX|Gibt für BCP-OUT-Vorgänge die letzte Zeile der Datenbanktabelle an, die in die Datendatei kopiert werden soll.<br /><br /> Gibt für BCP-IN-Vorgänge die letzte Zeile der Datendatei an, die in die Datenbanktabelle kopiert werden soll.<br /><br /> Der -Parameter *iValue* sollte die Adresse einer 64-Bit-Ganzzahl mit Vorzeichen sein, die den Wert enthält. Der maximale Wert, der an BCPLASTEX übergeben werden kann, ist 2^63-1.|  
|BCP_OPTION_MAXERRS|Die Anzahl von Fehlern, die zulässig sind, bevor der Massenkopiervorgang fehlschlägt. Der Standardwert ist 10. Ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück. Beim Massenkopieren sind maximal 65.535 Fehler zulässig. Wenn für diese Option größere Werte als 65.535 festgelegt werden, wird diese Option auf 65.535 festgelegt.|  
|BCP_OPTION_ROWCOUNT|Gibt die Anzahl von Zeilen zurück, auf die sich der aktuelle (oder letzte) BCP-Vorgang auswirkt.|  
|BCP_OPTION_TEXTFILE|Die Datendatei ist keine Binärdatei, sondern eine Textdatei. BCP stellt fest, ob es sich bei der Textdatei um eine Unicode-Datei handelt, indem der Unicode-Bytemarker in den ersten beiden Bytes der Datendatei überprüft wird.|  
|BCP_OPTION_UNICODEFILE|Wenn diese Option auf TRUE festgelegt wurde, bedeutet das, dass die Eingabedatei ein Unicode-Dateiformat ist.|  
  
## <a name="arguments"></a>Argumente  
 *eOption*[in]  
 Legen Sie eine der im obigen Abschnitt mit Hinweisen aufgelisteten Optionen fest.  
  
 *iValue*[in]  
 Der Wert für das angegebene *eOption*-Argument. Das *iValue*-Argument ist ein ganzzahliger Wert, der in einen void-Zeiger umgewandelt wird, um zukünftige Erweiterungen auf 64-Bit-Werte zuzulassen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_FAIL  
 Ein anbieterspezifischer Fehler ist aufgetreten. Ausführliche Informationen erhalten Sie über die [ISQLServerErrorInfo](https://docs.microsoft.com/sql/connect/oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db?view=sql-server-ver15)-Schnittstelle.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Die [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)-Methode wurde beispielsweise vor dem Aufruf dieser Funktion nicht aufgerufen.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund nicht genügenden Arbeitsspeichers  
  
## <a name="see-also"></a>Weitere Informationen  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
