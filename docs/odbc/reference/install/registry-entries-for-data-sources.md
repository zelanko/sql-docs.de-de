---
description: Registrierungseinträge für Datenquellen
title: Registrierungseinträge für Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 82759a988a0a2ff290d67406a1450ec9cb228a82
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461302"
---
# <a name="registry-entries-for-data-sources"></a>Registrierungseinträge für Datenquellen
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 Die Installer-DLL verwaltet Informationen zu jeder Datenquelle in der Registrierung. In Microsoft Windows NT/Windows 2000 und Microsoft Windows 95/98 werden diese Informationen in unter Schlüsseln unter einem der beiden folgenden Schlüssel in der Registrierung gespeichert:  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbc.ini  
 ```

 ```console
 HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini
 ```

 Welcher Schlüssel verwendet wird, hängt davon ab, ob es sich bei der Datenquelle um eine *Systemdaten Quelle handelt,* die für alle Benutzer verfügbar ist, oder um eine *Benutzerdaten Quelle,* die nur für den aktuellen Benutzer verfügbar ist. System Datenquellen werden in der HKEY_LOCAL_MACHINE Struktur gespeichert, und Benutzerdaten Quellen werden in der HKEY_CURRENT_USER Struktur gespeichert. In allen anderen Punkten sind Systemdaten Quellen und Benutzerdaten Quellen identisch.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Unterschlüssel für ODBC-Datenquellen](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [Unterschlüssel für Datenquellenspezifikationen](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [Standardunterschlüssel](../../../odbc/reference/install/default-subkey.md)  
  
-   [ODBC-Unterschlüssel](../../../odbc/reference/install/odbc-subkey.md)
