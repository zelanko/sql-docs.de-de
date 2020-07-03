---
title: Installieren von SMO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.prod_service: database-engine
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d6b0608265b44e7ccebd95491554739524bac390
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894415"
---
# <a name="installing-smo"></a>Installieren von SMO

[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw.md)]

Diese Seite enthält Informationen zum Installieren von SMO für die Verwendung durch Anwendungen und die Systemanforderungen für die Verwendung von SMO.

## <a name="smo-nuget-package"></a>SMO-nuget-Paket

Ab [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO wird als [Microsoft. SqlServer. sqlmanagementobjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) -nuget-Paket verteilt, damit Benutzer Anwendungen mit SMO entwickeln können.

Dies ist ein Ersatz für SharedManagementObjects.msi, der zuvor als Teil des SQL Feature Packs für jede Version von SQL Server freigegeben wurde. Anwendungen, die SMO verwenden, sollten aktualisiert werden, um stattdessen das nuget-Paket zu verwenden, und Sie müssen sicherstellen, dass die Binärdateien mit der Anwendung, die entwickelt wird, installiert werden.

>>[!Important]
>>Wie auf der Seite [Dateien und Versionsnummern](files-and-version-numbers.md) erwähnt, sollten Sie die SMO-Assemblys nicht im GAC installieren. Dies könnte zu Problemen mit anderen Anwendungen führen, die auch diese Versionen von SMO verwenden (z [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . b. Management Studio).

## <a name="installing-the-package"></a>Installieren des Pakets

Anweisungen und Beispiele für die Installation und Verwendung eines nuget-Pakets finden [Sie unter nuget-Schnellstart: Verwenden eines Pakets](https://docs.microsoft.com/nuget/quickstart/use-a-package) . 
  
## <a name="system-requirements"></a>Systemanforderungen
  
 SMO erfordert die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Ausführung von 4,0 oder .net Core 2,0, sodass alle Anwendungen, die es verwenden, sicherstellen müssen, dass auf den Client Computern diese Version oder höher installiert ist. Für einige Native Binärdateien, die mit den netfx SMO-Bibliotheken installiert werden, muss auch die VC 2013-Laufzeit installiert werden. Diese Laufzeit ist nicht im Paket enthalten. Sie können den redist, der für Ihre Zielarchitektur geeignet ist, vonhttps://www.microsoft.com/download/details.aspx?id=40784
  
