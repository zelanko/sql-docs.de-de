---
title: Von Katalogfunktionen zurückgegebene Daten | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], result sets
- functions [ODBC], catalog functions
ms.assetid: 399e1a64-8766-4c44-81ff-445399b7a1de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a0d9b63de04f79fd95c1b06d8e84d85c6f4fea02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305228"
---
# <a name="data-returned-by-catalog-functions"></a>Von Katalogfunktionen zurückgegebene Daten
Jede Katalogfunktion gibt Daten als Resultset zurück. Dieses Resultset unterscheidet sich nicht von anderen Resultsets. Sie wird in der Regel durch eine vordefinierte, parametrisierte **SELECT-Anweisung** generiert, die im Treiber hartcodiert oder in einer Prozedur in der Datenquelle gespeichert ist. Informationen zum Abrufen von Daten aus einem Resultset finden Sie unter [Wurde ein Resultset erstellt?](../../../odbc/reference/develop-app/was-a-result-set-created.md).  
  
 Das Resultset für jede Katalogfunktion wird im Referenzeintrag für diese Funktion beschrieben. Zusätzlich zu den aufgelisteten Spalten kann das Resultset treiberspezifische Spalten nach der letzten vordefinierten Spalte enthalten. Diese Spalten (falls vorhanden) werden in der Treiberdokumentation beschrieben.  
  
 Anwendungen sollten treiberspezifische Spalten relativ zum Ende des Resultsets binden. Das heißt, sie sollten die Anzahl einer treiberspezifischen Spalte als Die Nummer der letzten Spalte berechnen - abgerufen mit **SQLNumResultCols** - abzüglich der Anzahl der Spalten, die nach der erforderlichen Spalte auftreten. Dies erspart es, die Anwendung zu ändern, wenn dem Resultset in zukünftigen Versionen von ODBC oder dem Treiber neue Spalten hinzugefügt werden. Damit dieses Schema funktioniert, müssen Treiber neue treiberspezifische Spalten vor alten treiberspezifischen Spalten hinzufügen, damit sich die Spaltennummern nicht relativ zum Ende des Resultsets ändern.  
  
 Bezeichner, die im Resultset zurückgegeben werden, werden nicht zitiert, auch wenn sie Sonderzeichen enthalten. Angenommen, das Bezeichneranführungszeichen (das treiberspezifisch ist und über **SQLGetInfo**zurückgegeben wird) ist ein doppeltes Anführungszeichen (") und die Tabelle "Kreditorenkonten" enthält eine Spalte mit dem Namen "Kundenname". In der Zeile, die von **SQLColumns** für diese Spalte zurückgegeben wird, lautet der Wert der Spalte TABLE_NAME Kreditoren, nicht "Kreditorenkonten", und der Wert der Spalte COLUMN_NAME ist "Kundenname" und nicht "Kundenname". Um die Namen von Debitoren in der Tabelle Kreditorenkonten abzurufen, würde die Anwendung folgende Namen anführen:  
  
```  
SELECT "Customer Name" FROM "Accounts Payable"  
```  
  
 Weitere Informationen finden Sie unter [Quoted Identifiers](../../../odbc/reference/develop-app/quoted-identifiers.md).  
  
 Die Katalogfunktionen basieren auf einem SQL-ähnlichen Autorisierungsmodell, bei dem eine Verbindung basierend auf einem Benutzernamen und Kennwort hergestellt wird und nur Daten zurückgegeben werden, für die der Benutzer über eine Berechtigung verfügt. Der Passwortschutz einzelner Dateien, der nicht in dieses Modell passt, ist treiberdefiniert.  
  
 Die von den Katalogfunktionen zurückgegebenen Ergebnismengen sind fast nie aufrüstbar, und Anwendungen sollten nicht erwarten, die Struktur der Datenbank ändern zu können, indem sie die Daten in diesen Resultsets ändern.
