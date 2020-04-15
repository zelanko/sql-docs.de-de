---
title: INSERT - SQL-Befehl | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300005"
---
# <a name="insert---sql-command"></a>INSERT (SQL-Befehl)
Fügt einen Datensatz am Ende einer Tabelle an, die die angegebenen Feldwerte enthält.  
  
 Der Visual FoxPro ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie in den Anmerkungen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Argumente  
 INSERT INTO *dbf_name*  
 Gibt den Namen der Tabelle an, an die der neue Datensatz angehängt wird. *dbf_name* kann einen Pfad enthalten und kann ein Namensausdruck sein.  
  
 Wenn die von Ihnen angegebene Tabelle nicht geöffnet ist, wird sie ausschließlich in einem neuen Arbeitsbereich geöffnet, und der neue Datensatz wird an die Tabelle angehängt. Der neue Arbeitsbereich ist nicht ausgewählt. der aktuelle Arbeitsbereich bleibt ausgewählt.  
  
 Wenn die von Ihnen angegebene Tabelle geöffnet ist, fügt INSERT den neuen Datensatz an die Tabelle an. Wenn die Tabelle in einem anderen Arbeitsbereich als dem aktuellen Arbeitsbereich geöffnet ist, wird sie nicht ausgewählt, nachdem der Datensatz angehängt wurde. der aktuelle Arbeitsbereich bleibt ausgewählt.  
  
 [( *fname1*[, *fname2*[, ...]]]]  
 Gibt im neuen Datensatz die Namen der Felder an, in die die Werte eingefügt werden.  
  
 VALUES ( *eExpression1*[, *eExpression2*[, ...]])  
 Gibt die Feldwerte an, die in den neuen Datensatz eingefügt wurden. Wenn Sie die Feldnamen weglassen, müssen Sie die Feldwerte in der Reihenfolge angeben, die durch die Tabellenstruktur definiert ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Der neue Datensatz enthält die in der VALUES-Klausel aufgeführten Daten.  
  
## <a name="driver-remarks"></a>Driver-Bemerkungen  
 Wenn Ihre Anwendung die ODBC SQL-Anweisung INSERT an die Datenquelle sendet, konvertiert der Visual FoxPro ODBC-Treiber den Befehl ohne Übersetzung in den Befehl Visual FoxProINSERT.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE TABLE - SQL-Befehl](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT (SQL-Befehl)](../../odbc/microsoft/select-sql-command.md)
