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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fca4cfb1455c91ca57f7b1769266e2040d6a3511
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301821"
---
# <a name="binding-columns"></a>Binden von Spalten
Aus der Datenquelle abgerufene Daten werden in Variablen, die die Anwendung zu diesem Zweck zugeordnet hat, an die Anwendung zurückgegeben. Bevor dies möglich ist, muss die Anwendung diese Variablen den Spalten des Resultsets zuordnen bzw. diese *binden*. konzeptionell ist dieser Vorgang identisch mit dem Binden von Anwendungsvariablen an Anweisungs Parameter. Wenn die Anwendung eine Variable an eine Resultsetspalte bindet, wird diese Variable-Address, Datentyp usw. für den Treiber beschrieben. Der Treiber speichert diese Informationen in der Struktur, die er für diese Anweisung verwaltet, und verwendet die Informationen, um den Wert aus der Spalte zurückzugeben, wenn die Zeile abgerufen wird.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Binden von Resultsetspalten](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Verwenden von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
