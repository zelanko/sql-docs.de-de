---
title: Binden von Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a634a553672b83931091056dd489f7559c4269b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106214"
---
# <a name="binding-columns"></a>Binden von Spalten
Aus der Datenquelle abgerufene Daten werden in Variablen, die die Anwendung zu diesem Zweck zugeordnet hat, an die Anwendung zurückgegeben. Bevor dies möglich ist, muss die Anwendung diese Variablen den Spalten des Resultsets zuordnen bzw. diese *binden*. konzeptionell ist dieser Vorgang identisch mit dem Binden von Anwendungsvariablen an Anweisungs Parameter. Wenn die Anwendung eine Variable an eine Resultsetspalte bindet, wird diese Variable-Address, Datentyp usw. für den Treiber beschrieben. Der Treiber speichert diese Informationen in der Struktur, die er für diese Anweisung verwaltet, und verwendet die Informationen, um den Wert aus der Spalte zurückzugeben, wenn die Zeile abgerufen wird.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Binden von Resultsetspalten](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Verwenden von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
