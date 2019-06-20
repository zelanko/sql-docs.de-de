---
title: Konvertierungs-DLLs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translation DLLs [ODBC]
ms.assetid: 38975059-b346-410f-bb27-326f3f7bbf39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec1d0e23019f3e5b68ad38711c1f041b160ceb31
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305752"
---
# <a name="translation-dlls"></a>Übersetzungs-DLLs
Die Anwendung und die Datenquellensicht speichern oft Daten in anderen Zeichensätze. ODBC bietet es sich um einen generischen Mechanismus dar, der Daten aus einem Zeichensatz in eine andere übersetzt den Treiber ermöglicht. Es besteht aus einer DLL, die die Übersetzung Funktionen implementiert **SQLDriverToDataSource** und **SQLDataSourceToDriver**, die aufgerufen werden, indem alle übertragenen Daten zwischen der Datenquelle übersetzt der Treiber und Treiber. Diese DLL-Datei geschrieben werden kann, durch den Treiber-Entwickler, Anwendungsentwickler oder einem Drittanbieter.  
  
 Der Konvertierungs-DLL für eine bestimmte Datenquelle kann in die Systeminformationen für die Datenquelle angegeben werden. Weitere Informationen finden Sie unter [Datenquellenspezifikationen](../../../odbc/reference/install/data-source-specification-subkeys.md). Sie können auch zur Laufzeit mit der SQL_ATTR_TRANSLATE_DLL und SQL_ATTR_TRANSLATE_OPTION Verbindungsattribute festgelegt werden.  
  
 Die Übersetzungsoption wird ein Wert, der nur von einer bestimmten DLL-Übersetzung interpretiert werden kann. Wenn die Übersetzung zwischen verschiedenen Codepages DLL übersetzt wird, kann die Option z. B. die Anzahl von Codepages verwendet werden, von der Anwendung und der Datenquelle geben. Besteht keine Notwendigkeit für eine Übersetzung DLL eine Übersetzungsoption verwenden.  
  
 Nach der eine Übersetzung, die DLL angegeben wurde, wird der Treiber geladen und aufgerufen, um alle Datenflüsse zwischen der Anwendung und die Datenquelle übersetzt. Dies schließt alle SQL-Anweisungen und Zeichenparameter, die an die Datenquelle gesendet werden, und alle Zeichens, Metadaten von Zeichen wie z. B. Spaltennamen und Fehlermeldungen abgerufen werden, aus der Datenquelle. Verbindungsdaten ist nicht übersetzt, da der Konvertierungs-DLL nicht erst geladen wird, nachdem die Anwendung eine Verbindung mit der Datenquelle hergestellt hat.
