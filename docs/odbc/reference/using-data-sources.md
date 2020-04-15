---
title: Verwenden von Datenquellen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df9b09e4c5519e0fff44902bd83b8e3d92a67ca8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286540"
---
# <a name="using-data-sources"></a>Verwenden von Datenquellen
Datenquellen werden in der Regel vom Endbenutzer oder einem Techniker mit einem Programm namens *ODBC Administrator*erstellt. Der ODBC-Administrator fordert den Benutzer auf, den Treiber zu verwenden, und ruft diesen Treiber dann auf. Der Treiber zeigt ein Dialogfeld an, das die Informationen anfordert, die er zum Herstellen einer Verbindung mit der Datenquelle benötigt. Nachdem der Benutzer die Informationen eingibt, speichert der Treiber sie auf dem System.  
  
 Später ruft die Anwendung den Treiber-Manager auf und übergibt ihm den Namen einer Computerdatenquelle oder den Pfad einer Datei, die eine Dateidatenquelle enthält. Wenn ein Computerdatenquellenname übergeben wird, durchsucht der Treiber-Manager das System, um den von der Datenquelle verwendeten Treiber zu finden. Anschließend wird der Treiber geladen und der Datenquellenname an ihn weitergereicht. Der Treiber verwendet den Datenquellennamen, um die Informationen zu finden, die er zum Herstellen einer Verbindung mit der Datenquelle benötigt. Schließlich stellt es eine Verbindung mit der Datenquelle her, wobei der Benutzer in der Regel zur Eingabe einer Benutzer-ID und eines Kennworts aufgefordert wird, die im Allgemeinen nicht gespeichert werden.  
  
 Wenn eine Dateidatenquelle übergeben wird, öffnet der Treiber-Manager die Datei und lädt den angegebenen Treiber. Wenn die Datei auch eine Verbindungszeichenfolge enthält, wird diese an den Treiber weitergereicht. Unter Verwendung der Informationen in der Verbindungszeichenfolge stellt der Treiber eine Verbindung mit der Datenquelle her. Wenn keine Verbindungszeichenfolge übergeben wurde, fordert der Treiber den Benutzer in der Regel zur Eingabe der erforderlichen Informationen auf.
