---
title: Ibcpsession (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPInit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11ddae5bacdd5428a4381ec034d9dc9f0f22b6b7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413401"
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
  Initialisiert die Massenkopierstruktur, führt einige Fehlerprüfungen durch, überprüft die korrekte Angabe der Daten- und Formatdateinamen und öffnet dann diese Dateien.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPInit(   
const wchar_t *pwszTable,  
const wchar_t *pwszDataFile,  
const wchar_t *pwszErrorFile,  
inteDirection);  
```  
  
## <a name="remarks"></a>Hinweise  
 Die **BCPInit** -Methode sollte vor jeder anderen Massenkopiermethode aufgerufen werden. Die **BCPInit** Methode führt die erforderlichen Initialisierungen für einen Massenkopiervorgang von Daten zwischen der Workstation und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Die **BCPInit** -Methode untersucht die Struktur der Quell- oder Zieltabelle der Datenbank, nicht jedoch die Datendatei. Sie gibt basierend auf den einzelnen Spalten in der Datenbanktabelle, der Sicht oder dem SELECT-Resultset Datenformatwerte für die Datendatei an. Diese Spezifikation enthält unter anderem den Datentyp jeder Spalte, das Vorhandensein bzw. Nichtvorhandensein eines Längen- oder NULL-Wertindikators und von Bytezeichenfolgen des Abschlusszeichens der Daten, sowie die Breite von Datentypen fester Länge. Die **BCPInit** -Methode legt diese Werte fest wie folgt:  
  
-   Der angegebene Datentyp entspricht dem Datentyp der Spalte in der Datenbanktabelle, der Sicht oder dem SELECT-Resultset. Der Datentyp aufgelistet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im angegebenen systemeigenen Datentypen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Headerdatei (sqlncli.h). Ihre Werte weisen das Muster BCP_TYPE_XXX auf. Die Daten werden in computereigenem Format dargestellt, d. h. Daten aus einer Spalte vom integer-Datentyp werden in einer Sequenz aus vier Byte dargestellt, die, abhängig von dem Computer, auf dem die Datendatei erstellt wurden, das Format Big-Endian oder Little-Endian aufweisen.  
  
-   Wenn ein Datenbankdatentyp eine feste Länge hat, haben auch die Daten der Datendatei eine feste Länge. Massenkopieren-Methoden, die Daten verarbeiten (z. B. [Ibcpsession](ibcpsession-bcpexec-ole-db.md)) werden die Datenzeilen, die erwartet wird die Länge der Daten in der Datendatei identisch mit der Länge der die Daten in die Datenbanktabelle, Sicht oder Spalte auswählen, werden analysiert Liste. So müssen beispielsweise Daten für eine als `char(13)` definierte Datenbankspalte in jeder Zeile der Datei 13 Zeichen belegen. Für Daten mit fester Länge kann ein NULL-Indikator verwendet werden, wenn die Datenbankspalte NULL-Werte zulässt.  
  
-   Beim Kopieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], muss die Datendatei die Daten für jede Spalte in der Datenbanktabelle. Beim Kopieren von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Daten aus allen Spalten in der Datenbanktabelle, Sicht oder SELECT-Resultset in die Datendatei kopiert werden.  
  
-   Beim Kopieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die Ordnungsposition einer Spalte in der Datendatei muss mit der Position der Spalte in der Datenbanktabelle identisch sein. Beim Kopieren von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **BCPExec** -Methode setzt die Daten auf Grundlage der Ordnungsposition der Spalte in der Datenbanktabelle.  
  
-   Für Datenbank-Datentypen variabler Länge (beispielsweise `varbinary(22)`) und Datenbankspalten, die NULL-Werte zulassen, wird den Daten in der Datendatei ein Längen-/NULL-Indikator als Präfix hinzugefügt. Die Breite des Indikators ändert sich auf der Grundlage des Datentyps und der Version der Massenkopierfunktion. Die [ibcpsession:: Bcpcontrol](ibcpsession-bcpcontrol-ole-db.md) BCP_OPTION_FILEFMT-Option für die Methode gewährleistet die Kompatibilität zwischen früheren Datendateien für Massenkopiervorgänge und Servern, auf denen höhere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durch, der angibt, wenn die Breiten der Indikatoren in der Daten sind geringer ist als erwartet.  
  
> [!NOTE]  
>  Um die für eine Datendatei angegebenen datenformatwerte zu ändern, verwenden die [ibcpsession:: BCPColumns](ibcpsession-bcpcolumns-ole-db.md) und [ibcpsession:: BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) Methoden.  
  
 Massenkopiervorgänge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann optimiert werden, für die Tabellen, die keine Indizes enthalten durch Festlegen der Datenbankoption **in select / Bulkcopy**.  
  
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
 Ein Anwenderspezifischer Fehler ist aufgetreten "verwenden Sie ausführliche Informationen, die [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) Schnittstelle.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund nicht genügenden Arbeitsspeichers  
  
 E_INVALIDARG  
 Mindestens eines der Argumente wurde nicht ordnungsgemäß angegeben. Zum Beispiel wurde ein ungültiger Dateiname angegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IBCPSession &#40;OLE-DB&#41;](ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../native-client/features/performing-bulk-copy-operations.md)  
  
  
