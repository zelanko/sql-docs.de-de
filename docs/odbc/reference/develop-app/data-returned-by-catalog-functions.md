---
description: Von Katalogfunktionen zurückgegebene Daten
title: Von Katalog Funktionen zurückgegebene Daten | Microsoft-Dokumentation
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
ms.openlocfilehash: 4c42319520696060cd52c14c46f968badee27e20
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429362"
---
# <a name="data-returned-by-catalog-functions"></a>Von Katalogfunktionen zurückgegebene Daten
Jede Katalog Funktion gibt Daten als Resultset zurück. Dieses Resultset unterscheidet sich nicht von anderen Resultsets. Sie wird normalerweise durch eine vordefinierte, parametrisierte **Select** -Anweisung generiert, die im Treiber hart codiert ist oder in einer Prozedur in der Datenquelle gespeichert ist. Informationen zum Abrufen von Daten aus einem Resultset finden Sie unter [Was ist ein Resultset erstellt?](../../../odbc/reference/develop-app/was-a-result-set-created.md).  
  
 Das Resultset für jede Katalog Funktion wird im Verweis Eintrag für diese Funktion beschrieben. Zusätzlich zu den aufgelisteten Spalten kann das Resultset Treiber spezifische Spalten nach der letzten vordefinierten Spalte enthalten. Diese Spalten (sofern vorhanden) werden in der Treiber Dokumentation beschrieben.  
  
 Anwendungen sollten Treiber spezifische Spalten in Relation zum Ende des Resultsets binden. Das heißt, Sie sollten die Nummer einer treiberspezifischen Spalte als die Nummer der letzten Spalte berechnen, die mit **SQLNumResultCols** abgerufen wird. die Anzahl der Spalten, die nach der erforderlichen Spalte aufgetreten sind, ist geringer. Dies spart, wenn die Anwendung geändert werden muss, wenn dem Resultset in zukünftigen Versionen von ODBC oder dem Treiber neue Spalten hinzugefügt werden. Damit dieses Schema funktioniert, müssen Treiber vor den alten treiberspezifischen Spalten neue Treiber spezifische Spalten hinzufügen, damit sich die Spalten Nummern relativ zum Ende des Resultsets nicht ändern.  
  
 Bezeichner, die im Resultset zurückgegeben werden, werden nicht in Anführungszeichen eingeschlossen, auch wenn Sie Sonderzeichen enthalten. Nehmen wir beispielsweise an, dass das bezeichneranführungs Zeichen (das Treiber spezifisch und durch **SQLGetInfo**zurückgegeben wird) ein doppeltes Anführungszeichen (") und die Tabelle mit den zu zahlenden Konten eine Spalte namens" Customer Name "enthält. In der Zeile, die von **SQLColumns** für diese Spalte zurückgegeben wurde, ist der Wert der Spalte "table_name" Konten, die nicht "Konten ist bezahlt", und der Wert der Spalte "column_name" ist "Customer Name" und nicht "Customer Name". Zum Abrufen der Namen von Kunden in der Tabelle mit den Konten, die Sie bezahlen müssen, würde die Anwendung diese Namen angeben:  
  
```  
SELECT "Customer Name" FROM "Accounts Payable"  
```  
  
 Weitere Informationen finden Sie unter Bezeichner in Anführungs [Zeichen.](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
 Die Katalog Funktionen basieren auf einem SQL-ähnlichen Autorisierungs Modell, in dem eine Verbindung basierend auf einem Benutzernamen und einem Kennwort hergestellt wird, und nur Daten, für die der Benutzer über eine Berechtigung verfügt, werden zurückgegeben. Der Kenn Wort Schutz einzelner Dateien, die nicht in dieses Modell passen, ist Treiber definiert.  
  
 Die von den Katalog Funktionen zurückgegebenen Resultsets sind fast nie aktualisierbar, und Anwendungen sollten nicht erwarten, dass die Struktur der Datenbank durch Ändern der Daten in diesen Resultsets geändert werden kann.
