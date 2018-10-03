---
title: Befehl SET PATH | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f3d810e66249779b2d3706e92ea39f89a0f87cff
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727548"
---
# <a name="set-path-command"></a>SET PATH-Befehl
Gibt einen Pfad für die Suche von Dateien. Treiberspezifische Informationen finden Sie in den Hinweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Argumente  
 AUF [ *Pfad*]  
 Gibt die Verzeichnisse, Visual FoxPro suchen soll. Verwenden Sie Kommas oder Semikolons, um die Verzeichnisse.  
  
## <a name="remarks"></a>Hinweise  
 SET PATH können Sie für andere Programme Visual FoxPro-Suchpfade an, die innerhalb von gespeicherten Prozeduren aufgerufen werden kann. SET PATH ändert sich nicht auf den Pfad der Datenquelle aus, die Sie für die Verbindung angegeben haben.  
  
 Geben Sie Pfad festlegen auf, ohne *Pfad* den Pfad zu dem Verzeichnis oder Ordner wiederherstellen.  
  
## <a name="driver-remarks"></a>Treiber "Hinweise".  
 Wenn Sie in einer gespeicherten Prozedur SET PATH ausgeben, wird es durch die folgenden Funktionen und Befehle ignoriert:  
  
-   Katalogfunktionen z. B. [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) und [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) ignoriert den neuen Pfad und den von der Datenquelle im angegebenen Pfad verweisen weiterhin auf [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) oder [ SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
-   Befehle wie z. B. SELECT, INSERT, UPDATE, DELETE und CREATE TABLE ignoriert den neuen Pfad und den von der Datenquelle im angegebenen Pfad verweisen weiterhin auf **SQLPrepare** oder **SQLExecDirect**.  
  
 Wenn Sie SET PATH in einer gespeicherten Prozedur ausgeben und keine anschließend wieder in den ursprünglichen Zustand Sie den Pfad legen, verwendet andere Verbindungen mit der Datenbank (da es sich um eine SET PATH nicht auf datensitzungen begrenzt ist) den neuen Pfad.  
  
 Wenn Sie ausgewählt, oder Aktualisieren von Tabellen in einem anderen Verzeichnis als die, die von der Datenquelle angegeben möchten, geben Sie den vollständigen Pfad der Datei mit dem Befehl.  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-Visual FoxPro-einrichten (Dialogfeld)](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (Visual FoxPro-ODBC-Treiber)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (Visual FoxPro-ODBC-Treiber)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (Visual FoxPro-ODBC-Treiber)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
