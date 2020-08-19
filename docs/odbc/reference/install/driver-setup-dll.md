---
description: Setup-DLL für Treiber
title: Treiber-Setup-DLL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 79fff6ce68e7860b444ebefa736cb959cd54576b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476206"
---
# <a name="driver-setup-dll"></a>Setup-DLL für Treiber
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 Die Treiber-Setup-DLL enthält die Funktionen **ConfigDriver** und **ConfigDSN** . **ConfigDriver** führt Treiber spezifische Installationsaufgaben aus, z. b. die Eingabe von treiberspezifischen Informationen in die Registrierung. **ConfigDSN** verwaltet Treiber spezifische Informationen zu Datenquellen in der Registrierung. Eine umfassende Beschreibung dieser Funktionen finden Sie unter [dll-API-Referenz für Setup](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** Ruft die folgenden Funktionen in der Installationsprogramm-dll auf, um die Datenquellen Informationen in der Registrierung beizubehalten:  
  
-   **Sqlwrite tedsnfür ini**. Fügen Sie eine Datenquelle hinzu.  
  
-   **Sqlremovedsnfromini**. Löschen Sie eine Datenquelle.  
  
-   **Sqlschreiteprivateprofilestring**. Schreiben Sie einen treiberspezifischen Wert unter einem Datenquellen Spezifikations Unterschlüssel.  
  
-   **Sqlgetprivateprofilestring**. Lesen eines treiberspezifischen Werts aus einem Datenquellen Spezifikations Unterschlüssel.  
  
-   **Sqlgettranslator**. Fordert den Benutzer auf, einen Übersetzungs Namen und eine Option einzugeben. Diese Funktion ruft **ConfigTranslator** in der Übersetzer-Setup-DLL auf.  
  
 Die Treiber-Setup-DLL wird vom Treiber Entwickler geschrieben. Es kann Teil der Treiber-DLL oder einer separaten DLL sein.
