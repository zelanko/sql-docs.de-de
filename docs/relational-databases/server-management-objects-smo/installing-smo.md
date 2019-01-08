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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 97c7159682e421005385fd830ceed4380086089c
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432263"
---
# <a name="installing-smo"></a>Installieren von SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Diese Seite enthält Informationen zum Installieren von SMO für die Verwendung von Anwendungen und Systemanforderungen für die Verwendung von SMO.

## <a name="smo-nuget-package"></a>SMO-NuGet-Paket

Beginnend mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO wird als verteilt die [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) NuGet-Paket, dass Benutzer Anwendungen mit SMO zu entwickeln können.

Dies ist ein Ersatz für SharedManagementObjects.msi, die zuvor als Teil der SQL-Feature Pack für jede Version von SQL Server veröffentlicht wurde. Anwendungen, die SMO verwenden sollten aktualisiert werden, um das NuGet-Paket verwenden und dafür verantwortlich, sicherzustellen, dass die Binärdateien installiert sind, mit der Anwendung, die entwickelt werden.

>>[!Important]
>>Wie erwähnt die [Dateien und Versionsnummern](files-and-version-numbers.md) Seite, Sie sollten nicht die SMO-Assemblys im globalen Assemblycache installieren. Auf diese Weise kann dazu führen, dass Probleme mit anderen Anwendungen, die ebenfalls diese Versionen von SMO verwenden (z. B. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

## <a name="installing-the-package"></a>Installieren des Pakets

Finden Sie unter [NuGet Schnellstart - Verwenden eines Pakets](https://docs.microsoft.com/nuget/quickstart/use-a-package) Anweisungen und Beispiele für die Installation und Verwendung eines NuGet-Pakets. 
  
## <a name="system-requirements"></a>Systemanforderungen
  
 SMO erfordert [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0 ausführen, sodass alle Anwendungen verwenden, sicherstellen müssen, dass Clientcomputer die Version oder höher installiert. Einige nativen-Binärdateien installiert, die mit den NetFx SMO-Bibliotheken erfordern auch die VC++ 2013 Runtime installiert werden; dieser Laufzeit ist nicht im Paket enthalten. Sie können die entsprechenden, auf der Zielarchitektur aus Redist herunterladen. https://www.microsoft.com/download/details.aspx?id=40784
  
