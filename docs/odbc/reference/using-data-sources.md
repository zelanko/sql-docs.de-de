---
title: Verwenden von Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], about data sources
ms.assetid: d5550619-22b2-4b16-bd08-fbabb6554c40
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 52015cb202f46c50c16dcab408bed7761f0925db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951803"
---
# <a name="using-data-sources"></a>Verwenden von Datenquellen
Datenquellen werden in der Regel vom Benutzer erstellt oder ein Techniker mit einem Programm Namens der *ODBC-Administrator*. Der ODBC-Administrator fordert den Benutzer für den Treiber verwenden und ruft dann diesen Treiber. Der Treiber zeigt ein Dialogfeld, das die Informationen anfordert, wird, die es eine Verbindung mit der Datenquelle herstellen muss. Nachdem der Benutzer die Informationen eingegeben hat, werden Sie von der Treiber auf dem System gespeichert.  
  
 Später wird die Anwendung ruft der Treiber-Manager, und übergibt sie den Namen einer Datenquelle für den Computer oder den Pfad einer Datei mit einer Datenquelle. Wenn Computername der Datenquelle zu übergeben, sucht der Treiber-Manager das System, um die Suche nach dem Treiber, die von der Datenquelle verwendet. Anschließend wird der Treiber geladen und der Name der Datenquelle übergeben. Der Treiber verwendet den Datenquellennamen, um die gesuchten Informationen mit mit der Datenquelle hergestellt werden muss. Zum Schluss verbindet ihn mit der Datenquelle, die in der Regel den Benutzer aufzufordern, Benutzer-ID und das Kennwort, die in der Regel nicht gespeichert werden.  
  
 Wenn eine Datenquelle übergeben wird, wird der Treiber-Manager öffnet die Datei und lädt den angegebenen Treiber. Wenn die Datei auch eine Verbindungszeichenfolge enthält, übergibt er diese an den Treiber. Mit den Informationen in der Verbindungszeichenfolge verbindet der Treiber mit der Datenquelle. Wenn keine Verbindungszeichenfolge übergeben wurde, fordert der Treiber in der Regel der Benutzer die erforderlichen Informationen.
