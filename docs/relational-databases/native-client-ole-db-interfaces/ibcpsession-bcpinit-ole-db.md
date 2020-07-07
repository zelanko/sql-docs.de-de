---
title: IBCPSession::BCPInit (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPInit (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8707ad2b00a11e0e681c3b5a3a73cbbe82a2c1fa
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008475"
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Initialisiert die Massenkopierstruktur, führt einige Fehlerprüfungen durch, überprüft die korrekte Angabe der Daten- und Formatdateinamen und öffnet dann diese Dateien.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPInit(   
      const wchar_t *pwszTable,  
      const wchar_t *pwszDataFile,  
      const wchar_t *pwszErrorFile,  
      int eDirection);  
```  
  
## <a name="remarks"></a>Hinweise  
 Die **BCPInit** -Methode sollte vor jeder anderen Massenkopiermethode aufgerufen werden. Die **BCPInit**-Methode führt die erforderlichen Initialisierungen für einen Massenkopiervorgang von Daten zwischen der Workstation und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durch.  
  
 Die **BCPInit** -Methode untersucht die Struktur der Quell- oder Zieltabelle der Datenbank, nicht jedoch die Datendatei. Sie gibt basierend auf den einzelnen Spalten in der Datenbanktabelle, der Sicht oder dem SELECT-Resultset Datenformatwerte für die Datendatei an. Diese Spezifikation enthält unter anderem den Datentyp jeder Spalte, das Vorhandensein bzw. Nichtvorhandensein eines Längen- oder NULL-Wertindikators und von Bytezeichenfolgen des Abschlusszeichens der Daten, sowie die Breite von Datentypen fester Länge. Die **BCPInit** -Methode legt diese Werte fest wie folgt:  
  
-   Der angegebene Datentyp entspricht dem Datentyp der Spalte in der Datenbanktabelle, der Sicht oder dem SELECT-Resultset. Der Datentyp wird von den in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Headerdatei (sqlncli.h) angegebenen systemeigenen Datentypen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgelistet. Ihre Werte weisen das Muster BCP_TYPE_XXX auf. Die Daten werden in computereigenem Format dargestellt, d. h. Daten aus einer Spalte vom integer-Datentyp werden in einer Sequenz aus vier Byte dargestellt, die, abhängig von dem Computer, auf dem die Datendatei erstellt wurden, das Format Big-Endian oder Little-Endian aufweisen.  
  
-   Wenn ein Datenbankdatentyp eine feste Länge hat, haben auch die Daten der Datendatei eine feste Länge. Beim Verarbeiten der Daten durch Massenkopiermethoden (beispielsweise [IBCPSession::BCPExec](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)) werden die Datenzeilen analysiert. Dabei wird erwartet, dass die Länge der Daten in der Datendatei identisch ist mit der in der Datenbanktabelle, Sicht oder SELECT-Spaltenliste angegebenen Länge der Daten. So müssen beispielsweise Daten für eine als `char(13)` definierte Datenbankspalte in jeder Zeile der Datei 13 Zeichen belegen. Für Daten mit fester Länge kann ein NULL-Indikator verwendet werden, wenn die Datenbankspalte NULL-Werte zulässt.  
  
-   Zum Kopieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss die Datendatei für jede Spalte der Datenbanktabelle Daten aufweisen. Beim Kopieren von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Daten von allen Spalten der Datenbanktabelle, der Sicht oder des SELECT-Resultsets in die Datendatei kopiert.  
  
-   Beim Kopieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss die Ordnungsposition einer Spalte in der Datendatei der Ordnungsposition der Spalte in der Datenbanktabelle genau entsprechen. Beim Kopieren von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] platziert die **BCPExec**-Methode Daten auf der Grundlage der Ordnungsposition der Spalte in der Datenbanktabelle.  
  
-   Für Datenbank-Datentypen variabler Länge (beispielsweise `varbinary(22)`) und Datenbankspalten, die NULL-Werte zulassen, wird den Daten in der Datendatei ein Längen-/NULL-Indikator als Präfix hinzugefügt. Die Breite des Indikators ändert sich auf der Grundlage des Datentyps und der Version der Massenkopierfunktion. Die BCP_OPTION_FILEFMT-Option der [IBCPSession::BCPControl](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)-Methode gewährleistet die Kompatibilität zwischen früheren Datendateien für Massenkopiervorgänge und Servern, auf denen höhere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden, indem sie signalisiert, wenn die Breite der Indikatoren in den Daten kleiner ist als erwartet.  
  
> [!NOTE]  
>  Verwenden Sie zum Ändern der für eine Datendatei angegebenen Datenformatwerte die Methoden [IBCPSession::BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) und [IBCPSession::BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md).  
  
 Mithilfe der Datenbankoption **select into/bulkcopy** können Massenkopiervorgänge in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für Tabellen optimiert werden, die keinen Index enthalten.  
  
## <a name="arguments"></a>Argumente  
 *pwszTable*[in]  
 Name der Datenbanktabelle, in die bzw. aus der kopiert werden soll. Der Name kann den Namen der Datenbank oder den Namen des Besitzers enthalten. Beispiel: "pubs.username.titles", "pubs..titles", "username.titles".  
  
 Wenn für das eDirection-Argument BCP_DIRECTION_OUT festgelegt ist, kann das pwszTable-Argument den Namen einer Datenbanksicht annehmen.  
  
 Wird für das **eDirection** -Argument BCP_DIRECTION_OUT festgelegt und mithilfe der **BCPControl** -Methode eine SELECT-Anweisung angegeben, bevor die BCPExec-Methode aufgerufen wird, muss für das *pwszTable* -Argument NULL festgelegt werden.  
  
 *pwszDataFile*[in]  
 Name der Benutzerdatei, in die bzw. aus der kopiert werden soll.  
  
 *pwszErrorFile*[in]  
 Der Name der Fehlerdatei, in die Statusmeldungen, Fehlermeldungen und Kopien von Zeilen geschrieben werden sollen, die nicht von einer Benutzerdatei in eine Tabelle kopiert werden konnten. Wenn für das *pwszErrorFile* -Argument NULL festgelegt wird, wird keine Fehlerdatei verwendet.  
  
 *eDirection*[in]  
 Die Richtung des Kopiervorgangs, entweder BCP_DIRECTION_IN oder BCP_DIRECTION_OUT. BCP_DIRECTION_IN steht für eine Kopie von einer Benutzerdatei in eine Datenbanktabelle; BCP_DIRECTION_OUT steht für eine Kopie von einer Datenbanktabelle in eine Benutzerdatei.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_FAIL  
 Ein Anbieter spezifischer Fehler ist aufgetreten. Ausführliche Informationen erhalten Sie über die [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) -Schnittstelle.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund nicht genügenden Arbeitsspeichers  
  
 E_INVALIDARG  
 Mindestens eines der Argumente wurde nicht ordnungsgemäß angegeben. Zum Beispiel wurde ein ungültiger Dateiname angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
