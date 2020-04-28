---
title: Befehl "Pfad festlegen" | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300820"
---
# <a name="set-path-command"></a>SET PATH-Befehl
Gibt einen Pfad für Datei suchen an. Treiber spezifische Informationen finden Sie in den hinweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Argumente  
 In [ *Pfad*]  
 Gibt die Verzeichnisse an, die von Visual FoxPro durchsucht werden sollen. Verwenden Sie Kommas oder Semikolons, um die Verzeichnisse voneinander zu trennen.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit Set Path können Sie Suchpfade für andere Visual FoxPro-Programme angeben, die innerhalb gespeicherter Prozeduren aufgerufen werden können. Durch Festlegen des Pfads wird der Pfad der Datenquelle, die Sie für die Verbindung angegeben haben, nicht geändert.  
  
 Problem legen Sie den Pfad auf ohne *Pfad* fest, um den Pfad zum Standardverzeichnis oder-Ordner wiederherzustellen.  
  
## <a name="driver-remarks"></a>Hinweise zu Treibern  
 Wenn Sie Set Path in einer gespeicherten Prozedur ausgeben, wird es von den folgenden Funktionen und Befehlen ignoriert:  
  
-   Katalog Funktionen wie [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) und [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) ignorieren den neuen Pfad und verweisen weiterhin auf den von der Datenquelle in [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) oder [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)angegebenen Pfad.  
  
-   Befehle wie SELECT, INSERT, Update, DELETE und CREATE TABLE ignorieren den neuen Pfad und verweisen weiterhin auf den von der Datenquelle in **SQLPrepare** oder **SQLExecDirect**angegebenen Pfad.  
  
 Wenn Sie Set Path in einer gespeicherten Prozedur ausgeben und den Pfad nicht wieder auf den ursprünglichen Zustand zurücksetzen, wird der neue Pfad von anderen Verbindungen mit der Datenbank verwendet (da Set Path nicht auf Daten Sitzungen beschränkt ist).  
  
 Wenn Sie Tabellen in einem anderen Verzeichnis als dem von der Datenquelle angegebenen Verzeichnis erstellen, auswählen oder aktualisieren möchten, geben Sie den vollständigen Pfad der Datei mit dem Befehl an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC Visual FoxPro-Setup (Dialog Feld)](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (Visual FoxPro-ODBC-Treiber)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (Visual FoxPro-ODBC-Treiber)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (Visual FoxPro-ODBC-Treiber)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
