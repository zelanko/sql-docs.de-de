---
title: Verwenden von Microsoft Component Services | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], component services
- component services [ODBC]
ms.assetid: 06450562-d8f3-4987-b7bd-4a70223ff937
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fb5763058fa198cbad7464434e31942ef8d6cd7d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307581"
---
# <a name="using-microsoft-component-services"></a>Verwenden von Microsoft Component Services
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Sie können eine Oracle-Datenbank aktivieren, um mit Transaktionskomponentendiensten (oder MTS, wenn Sie Windows NT verwenden) unter Microsoft Windows NT/Windows 2000 und Microsoft Windows 95/98 zu arbeiten. Damit eine Oracle-Datenbank mit Component Services arbeiten kann, die Transaktionen unterstützt, sollten Systemadministratoren eine Ansicht mit dem Namen "V-XATRANS" erstellen. Zum Erstellen dieses Skripts müssen Sie ein von Oracle bereitgestelltes Skript ausführen. Weitere Informationen finden Sie in der Component Services-Hilfe oder in der Oracle-Dokumentation.
