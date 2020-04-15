---
title: Übersetzungs-DLLs | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3dad12bcd71434c1013b4fde5b4bd0231e56016f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297945"
---
# <a name="translation-dlls"></a>Übersetzungs-DLLs
Die Anwendung und datenquelle speichern Daten häufig in verschiedenen Zeichensätzen. ODBC bietet einen generischen Mechanismus, der es dem Treiber ermöglicht, Daten von einem Zeichensatz in einen anderen zu übersetzen. Es besteht aus einer DLL, die die Übersetzungsfunktionen **SQLDriverToDataSource** und **SQLDataSourceToDriver**implementiert, die vom Treiber aufgerufen werden, um alle Daten zu übersetzen, die zwischen datenquellen und Treiber fließen. Diese DLL kann vom Anwendungsentwickler, dem Treiberentwickler oder einem Drittanbieter geschrieben werden.  
  
 Die Übersetzungs-DLL für eine bestimmte Datenquelle kann in den Systeminformationen für diese Datenquelle angegeben werden. Weitere Informationen finden Sie unter [Unterschlüssel für Datenquellenspezifikation](../../../odbc/reference/install/data-source-specification-subkeys.md). Es kann auch zur Laufzeit mit den SQL_ATTR_TRANSLATE_DLL- und SQL_ATTR_TRANSLATE_OPTION-Verbindungsattributen festgelegt werden.  
  
 Die Übersetzungsoption ist ein Wert, der nur von einer bestimmten Übersetzungs-DLL interpretiert werden kann. Wenn die Übersetzungs-DLL z. B. zwischen verschiedenen Codepages übersetzt wird, gibt die Option möglicherweise die Nummern der von der Anwendung verwendeten Codepages und der Datenquelle an. Es ist nicht erforderlich, dass eine Übersetzungs-DLL eine Übersetzungsoption verwendet.  
  
 Nachdem eine Übersetzungs-DLL angegeben wurde, lädt der Treiber sie und ruft sie auf, um alle Daten zu übersetzen, die zwischen der Anwendung und der Datenquelle fließen. Dazu gehören alle SQL-Anweisungen und Zeichenparameter, die an die Datenquelle gesendet werden, sowie alle Zeichenergebnisse, Zeichenmetadaten wie Spaltennamen und aus der Datenquelle abgerufene Fehlermeldungen. Verbindungsdaten werden nicht übersetzt, da die Übersetzungs-DLL erst geladen wird, nachdem die Anwendung eine Verbindung mit der Datenquelle hergestellt hat.
