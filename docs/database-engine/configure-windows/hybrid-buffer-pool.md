---
title: Hybrider Pufferpool | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/06/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ''
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.openlocfilehash: a8098c38b72ba44ab973fe5564b93740252bafc6
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51560307"
---
# <a name="hybrid-buffer-pool"></a>Hybrider Pufferpool
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit SQL Server 2019 CTP 2.1 wird ein neues Feature in der SQL Server-Datenbank-Engine eingeführt, mit dem direkt auf Datenseiten in den auf einem Gerät mit persistentem Speicher (PMEM) gespeicherten Datenbankdateien zugegriffen werden kann. 

In einem herkömmlichen System ohne persistenten Speicher werden Data-Seiten von SQL Server im Pufferpool zwischengespeichert. Mit dem hybriden Pufferpool kopiert SQL Server die Seite nicht in den DRAM-basierten Teil des Pufferpools, stattdessen wird direkt in der Datenbankdatei (die sich auf einem PMEM-Gerät befindet) auf die Seite verwiesen. Der Zugriff auf Datendateien in PMEM für den hybriden Pufferpool erfolgt mit der im Speicher abgebildeten E/A, auch bekannt als „Enlightenment“.

Auf einem PMEM-Gerät kann nur auf nicht modifizierte Seiten direkt verwiesen werden. Wenn eine Seite geändert wird, wird sie in DRAM gespeichert und dann letztendlich zurück auf das PMEM-Gerät geschrieben.

Dieses Feature ist sowohl für Windows als auch für Linux verfügbar.

## <a name="enable-hybrid-buffer-pool"></a>Aktivieren des hybridem Pufferpools

Bei der CTP-Version 2.1 müssen Sie das Startablaufverfolgungsflag 809 aktivieren, um den hybriden Pufferpool zu verwenden.

## <a name="best-practices-for-hybrid-buffer-pool"></a>Bewährte Methoden für den hybriden Pufferpool

* Verwendenden Sie beim Formatieren Ihres PMEM-Geräts unter Windows die größte verfügbare Größe der Zuordnungseinheit für NTFS (2 MB in Windows Server 2019), und stellen Sie sicher, dass das Gerät für DAX (DirectAccess) aktiviert wurde.
  