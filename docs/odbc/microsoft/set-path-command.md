---
title: SET PATH Befehl | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET PATH command [ODBC]
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e44093c3ea18bc995264a8974726f5af0abe3b3a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300820"
---
# <a name="set-path-command"></a>SET PATH-Befehl
Gibt einen Pfad für Dateisuchen an. Treiberspezifische Informationen finden Sie in den Anmerkungen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Argumente  
 ZU [ *Pfad*]  
 Gibt die Verzeichnisse an, die Visual FoxPro durchsuchen soll. Verwenden Sie Kommas oder Semikolons, um die Verzeichnisse zu trennen.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit SET PATH können Sie Suchpfade für andere Visual FoxPro-Programme angeben, die innerhalb gespeicherter Prozeduren aufgerufen werden können. SET PATH ändert den Pfad der Datenquelle, die Sie für die Verbindung angegeben haben, nicht.  
  
 Geben Sie SET PATH TO ohne *Pfad* aus, um den Pfad zum Standardverzeichnis oder -ordner wiederherzustellen.  
  
## <a name="driver-remarks"></a>Driver-Bemerkungen  
 Wenn Sie SET PATH in einer gespeicherten Prozedur ausgeben, wird es von den folgenden Funktionen und Befehlen ignoriert:  
  
-   Katalogfunktionen wie [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) und [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) ignorieren den neuen Pfad und verweisen weiterhin auf den Pfad, der von der Datenquelle in [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) oder [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)angegeben wird.  
  
-   Befehle wie SELECT, INSERT, UPDATE, DELETE und CREATE TABLE ignorieren den neuen Pfad und verweisen weiterhin auf den Pfad, der von der Datenquelle in **SQLPrepare** oder **SQLExecDirect**angegeben wird.  
  
 Wenn Sie SET PATH in einer gespeicherten Prozedur ausstellen und den Pfad anschließend nicht wieder in den ursprünglichen Zustand zurücksetzen, verwenden andere Verbindungen zur Datenbank den neuen Pfad (da SET PATH nicht auf Datensitzungen beschränkt ist).  
  
 Wenn Sie Tabellen in einem anderen Verzeichnis als dem von der Datenquelle angegebenen Verzeichnis erstellen, auswählen oder aktualisieren möchten, geben Sie mit dem Befehl den vollständigen Pfad der Datei an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC Visual FoxPro Setup Dialogfeld](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (Visual FoxPro ODBC-Treiber)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (Visual FoxPro ODBC-Treiber)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (Visual FoxPro-ODBC-Treiber)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
