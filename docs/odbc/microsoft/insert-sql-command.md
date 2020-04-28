---
title: INSERT-SQL-Befehl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- INSERT [ODBC]
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ce00005fb1aa0ca9732fc5e9cfeacd6faf6ef9e1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300005"
---
# <a name="insert---sql-command"></a>INSERT (SQL-Befehl)
Fügt einen Datensatz an das Ende einer Tabelle an, die die angegebenen Feldwerte enthält.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiber spezifische Informationen finden Sie in den hinweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Argumente  
 In *dbf_name* einfügen  
 Gibt den Namen der Tabelle an, an die der neue Datensatz angefügt wird. *dbf_name* kann einen Pfad enthalten und kann ein namens Ausdruck sein.  
  
 Wenn die von Ihnen angegebene Tabelle nicht geöffnet ist, wird Sie ausschließlich in einem neuen Arbeitsbereich geöffnet, und der neue Datensatz wird an die Tabelle angehängt. Der neue Arbeitsbereich ist nicht ausgewählt. der aktuelle Arbeitsbereich bleibt ausgewählt.  
  
 Wenn die von Ihnen angegebene Tabelle geöffnet ist, fügt INSERT den neuen Datensatz an die Tabelle an. Wenn die Tabelle in einem anderen Arbeitsbereich als dem aktuellen Arbeitsbereich geöffnet ist, wird Sie nach dem Anfügen des Datensatzes nicht ausgewählt. der aktuelle Arbeitsbereich bleibt ausgewählt.  
  
 [( *fname1*[, *fname2*[,...]])]  
 Gibt die Namen der Felder im neuen Datensatz an, in die die Werte eingefügt werden.  
  
 Werte ( *eExpression1*[, *eExpression2*[,...]])  
 Gibt die Feldwerte an, die in den neuen Datensatz eingefügt werden. Wenn Sie die Feldnamen weglassen, müssen Sie die Feldwerte in der von der Tabellenstruktur definierten Reihenfolge angeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der neue Datensatz enthält die Daten, die in der VALUES-Klausel aufgeführt sind.  
  
## <a name="driver-remarks"></a>Hinweise zu Treibern  
 Wenn Ihre Anwendung die INSERT-Anweisung der ODBC-SQL-Anweisung an die Datenquelle sendet, konvertiert der Visual FoxPro-ODBC-Treiber den Befehl ohne Übersetzung in den Visual foxproinsert-Befehl.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE TABLE-SQL-Befehl](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT (SQL-Befehl)](../../odbc/microsoft/select-sql-command.md)
