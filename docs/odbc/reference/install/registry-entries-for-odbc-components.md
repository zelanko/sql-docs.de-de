---
description: Registrierungseinträge für ODBC-Komponenten
title: Registrierungseinträge für ODBC-Komponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- installing ODBC components [ODBC], registry entries
- registry entries for components [ODBC]
- subkeys [ODBC], for components
- registry entries for components [ODBC], about registry entries
ms.assetid: c90aa8a4-6ece-48de-901c-17d23739a9ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e3364f2b38fdb0c41ae0493b545740b17ee712bf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491335"
---
# <a name="registry-entries-for-odbc-components"></a>Registrierungseinträge für ODBC-Komponenten
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 Die Installer-DLL verwaltet Informationen zu allen installierten ODBC-Komponenten in der Registrierung. Auf Computern, auf denen Microsoft Windows NT und Microsoft Windows 95/98 ausgeführt wird, werden diese Informationen in unter Schlüsseln unter dem folgenden Schlüssel in der Registrierung gespeichert:  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbcinst.ini
 ```

 Da Odbcinst.ini ein Unterschlüssel der HKEY_LOCAL_MACHINE Struktur ist, sind die Informationen zu ODBC-Komponenten für alle Benutzer des Computers verfügbar.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Unterschlüssel für ODBC-Kernkomponenten](../../../odbc/reference/install/odbc-core-subkey.md)  
  
-   [Unterschlüssel für ODBC-Treiber](../../../odbc/reference/install/odbc-drivers-subkey.md)  
  
-   [Unterschlüssel für Treiberspezifikationen](../../../odbc/reference/install/driver-specification-subkeys.md)  
  
-   [Unterschlüssel für Standardtreiber](../../../odbc/reference/install/default-driver-subkey.md)  
  
-   [Unterschlüssel für ODBC-Konvertierungsprogramme](../../../odbc/reference/install/odbc-translators-subkey.md)  
  
-   [Unterschlüssel für Konvertierungsprogrammspezifikationen](../../../odbc/reference/install/translator-specification-subkeys.md)
