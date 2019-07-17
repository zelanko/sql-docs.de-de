---
title: Setup-DLL für Treiber | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: df91638f91091940e00e7a6a19d0fd6cb700f85f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094163"
---
# <a name="driver-setup-dll"></a>Setup-DLL für Treiber
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003, ist ODBC in das Windows-Betriebssystem enthalten. Sie sollten nur explizit ODBC in früheren Versionen von Windows installieren.  
  
 Der Setup-DLL enthält Treiber die **ConfigDriver** und **ConfigDSN** Funktionen. **ConfigDriver** -Treiber-spezifischen Installationsaufgaben wie das Eingeben von treiberspezifische Informationen in die Registrierung ausgeführt. **ConfigDSN** treiberspezifische Informationen zu den Datenquellen in der Registrierung verwaltet. Eine vollständige Beschreibung dieser Funktionen, finden Sie unter [-Setup-DLL-API-Referenz](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** ruft Sie die folgenden Funktionen in das Installationsprogramm-DLL von Datenquelleninformationen in der Registrierung zu verwalten:  
  
-   **SQLWriteDSNToIni**. Fügen Sie eine Datenquelle hinzu.  
  
-   **SQLRemoveDSNFromIni**. Löschen einer Datenquelle.  
  
-   **SQLWritePrivateProfileString**. Schreiben Sie einen Treiber-spezifischen Wert unter einem Unterschlüssel von Data Source-Spezifikation.  
  
-   **SQLGetPrivateProfileString**. Gelesen Sie einen treiberspezifische-Wert aus dem Unterschlüssel Data Source-Spezifikation.  
  
-   **SQLGetTranslator**. Der Benutzer für einen Übersetzer-Namen und eine Option aufgefordert. Diese Funktion ruft **ConfigTranslator** in die Translator-setup-DLL.  
  
 Der Setup-Treiber DLL wird vom Treiber Entwickler geschrieben werden. Teil des Treibers möglich DLL oder einer separaten DLL.
