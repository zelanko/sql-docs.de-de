---
title: Bindungsspalten | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301821"
---
# <a name="binding-columns"></a>Binden von Spalten
Daten, die aus der Datenquelle abgerufen werden, werden in Variablen an die Anwendung zurückgegeben, die die Anwendung zu diesem Zweck zugewiesen hat. Bevor dies möglich ist, muss die Anwendung diese Variablen den Spalten des Resultsets zuordnen oder *binden.* konzeptionell ist dieser Prozess derselbe wie das Binden von Anwendungsvariablen an Anweisungsparameter. Wenn die Anwendung eine Variable an eine Ergebnissatzspalte bindet, wird diese Variable - Adresse, Datentyp usw. - an den Treiber beschrieben. Der Treiber speichert diese Informationen in der Struktur, die er für diese Anweisung verwaltet, und verwendet die Informationen, um den Wert aus der Spalte zurückzugeben, wenn die Zeile abgerufen wird.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Binden von Resultsetspalten](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Verwenden von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
