---
title: DELETE - SQL-Befehl | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE [ODBC]
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9757fd57d999815964266c035963de1129eaf5e8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303551"
---
# <a name="delete---sql-command"></a>DELETE (SQL-Befehl)
Markiert Datensätze zum Löschen.  
  
 Der Visual FoxPro ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie in den Anmerkungen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DELETE FROM [DatabaseName!]TableName  
   [WHERE FilterCondition1 [AND | OR FilterCondition2 ...]]  
```  
  
## <a name="arguments"></a>Argumente  
 VON [ *Datenbankname!*] *TableName*  
 Gibt die Tabelle an, in der Datensätze zum Löschen markiert sind.  
  
 *Databasename!* gibt den Namen einer Datenbank an, die die Tabelle enthält, wenn die enthaltende Datenbank nicht die mit der Datenquelle angegebene Datenbank ist. Sie müssen den Namen einer Datenbank einschließen, die die Tabelle enthält, wenn es sich bei der Datenbank nicht um die mit der Datenquelle angegebene Datenbank handelt. Fügen Sie das Ausrufezeichen (!) nach dem Datenbanknamen und vor dem Tabellennamen ein.  
  
 WO *FilterCondition1*[UND &#124; ODER *FilterCondition2*...]  
 Gibt an, dass Visual FoxPro nur bestimmte Datensätze zum Löschen markiert.  
  
 *FilterCondition* gibt die Kriterien an, die Datensätze erfüllen müssen, um zum Löschen markiert zu werden. Sie können beweitete Filterbedingungen einschließen, die Sie möchten, und sie mit dem OPERATOR AND oder OR verbinden. Sie können auch den Operator NOT verwenden, um den Wert eines logischen Ausdrucks umzukehren, oder Sie können **EMPTY**( ) verwenden, um nach einem leeren Feld zu suchen.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn SET DELETED auf ON festgelegt ist, werden zum Löschen markierte Datensätze von allen Befehlen ignoriert, die einen Bereich enthalten.  
  
 DELETE - SQL verwendet Datensatzsperren beim Markieren mehrerer Datensätze zum Löschen in Tabellen, die für den freigegebenen Zugriff geöffnet wurden. Dies reduziert Rekordkonflikte in Mehrbenutzersituationen, kann jedoch die Leistung verringern. Öffnen Sie die Tabelle für maximale Leistung für die exklusive Verwendung.  
  
## <a name="driver-remarks"></a>Driver-Bemerkungen  
 Wenn Ihre Anwendung die ODBC SQL-Anweisung DELETE an die Datenquelle sendet, konvertiert der Visual FoxPro ODBC-Treiber den Befehl ohne Übersetzung in den Befehl Visual FoxPro DELETE.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehl SET DELETED](../../odbc/microsoft/set-deleted-command.md)
