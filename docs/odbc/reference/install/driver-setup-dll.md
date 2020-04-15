---
title: Treiber-Setup-DLL | Microsoft Docs
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
ms.openlocfilehash: a0a2878591c92fe0b2070a295d9dc622c245c17e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306421"
---
# <a name="driver-setup-dll"></a>Setup-DLL für Treiber
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur explizit auf früheren Windows-Versionen installieren.  
  
 Die Treiber-Setup-DLL enthält die **Funktionen ConfigDriver** und **ConfigDSN.** **ConfigDriver** führt treiberspezifische Installationsaufgaben aus, z. B. die Eingabe treiberspezifischer Informationen in die Registrierung. **ConfigDSN** verwaltet treiberspezifische Informationen zu Datenquellen in der Registrierung. Eine vollständige Beschreibung dieser Funktionen finden Sie unter [Setup-DLL-API-Referenz](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** ruft die folgenden Funktionen in der Installations-DLL auf, um Datenquelleninformationen in der Registrierung zu verwalten:  
  
-   **SQLWriteDSNToIni**. Fügen Sie eine Datenquelle hinzu.  
  
-   **SQLRemoveDSNFromIni**. Löschen Sie eine Datenquelle.  
  
-   **SQLWritePrivateProfileString**. Schreiben Sie einen treiberspezifischen Wert unter einen Unterschlüssel für die Datenquellenspezifikation.  
  
-   **SQLGetPrivateProfileString**. Lesen Sie einen treiberspezifischen Wert aus einem Datenquellenspezifikationsunterschlüssel.  
  
-   **SQLGetTranslator**. Fordern Sie den Benutzer auf, einen Übersetzernamen und eine Option zu verwenden. Diese Funktion ruft **ConfigTranslator** in der Übersetzer-Setup-DLL auf.  
  
 Die Treiber-Setup-DLL wird vom Treiberentwickler geschrieben. Es kann Teil der Treiber-DLL oder einer separaten DLL sein.
