---
title: 'Ibcpsession:: Bcpcontrol (OLE DB) | Microsoft-Dokumentation'
description: IBCPSession::BCPControl (OLE DB)
ms.custom: ''
ms.date: 07/03/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPControl (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPControl method
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 49c26fdaf7912fe0cf67d35ac8fa6f581319cbe5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66790962"
---
# <a name="ibcpsessionbcpcontrol-ole-db"></a>IBCPSession::BCPControl (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Legt die Optionen für einen Massenkopiervorgang fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPControl(   
      int eOption,  
      void *iValue);  
```  
  
## <a name="remarks"></a>Remarks  
 Mit der **BCPControl**-Methode werden verschiedene Steuerelementparameter für Massenkopiervorgänge festgelegt, einschließlich der Anzahl von Fehlern, die vor dem Abbrechen eines Massenkopiervorgangs zulässig sind, der Nummern der ersten und letzten Zeilen, die aus einer Datendatei kopiert werden sollen, und der Batchgröße.  
  
 Außerdem wird diese Methode dazu verwendet, die SELECT-Anweisung beim Massenkopieren von Daten aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] anzugeben. Sie können das **eOption-Argument** auf BCP_OPTION_HINTS und das **iValue**-Argument festlegen, um einen Zeiger auf eine Zeichenfolge mit Breitzeichen zur Verfügung zu haben, die die SELECT-Anweisung enthält.  
  
 Mögliche Werte für *eOption* sind:  
  
|Option|und Beschreibung|  
|------------|-----------------|  
|BCP_OPTION_ABORT|Beendet einen Massenkopiervorgang, der bereits ausgeführt wird. Sie können die **BCPControl**-Methode mit einem *eOption*-Argument von BCP_OPTION_ABORT aus einem anderen Thread aufrufen, um den ausgeführten Massenkopiervorgang anzuhalten. Die *iValue* Argument wird ignoriert.|  
|BCP_OPTION_BATCH|Die Anzahl der Zeilen pro Batch. Der Standardwert ist 0 (null), womit beim Extrahieren von Daten alle Zeilen in einer Tabelle oder beim Kopieren von Daten nach [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] alle Zeilen in der Benutzerdatendatei angegeben werden. Mit einem Wert kleiner als 1 wird BCP_OPTION_BATCH auf den Standardwert zurückgesetzt.|  
|BCP_OPTION_DELAYREADFMT|Ein boolescher Wert. Wenn er auf TRUE festgelegt ist, erfolgt das Lesen durch [IBCPSession::BCPReadFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) bei der Ausführung. Wenn False (Standard), ibcpsession:: Bcpreadfmt sofort wird die Formatdatei zu lesen. Ein Sequenzfehler tritt erfolgt, wenn **BCP_OPTION_DELAYREADFMT** ist "true", und Sie rufen ibcpsession:: BCPColumns oder ibcpsession:: BCPColFmt.<br /><br /> Ein Sequenzfehler tritt auch aufrufen `IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)FALSE))` nach dem Aufruf `IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)TRUE)` und ibcpsession:: Bcpwritefmt.<br /><br /> Weitere Informationen finden Sie unter [Metadatenermittlung](../../oledb/features/metadata-discovery.md).|  
|BCP_OPTION_FILECP|Das *iValue*-Argument enthält die Nummer der Codepage für die Datendatei. Sie können die Nummer der Codepage angeben, z. B. 1252 oder 850, oder einen der folgenden Werte:<br /><br /> BCP_FILECP_ACP: Daten in der Datei sind in der Microsoft Windows®-Codepage des Clients.<br /><br /> BCP_FILECP_OEMCP: Daten in der Datei sind in der OEM-Codepage des Clients (Standard).<br /><br /> BCP_FILECP_RAW: Daten in der Datei sind in der Codepage von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|BCP_OPTION_FILEFMT|Die Versionsnummer des Datendateiformats. Diese kann 80 ([!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]), 90 ([!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]), 100 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] oder [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]) oder 110 ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]) sein. Der Standardwert ist 110. Dies ist beim Exportieren und Importieren von Daten in Formate nützlich, die in früheren Versionen des Servers unterstützt wurden.  Geben Sie beispielsweise zum Importieren von Daten aus einer Textspalte eines [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]-Servers in eine **varchar(max)**-Spalte auf einem [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Server oder höher den Wert 80 an. Wenn Sie den Wert 80 entsprechend beim Exportieren von Daten aus einer **varchar(max)**-Spalte angeben, werden diese wie Textspalten im [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]-Format gespeichert und können in eine Textspalte eines[!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] -Servers importiert werden.|  
|BCP_OPTION_FIRST|Die erste Datenzeile der zu kopierenden Datei oder Tabelle. Der Standard ist 1; ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück.|  
|BCP_OPTION_FIRSTEX|Gibt für BCP-OUT-Vorgänge die erste Zeile der Datenbanktabelle an, die in die Datendatei kopiert werden soll.<br /><br /> Gibt für BCP-IN-Vorgänge die erste Zeile der Datendatei an, die in die Datenbanktabelle kopiert werden soll.<br /><br /> Die *iValue* Parameter wird die Adresse einer 64-Bit-Ganzzahl mit Vorzeichen werden mit dem Wert erwartet. Der maximale Wert, der an BCPFIRSTEX übergeben werden kann, ist 2^63-1.|  
|BCP_OPTION_FMTXML|Gibt an, dass die generierte Formatdatei das XML-Format aufweisen sollte. Diese Option ist standardmäßig deaktiviert. Die Formatdateien werden standardmäßig als Textdateien gespeichert. Das XML-Format bietet größere Flexibilität, ist jedoch mit einigen Einschränkungen verbunden. Sie können beispielsweise das Präfix und das Abschlusszeichen für ein Feld nicht gleichzeitig angeben, was in älteren Formatdateien durchaus möglich war.<br /><br /> Hinweis: XML-Formatdateien werden nur unterstützt, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tools zusammen mit OLE DB-Treiber für SQL Server installiert sind.|  
|BCP_OPTION_HINTS|Das *iValue*-Argument enthält einen Zeichenfolgenzeiger mit Breitzeichen. Die adressierte Zeichenfolge gibt entweder Verarbeitungshinweise für das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Massenkopieren oder eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung an, die ein Resultset zurückgibt. Wenn eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung angegeben ist, die mehr als ein Resultset zurückgibt, werden alle auf das erste Resultset folgenden Resultsets nicht berücksichtigt.|  
|BCP_OPTION_KEEPIDENTITY|Wenn das *iValue*-Argument auf TRUE festgelegt ist, wird mit dieser Option angegeben, dass die Massenkopiermethoden Datenwerte einfügen, die für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Spalten bereitgestellt werden, die mit einer Identitätsbeschränkung definiert sind. Die Eingabedatei muss Werte für die IDENTITY-Spalten angeben. Wenn dies nicht festgelegt ist, werden neue Identitätswerte für die eingefügten Zeilen generiert. Alle in der Datei für die IDENTITY-Spalten vorhandenen Daten werden ignoriert.|  
|BCP_OPTION_KEEPNULLS|Bestimmt, ob leere Datenwerte in der Datei in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle in NULL-Werte konvertiert werden. Wenn das *iValue*-Argument auf TRUE festgelegt ist, werden leere Werte in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle in NULL-Werte konvertiert. In der Standardeinstellung werden leere Werte in einen Standardwert für die Spalte in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle konvertiert, sofern ein Standardwert angegeben ist.|  
|BCP_OPTION_LAST|Die letzte zu kopierende Zeile. Standardmäßig werden alle Zeilen kopiert. Ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück.|  
|BCP_OPTION_LASTEX|Gibt für BCP-OUT-Vorgänge die letzte Zeile der Datenbanktabelle an, die in die Datendatei kopiert werden soll.<br /><br /> Gibt für BCP-IN-Vorgänge die letzte Zeile der Datendatei an, die in die Datenbanktabelle kopiert werden soll.<br /><br /> Die *iValue* Parameter wird die Adresse einer 64-Bit-Ganzzahl mit Vorzeichen werden mit dem Wert erwartet. Der maximale Wert, der an BCPLASTEX übergeben werden kann, ist 2^63-1.|  
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
 Ein anwenderspezifischer Fehler ist aufgetreten. Ausführlichere Informationen erhalten Sie über die [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) -Schnittstelle.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Die [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)-Methode wurde beispielsweise vor dem Aufruf dieser Funktion nicht aufgerufen.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund nicht genügenden Arbeitsspeichers  
  
## <a name="see-also"></a>Weitere Informationen  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
