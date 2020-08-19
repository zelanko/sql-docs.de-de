---
description: Übersetzungs-DLLs
title: Übersetzungs-DLLs | Microsoft-Dokumentation
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
ms.openlocfilehash: 88e0fc6879db7e4b370acc62b2d0102b3ef0a375
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421454"
---
# <a name="translation-dlls"></a>Übersetzungs-DLLs
Die Anwendung und die Datenquelle speichern häufig Daten in unterschiedlichen Zeichensätzen. ODBC stellt einen generischen Mechanismus bereit, der es dem Treiber ermöglicht, Daten von einem Zeichensatz in einen anderen zu übersetzen. Sie besteht aus einer DLL, die die Übersetzungsfunktionen **sqldriverydatasource** und **sqldatasourcededriver**implementiert, die vom Treiber aufgerufen werden, um den gesamten Datenfluss zwischen der Datenquelle und dem Treiber zu übersetzen. Diese DLL kann vom Anwendungsentwickler, vom Treiber Entwickler oder von einem Drittanbieter geschrieben werden.  
  
 Die Übersetzungs-DLL für eine bestimmte Datenquelle kann in den Systeminformationen für diese Datenquelle angegeben werden. Weitere Informationen finden Sie [unter Datenquellen Spezifikations Unterschlüssel](../../../odbc/reference/install/data-source-specification-subkeys.md). Sie kann auch zur Laufzeit mit den SQL_ATTR_TRANSLATE_DLL-und SQL_ATTR_TRANSLATE_OPTION Verbindungs Attributen festgelegt werden.  
  
 Bei der Übersetzungs Option handelt es sich um einen Wert, der nur von einer bestimmten Übersetzungs-DLL interpretiert werden kann. Wenn die Übersetzungs-DLL beispielsweise zwischen verschiedenen Codepages übersetzt, gibt die Option möglicherweise die Anzahl der Codepages aus, die von der Anwendung und der Datenquelle verwendet werden. Es ist nicht erforderlich, dass eine Übersetzungs-DLL eine Übersetzungs Option verwendet.  
  
 Nachdem eine Übersetzungs-DLL angegeben wurde, lädt der Treiber Sie und ruft Sie auf, um den gesamten Datenfluss zwischen der Anwendung und der Datenquelle zu übersetzen. Dies umfasst alle SQL-Anweisungen und Zeichen Parameter, die an die Datenquelle gesendet werden, sowie alle Zeichen Ergebnisse, Zeichen Metadaten wie Spaltennamen und Fehlermeldungen, die aus der Datenquelle abgerufen werden. Die Verbindungsdaten werden nicht übersetzt, weil die Übersetzungs-DLL erst geladen wird, nachdem die Anwendung eine Verbindung mit der Datenquelle hergestellt hat.
