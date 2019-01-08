---
title: Daten, die von Katalogfunktionen zurückgegeben werden. | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10e3726d26e03da2f9f731babc105244dbf1ff05
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52539785"
---
# <a name="data-returned-by-catalog-functions"></a>Von Katalogfunktionen zurückgegebene Daten
Jede Katalogfunktion gibt die Daten als Resultset zurück. Dieses Resultset unterscheidet sich nicht von anderen Resultsets. Es wird in der Regel generiert, durch eine vordefinierte, parametrisiert **wählen** -Anweisung, die in der Treiber hartcodiert oder in einer Prozedur in der Datenquelle gespeichert ist. Weitere Informationen zum Abrufen von Daten aus einem Resultset zu erhalten, finden Sie unter [wurde ein Ergebnis erstellt festlegen?](../../../odbc/reference/develop-app/was-a-result-set-created.md).  
  
 Das Resultset für jede Katalogfunktion wird in der Referenz-Eintrag für diese Funktion beschrieben. Zusätzlich zu den aufgelisteten Spalten kann das Resultset treiberspezifischen Spalten nach der letzten vordefinierte Spalte enthalten. Diese Spalten (sofern vorhanden) werden in der Dokumentation zu Driver beschrieben.  
  
 Anwendungen sollten treiberspezifischen Spalten relativ zum Ende des Resultsets binden. D. h. sie sollte berechnen Sie die Anzahl einer Spalte treiberspezifische als die Anzahl der letzten Spalte - mit abgerufen **SQLNumResultCols** – abzüglich der Anzahl der Spalten, die nach der erforderlichen Spalte auftreten. Dies spart müssen die Anwendung zu ändern, wenn neue Spalten, bis das Ergebnis hinzugefügt werden festgelegt in zukünftigen Versionen von ODBC oder dem Treiber. Für dieses Schema zu arbeiten müssen Treiber neue treiberspezifische Spalten vor der alten treiberspezifischen Spalten hinzufügen, sodass Spaltennummern relativ zum Ende des Resultsets nicht geändert werden.  
  
 Bezeichner, die im Resultset zurückgegeben werden sind nicht in Anführungszeichen eingeschlossen, selbst wenn sie Sonderzeichen enthalten. Nehmen wir beispielsweise an den Bezeichner Anführungszeichens (d. h. treiberspezifische und über zurückgegebenen **SQLGetInfo**) ist ein doppeltes Anführungszeichen ("), und der Tabelle" Accounts Payable "enthält eine Spalte namens" Customer Name ". In der Zeile, die vom **SQLColumns** für diese Spalte wird der Wert der Spalte TABLE_NAME Accounts Payable, nicht "Accounts Payable", und der Wert der COLUMN_NAME-Spalte Kundennamen, nicht "Kundenname". Um die Namen der Kunden in der Tabelle Accounts Payable abzurufen, würde die Anwendung diese Namen Zitat:  
  
```  
SELECT "Customer Name" FROM "Accounts Payable"  
```  
  
 Weitere Informationen finden Sie unter [Bezeichner in Anführungszeichen](../../../odbc/reference/develop-app/quoted-identifiers.md).  
  
 Die Katalogfunktionen basiert auf einer SQL-ähnlichen Autorisierungsmodell in der eine Verbindung hergestellt, basierend auf einem Benutzernamen und das Kennwort ein, und nur Daten, die für die der Benutzer eine Berechtigung verfügt, werden zurückgegeben. Kennwortschutz von den einzelnen Dateien, die nicht in dieses Modell passt, wird die Treiber definiert.  
  
 Die durch die Katalogfunktionen zurückgegebenen Resultsets können fast nie aktualisiert werden, und Anwendungen sollten nicht erwarten, damit die Struktur der Datenbank zu ändern, indem Sie Daten in diesen Resultsets geändert werden kann.
