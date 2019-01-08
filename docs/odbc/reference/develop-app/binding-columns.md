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
manager: craigg
ms.openlocfilehash: 88e3593276851b6ab38fde0472a70be31b7cbf34
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52531874"
---
# <a name="binding-columns"></a>Binden von Spalten
Aus der Datenquelle abgerufene Daten werden in der Variablen an die Anwendung zurückgegeben, der für diesen Zweck die Anwendung belegt wird. Bevor Sie dies tun kann, muss die Anwendung zuzuordnen, oder *binden*, diese Variablen auf die Spalten des Resultsets festgelegt; vom Konzept her dieser Prozess ist identisch mit der Anwendungsvariablen an Anweisungsparameter zu binden. Wenn die Anwendung eine Variable an einer Resultsetspalte bindet, beschreibt es die Variable - Adresse, Datentyp und So weiter – an den Treiber. Der Treiber speichert diese Informationen in der Struktur, die sie für diese Anweisung verwaltet und verwendet die Informationen, um den Wert aus der Spalte zurückzugeben, wenn die Zeile abgerufen wird.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Binden von Resultsetspalten](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Verwenden von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
